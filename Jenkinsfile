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
		sh 'aws s3 cp ${WORKSPACE}/dist/rectangle-$BUILD_NUMBER.jar s3://jenkins-s3bucket-t7221z7tjgln'
	}
    stage ('Report'){  
		withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: '84f648e6-a43e-473d-acef-bf06b07d25bf', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
   		sh 'aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins' 
           }		
        }
    }
	
