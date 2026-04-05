pipeline {
    agent any

    environment {
        PATH = "/opt/maven/bin:$PATH"
    }

    stages {

        stage("build") {
            steps {
                echo "----------- build started ----------"
                sh 'mvn clean install -DskipTests'
                echo "----------- build completed ----------"
            }
        }

        stage('SonarQube analysis') {
            environment {
                scannerHome = tool 'sonarqubescanner'
            }

            steps {
                withSonarQubeEnv('sonarqubeserver') {
                    sh 'mvn sonar:sonar'
                }
            }
        }

        

    }
}
