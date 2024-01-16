pipeline{
    agent { label 'prod-node-1' }
    environment {
        SONARQUBE_HOME = tool 'sonar-qube'
        SONARQUBE_TOKEN = credentials('squ_c604c48fd338cab30db5a2d3c5b304444080e246')
        SONARQUBE_PROJECT_KEY = 'new_chatapp'
    }
    stages{
        /*stage ("Git Pull") {
            steps{
                git 'https://github.com/Atharvajadhao/new_chatapp.git'
            }
        }*/
        stage ('SonarQube Testing') {
            steps {
                script {
                    def scannerHome = tool 'sonar-qube'
                    withSonarQubeEnv('sonar-server') {
                        // Run the SonarQube Scanner with project key and authentication token
                        sh "${scannerHome}/bin/sonar-scanner -Dsonar.login=${SONARQUBE_TOKEN} -Dsonar.projectKey=${SONARQUBE_PROJECT_KEY}"
                    }
                }
            }
        }
        stage ('Build') {
            steps {
                sh "sudo cp -r . /home/ubuntu/new_chatapp"
            }
        }
        stage ('Deploy') {
            steps {
               sh 'bash /home/ubuntu/new_chatapp/scripts/AppStart.sh'
            }
        }
    }
}
