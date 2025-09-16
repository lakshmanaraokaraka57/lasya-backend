pipeline{
    agent any
    environment{
        PROJECT='Lasya-InfoTech'
        component='backend'
       def appVersion=''
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
                    npm install
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
