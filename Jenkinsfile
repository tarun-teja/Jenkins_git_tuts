pipeline {
    agent { docker { 
        image 'alpine' 
        args "-v /tmp/testground:/root/testground"
    } }
    stages {
        stage('build') {
            steps {
                sh 'date'
                sh 'cat /etc/*release*'
            }
        }
        stage('Testing 1'){
            steps {
                sh 'pwd'
                sh 'ls'
                #sh 'cat /root/testground/nin'
            }
        }
    }
}
