pipeline {
    agent any

    parameters {
        choice(name: 'ENVIRONMENT', choices: ['dev', 'qa', 'uat'], description: 'Choose environment')
    }

    environment {
        SSH_KEY_CRED = 'ssh-deploy-key'
        IMAGE = "ankushmohite/node-todo-cicd:R1.1-${BUILD_NUMBER}"
    }

    stages {

        stage('Code') {
            steps {
                git url: 'https://github.com/ankushmohite/node-todo-cicd.git', branch: 'master'
            }
        }

        stage('Build & Push Docker Image') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerHub',
                                                  usernameVariable: 'DOCKER_USER',
                                                  passwordVariable: 'DOCKER_PASS')]) {

                    sh '''
                        docker build -t $IMAGE .
                        echo "$DOCKER_PASS" | docker login -u "$DOCKER_USER" --password-stdin
                        docker push $IMAGE
                        docker logout
                    '''
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    def IP_CRED_ID = ""

                    if (params.ENVIRONMENT == "dev")  IP_CRED_ID = "dev_ip"
                    if (params.ENVIRONMENT == "qa")   IP_CRED_ID = "qa_ip"
                    if (params.ENVIRONMENT == "uat")  IP_CRED_ID = "uat_ip"

                    withCredentials([
                        string(credentialsId: IP_CRED_ID, variable: 'TARGET_IP'),
                        sshUserPrivateKey(credentialsId: env.SSH_KEY_CRED, keyFileVariable: 'SSH_KEY')
                    ]) {

                        sh """
                            ssh -i $SSH_KEY -o StrictHostKeyChecking=no ubuntu@${TARGET_IP} '
                                docker pull ${IMAGE}
                                docker rm -f node-app || true
                                docker run -d --name node-app -p 8000:8000 ${IMAGE}
                            '
                        """
                    }
                }
            }
        }
    }
}
