pipeline{
    agent { label 'dev-node' }
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
        stage('Deploy') {
            steps {
               sh 'bash /home/ubuntu/new_chatapp/scripts/AppStart.sh'
            }
        }
    }
}
