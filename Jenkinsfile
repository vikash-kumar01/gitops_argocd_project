pipeline{

    agent any 

    environment{

        DOCKERHUB_USERNAME = "vikashashoke"
        APP_NAME = "gitops-argo-app"
        IMAGE_TAG = "${BUILD_NUMBER}"
        IMAGE_NAME = "${DOCKERHUB_USERNAME}" + "/" + "${APP_NAME}"
        REGISTRY_CREDS = 'dockerhub'
    }

    stages{

        stage('Clenup workspace'){

           steps{
               script{

                  cleanWs()
               }
           }
        }
        stage('Checkout SCM'){

            steps{
                script{
                    git credentialsId: 'github',
                    url: 'https://github.com/vikash-kumar01/gitops_argocd_project.git',
                    branch: 'main'
                }
            }
        }
        stage('Build Docker Image'){
            steps{
                script{

                    docker_image = docker.build "${IMAGE_NAME}"
                }
            }
        }
    }
}

//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