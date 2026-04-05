pipeline {
    agent any

    environment {
        PATH = "/opt/maven/bin:$PATH"
    }

    stages {

        stage("build") {
            steps {
                echo "----------- build started ----------"
                sh 'mvn clean install'
                echo "----------- build completed ----------"
            }
        }

        stage('SonarQube analysis') {
            steps {
                echo "----------- sonar started ----------"
                withSonarQubeEnv('sonarqube-server') {
                    sh 'mvn sonar:sonar'
                }
                echo "----------- sonar completed ----------"
            }
        }

    }
}
