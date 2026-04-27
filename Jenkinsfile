pipeline {
    agent { label 'ssh-agent' }

    tools {
        nodejs 'node-25'
    }

    stages {
        stage('SCM') {
           steps {
                git branch: 'master', url: 'https://github.com/Spokay/sonar-test.git'
           }
        }
        stage('SonarQube Analysis') {
            steps {
                script {
                    def scannerHome = tool 'SonarScanner'
                    withSonarQubeEnv('sonar-spokay') {
                        sh "${scannerHome}/bin/sonar-scanner"
                    }
                }
            }
        }
    }
}

