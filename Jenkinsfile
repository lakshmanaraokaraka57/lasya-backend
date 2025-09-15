pipeline{
    agent any
    environment{
        PROJECT='Lasya-InfoTech'
        component='backend'
        appVersion=''
    }
    stages{
        stage('Read Version'){
            steps{
                script{
                    def appVersion = readJSON file: 'package.json'
                    appVersion=package.json.Version
                    echo "appversion is:$appVersion"
                }
            }
        }
        
        
    }
    post{
        success{
            script{
                def timestamp= new Date()
                echo 'Deployment completed at ${timestamp}'
            }
            deleteDir()
        }
        failure{
            script{
                def timestamp = new Date()
                echo  'Deployment is not completed at ${timestamp}'
            }
        }
    }
}
