def buildNumber =''

node('master'){
    stage('Build and Artifactory Upload'){

sh ("curl --insecure --user jenkins:jenkins -X POST 'http://52.224.106.41:8080/job/Build_Job/build?token=trigger123' ")
sleep 90
sh("curl -X GET --user  jenkins:jenkins 'http://52.224.106.41:8080/job/Build_Job/lastBuild/buildNumber' -k  > outFile ")
buildNumber = readFile 'outFile'
echo "The build number is ${buildNumber}"
echo " BUILD CONSOLE OUTPUT OF BUILD NUMBER ${buildNumber}"

sh("curl -X GET --user  jenkins:jenkins 'http://52.224.106.41:8080/job/Build_Job/${buildNumber}/consoleText' ")
sleep 150

    } 
 stage('Deployment to Tomcat'){
sh("curl -X GET --user  jenkins:jenkins 'http://52.224.106.41:8080/job/Deploy_Job/lastBuild/consoleText' ")
}
}
