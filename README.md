# jenkinsgolang


Make sure the follwing steps are run under user root:
1. create a folder to be used as the workspace
2. cd to it
3. git clone https://github.com/shaipa999/jenkinsgolang.git
4. do chmod -R 777 ./jenkins-certs/  && chmod -R 777 ./jenkins/
5. Make sure minikube is started with docker driver - minikube start --driver=none
6. Execute command kubectl config view > kubcfg to generate a kube cfg file
7. Run the command kubectl config view and copy the server url from the Server tag in the output.
8. Go to the folder ./jenkinssr/jenkins/workspace/deployToKurb@script/ and in Jenkinsfile change the <mini_kube_url> with the minikube url you fetch in step 7.
9. Run the command docker-compose up -d to start the Jenkins
10. Wait 2 minutes and browse to the following url: http://localhost:8080/credentials/store/system/domain/_/credential/2/update - Auth with User:admin , Pass: admin
11. Tick the Replace box and upload the kubcfg file from step 6 and save
12. Browse to the job in the URL: http://localhost:8080/job/deployToKurb/ and press Build Now to update the process.



To make changes in the App Code, Edit the code in /jenkinssr/jenkins/workspace/deployToKurb/files main.go