pipeline {
    agent any
    // environment {
    //     IMAGE_NAME = 'sanjeevkt720/jenkins-flask-app'
    //     IMAGE_TAG = "${IMAGE_NAME}:${env.BUILD_NUMBER}"
    //     KUBECONFIG = credentials('kubeconfig-credentials-id')
     options {
        // Timeout counter starts AFTER agent is allocated
        timeout(time: 20, unit: 'SECONDS')
    }
    // }
    stages {

        // stage('Checkout') {
        //     steps {
        //         git url: 'https://github.com/kodekloudhub/jenkins-project.git', branch: 'main'
        //         sh "ls -ltr"
        //     }
        // }

          stage('sleep') {
            steps {
                sh "sleep 30"
            }
        }


        stage('Setup') {
            // environment{
            //     HOST_NAME="mim"
            //     PORT=5555
            // }
            steps {
                withCredentials([usernamePassword(credentialsId: "e0944a0d-09af-4b2f-812e-06b7f377bdac",usernameVariable: "myUser",passwordVariable: 
                "mypass")])
                // sh "pip install -r requirements.txt"
                //install pip last build pip was not found.

                {
                    sh '''
                        echo "user is ${myUser}"
                        echo "pass is ${mypass}"
                    '''
                }
                sh "python3 -m venv venv"      
                sh "bash -c 'source venv/bin/activate && pip install -r requirements.txt'"
                // sh "echo 'pass is ${mypass}'"
        }}
        stage('Test') {
            steps {
               sh '''
                    . venv/bin/activate
                    pytest
                '''
                sh "whoami"
                // echo "PORT is ${env.GIT_COMMIT}"
            }
            
        }}} //need to remove after this lab
//         stage('Login to docker hub') {
//             steps {
//                 withCredentials([string(credentialsId: 'dockerhubpwd', variable: 'dockerhubpwd')]) {
//                 sh 'echo ${dockerhubpwd} | docker login -u sanjeevkt720 --password-stdin'}
//                 echo 'Login successfully'
//             }
//         }
//         stage('Build Docker Image')
//         {
//             steps
//             {
//                 sh 'docker build -t ${IMAGE_TAG} .'
//                 echo "Docker image build successfully"
//                 sh "docker images"
//             }
//         }
//         stage('Push Docker Image')
//         {
//             steps
//             {
//                 sh 'docker push ${IMAGE_TAG}'
//                 echo "Docker image push successfully"
//             }
//         }
//         stage('Deploy to EKS Cluster') {
//             steps {
//                 sh "kubectl apply -f deployment.yaml"
//                 echo "Deployed to EKS Cluster"
//             }
//         }
//     }
// }
