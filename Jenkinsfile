pipeline{
    agent any
    
    stages{
        stage('docker build'){
            steps{
                script{
                    def status = bat(
                        script: 'docker build -t python-app .',
                        returnStatus: true
                    )
                    if(status != 0){
                        error 'Docker build failed'
                    }
                }
            }
        }
        stage('Run container'){
            steps{
                bat'docker run python-app'
            }
        }
        

    }
    post{
            always{
                bat'docker system prune -f'
            }
        }
}