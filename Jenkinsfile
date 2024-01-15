pipeline {
    agent none

    stages {
        stage('Build') {
            matrix {
                axes {
                    axis {
                        name 'BRANCH'
                        values 'dev', 'master'
                    }
                }
                agent {
                    label "${BRANCH}-node"
                }
                stages {
                    stage('Git Pull') {
                        steps {
                            script {
                                git 'https://github.com/Atharvajadhao/new_chatapp.git'
                            }
                        }
                    }
                    stage('Build') {
                        steps {
                            script {
                                echo "Building ${BRANCH} branch on ${BRANCH}-node"
                                sh "sudo cp -r . /home/ubuntu/new_chatapp"
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
        }
    }
}
