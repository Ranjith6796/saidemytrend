pipeline {
    agent any
    environment {
        PATH = "/opt/maven/bin:$PATH"
    }

    stages {
        stage('GitHub Clone') {
            steps {
                git url: 'https://github.com/Ranjith6796/saidemytrend.git', branch: 'main'
            }
        }
        
        stage("build") {
            steps {
                sh 'mvn clean deploy'
            }
        }

        stage('SonarQube analysis') {
            environment {
                scannerHome = tool 'ranjith-abs-server'
            }
            steps {
                withSonarQubeEnv('sonar-server') {
                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }
    }
} 
