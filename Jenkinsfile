properties([pipelineTriggers([githubPush()])])

node('linux') {   
	stage('Test') {    
		git 'https://github.com/akshita-gulati/java-project.git'
		sh 'ant -buildfile test.xml'   
	}   
	stage('Build') {    
                sh 'ant'
                sh 'ant -f build.xml -v'
        }   
	stage('Deploy') {    
		pip install [--user] awscli
    		aws s3 cp rectangle-4.jar jenkins-s3bucket-1bcf79bs7meg2.s3.amazonaws.com
	}
}
