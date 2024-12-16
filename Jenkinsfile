pipeline{
    agent any
    environment {
        DOCKERHUB_CREDENTIALS = credentials('docker_hub_credentials')
    } 
    stages
    {
        stage("gitclone"){
            steps{
                echo "gonig to github repo  "
                git 'https://github.com/amirelkhateeb/firstautofile'

            }
            post{
                always{
                    echo "========always========"
                }
                success{
                    echo "========A executed successfully========"
                }
                failure{
                    echo "========A execution failed========"
                }
            }
        }
        stage('build image'){
            steps{
            
             sh 'docker build -t amirelkhateeb/hrapp:latest . '  

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
  