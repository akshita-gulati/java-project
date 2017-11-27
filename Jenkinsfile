properties([pipelineTriggers([githubPush()])])

node('linux') {   
	stage('Unit Tests') {    
		git 'https://github.com/akshita-gulati/java-project.git'
		sh 'ant -buildfile test.xml'   
	} 
}
