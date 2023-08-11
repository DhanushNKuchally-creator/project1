pipeline{
    
    agent any
    
    environment{
        dockerImage= ""
        registry= "dhanushnkuchally/image1"
        registryCredential= "6d75c84c-a226-41be-ae01-4078953f6ff6"
    }
    
    stages{
        stage('Checkout'){
            steps{
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/DhanushNKuchally-creator/project1.git']])
            }
        }
        stage('Build Docker Image'){
            steps{
                script{
                    dockerImage= docker.build registry
                }
            }
        }
        stage('Upload Image') {
            steps{    
                script {
                    docker.withRegistry( '', registryCredential ){ 
                    dockerImage.push()
                    }
            }
        }
      }
        stage('Run Docker Container') {
            steps {
                script {
                    def dockerImage = docker.image(registry)
                    dockerImage.run('-p 8081:80 -d')
                        }
                    }
                }

    }
              
        
    }
