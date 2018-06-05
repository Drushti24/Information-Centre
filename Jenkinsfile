import groovy.util.ConfigSlurper
node('master'){
 stage('build'){
def job= sh ('curl --insecure --user jenkins:jenkins -X POST http://52.224.106.41:8080/job/Build_Job/build?token=trigger123')
sleep 10
while (output.result == "SUCCESS"){
def lastbuild = sh ('curl --insecure -X POST http://52.224.106.41:8080/job/Build_Job/lastBuild/api/json')
def output  = new ConfigSlurper().parse(lastbuild)
 return output.result
 }
 }
}
