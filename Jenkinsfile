properties([pipelineTriggers([githubPush()])])

node('linux') {   
	stage('Unit Tests') {    
		git 'https://github.com/akshita-gulati/java-project.git'
		sh 'ant -f test.xml -v'   
		junit 'reports/result.xml'   
	}
	stage('Build') {                                   
		sh 'ant -f build.xml -v'        
	}
	stage('Deploy') {
		sh 'aws s3 cp ${WORKSPACE}/dist/rectangle-$BUILD_NUMBER.jar s3://jenkins-s3bucket-10yn3xnstrpvr'
	}
	stage ('Report'){  
		withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: '084c8e83-7841-4f25-864c-b4827e6faaa5', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
   		sh 'aws cloudformation describe-stack-resources --stack-name jenkins --region us-east-1' 
           }
		
	}

}
