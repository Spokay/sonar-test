pipeline {
    agent { label 'ssh-agent' }

    stages {
        stage('SCM') {
           steps {
                git branch: 'master', url: 'https://github.com/Spokay/sonar-test.git'
           }
        }
        stage('SonarQube Analysis') {
            steps {
                def scannerHome = tool 'SonarScanner';
                withSonarQubeEnv('SonarScanner') {
                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }
    }
}

