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
		sh 'aws s3 cp rectangle-$BUILD_NUMBER.jar s3://jenkins-s3bucket-10yn3xnstrpvr.s3.amazonaws.com'
	}
}
