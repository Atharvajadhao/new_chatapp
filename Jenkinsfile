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
               sshagent(['jenkins-deploy']) {
                   sh "scp -r -o StrictHostKeyChecking=no fundoo ubuntu@10.0.1.127:/home/ubuntu/new_chatapp "
               }
            }
        }
        stage('deploy') {
            steps {
               sh 'ssh -i /var/lib/jenkins/jenkins.pem ubuntu@10.0.1.127 "bash /home/ubuntu/new_chatapp/scripts/Start_Server.sh"'
            }
        }
    }
}
