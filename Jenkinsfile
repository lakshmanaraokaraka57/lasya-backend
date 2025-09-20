pipeline{
    agent { label 'AGENT-1' }
    environment{
        PROJECT='expense'
        component='backend'
        appVersion=''
    }
    stages{
        stage('Read Version'){
            steps{
                script{
                    
                    def packageJson = readJSON file: 'package.json'
                    appVersion=packageJson.version
                    echo "appversion is:$appVersion"
                }
            }
        }
        stage('Install Dependencies'){
            steps{
                script{
                    sh """
                     npm install
                    """
                }
            }
        }
        stage('Docker Build'){
            steps{
                script{
                    sh """
                      docker build -t backend:v1.0.0 .
                   
                    """
                }
            }
        }
    }
    post{
        success{
            script{
                def timestamp= new Date()
                echo "Deployment completed at ${timestamp}"
            }
            deleteDir()
        }
        failure{
            script{
                def timestamp = new Date()
                echo  "Deployment is not completed at ${timestamp}"
            }
        }
    }
}
