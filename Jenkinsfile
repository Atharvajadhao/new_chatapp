pipeline{
    agent { label 'prod-node-1' }
    stages{
        stage ("Git Pull") {
            steps{
                git 'https://github.com/Atharvajadhao/new_chatapp.git'
            }
        }
        stage ('SonarQube Testing') {
            steps {
                script {
                    def scannerHome = tool 'SonarScanner';
                    withSonarQubeEnv() {
                      sh "${scannerHome}/bin/sonar-scanner"
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
