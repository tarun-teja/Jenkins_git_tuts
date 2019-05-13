pipeline {
    agent { docker { 
        image 'alpine' 
        args "-v /tmp/testground:/root/testground"
    } }
    stages {
        stage('build') {
            steps {
                //forgot to add stuff
                sh 'date'
                sh 'cat /etc/*release*'
            }
        }
        stage('Testing 1'){
            steps {
                //sh 'cat /root/testground/nin'
                  sh 'echo "excludin this coz we are not mounting stuff"'
            }
        }
    }
}
