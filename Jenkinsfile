pipeline{
    agent any   
    environment {
        DOCKERHUB_CREDENTIALS = credentials('docker_hub_credentials')
    } 
    stages
    {
        stage('gitclone'){
            steps{
                echo "gonig to github repo  "
                git 'https://github.com/amirelkhateeb/firstautofile'

        
        }
        }
        stage('build image'){
            steps{
            
             sh 'docker build -t hrapp:latest .'  

             }
        }
        stage('LOGIN'){
            steps{
                sh 'echo "$DOCKERHUB_CREDENTIALS_PSW" | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin '
            }
        }
        stage('push'){
            steps{
                sh 'docker push amirelkhateeb/hrapp:latest '
            }
        }

    }   

}
  