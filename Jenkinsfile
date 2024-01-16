pipeline{
    agent { label 'prod-node-1' }
    environment {
        SONARQUBE_HOME = tool 'sonar-qube'
        SONARQUBE_TOKEN = credentials('squ_136e23008e031f0edd99fe8fcc25f4e41546cfec')
        SONARQUBE_PROJECT_KEY = 'new_chatapp'
    }
    stages{
        stage("Git Pull"){
            steps{
                git 'https://github.com/Atharvajadhao/new_chatapp.git'
            }
        }
        stage('Build') {
            steps {
                sh "sudo cp -r . /home/ubuntu/new_chatapp"
            }
        }
        stage('SonarQube Testing') {
            steps {
                def scannerHome = tool 'sonar-qube'
                withSonarQubeEnv('sonar-server') {
                    // Run the SonarQube Scanner with project key and authentication token
                    sh "${scannerHome}/bin/sonar-scanner -Dsonar.login=${SONARQUBE_TOKEN} -Dsonar.projectKey=${SONARQUBE_PROJECT_KEY}"
                }
            }
        }
        stage('Deploy') {
            steps {
               sh 'bash /home/ubuntu/new_chatapp/scripts/AppStart.sh'
            }
        }
    }
}
