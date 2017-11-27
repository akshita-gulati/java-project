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
}
