pipeline {
    agent {label 'Prod-2'}
    stages {
        stage('Checkout') {
            steps {
                // Checkout your source code from version control
                 git checkout <repository_url>
            }
        }
        
        stage('Build') {
            steps {
                // Compile the Java source code
                sh 'javac HelloWorld.java'
            }
        }
        
        stage('Run') {
            steps {
                // Run the compiled Java program
                sh 'java HelloWorld'
            }
        }
        
        stage('SonarQube Analysis') {
            steps {
                script {
                    def scannerHome = tool name: 'SonarQube Scanner', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
                    withEnv(["PATH+SONARQUBE_SCANNER=${scannerHome}/bin"]) {
                        sh 'sonar-scanner'
                    }
                }
            }
        }
    }
}
