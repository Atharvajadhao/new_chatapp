pipeline{
    agent any
    stages{
        stage("git"){
            steps{
                git 'https://github.com/Priya412-coder/new_chatapp-1.git'
            }
        }
        stage('build') {
            steps {
                sh "sudo cp -r . /home/ubuntu/new_chatapp"
            }
        }
        stage('deploy') {
            steps {
               sh 'bash /home/ubuntu/new_chatapp/scripts/AppStart.sh"'
            }
        }
    }
}
