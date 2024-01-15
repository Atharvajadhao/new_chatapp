pipeline{
    agent any
    stages{
        stage("Git Pull"){
            steps{
                git 'https://github.com/Priya412-coder/new_chatapp-1.git'
            }
        }
        stage('Build') {
            steps {
                sh "sudo cp -r . /home/ubuntu/new_chatapp"
            }
        }
        stage('Deploy') {
            steps {
               sh 'bash /home/ubuntu/new_chatapp/scripts/AppStart.sh"'
            }
        }
    }
}
