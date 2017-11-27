properties([pipelineTriggers([githubPush()])])

node('linux') {   
stage('Unit Tests') {  
    sh 'ant'
    git 'https://github.com/akshita-gulati/java-project.git'
    sh 'ant -f test.xml -v'   
    junit 'reports/result.xml'
}   
