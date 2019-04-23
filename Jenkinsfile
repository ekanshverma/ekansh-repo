pipeline {
	agent any
	stages {
		stage('s3download') {
		steps {
		withAWS(region:'ap-south-1',credentials:'004af566-6b2e-485d-bb67-1ed385067048'){ 
		s3Download(file:'myfile.txt', bucket:'ekansh-bucket',path:'myfile.txt', force:true)
}} }
                stage('editing'){
                steps{
                        sh label: '', script: '''#!/bin/bash
pwd
ls -al
cat myfile.txt
echo "appended one" >> /var/lib/jenkins/workspace/pipeline/myfile.txt
cat  /var/lib/jenkins/workspace/pipeline/myfile.txt'''
        }

}
stage('uploading'){
steps{
withAWS(region:'ap-south-1',credentials:'004af566-6b2e-485d-bb67-1ed385067048'){
s3Upload(file:'myfile.txt', bucket:'ekansh-bucket', path:'myfile.txt')
}
}
}
} }

