def awsCredentials = [[$class: 'AmazonWebServicesCredentialsBinding', credentialsId: 'aws-personal']]

pipeline {
    agent any
    stages {
        stage('Linting') {
            steps {
                sh 'cfn-lint -t templates/aws-vpc.template.yaml'
            }
        }
        stage('Validate') {
            steps {
                sh 'aws cloudformation validate-template --template-body file://templates/aws-vpc.template.yaml'
            }
        }        
        stage('Unittesting') {
            steps {
                withCredentials(awsCredentials) {
                    sh 'taskcat test run'
                }    
            }
        }
    }
    post { 
        always { 
            echo 'I will always say Hello again!'
            publishHTML target: [
              allowMissing: false,
              alwaysLinkToLastBuild: false,
              keepAll: true,
              reportDir: 'taskcat_outputs',
              reportFiles: 'index.html',
              reportName: 'Unittest Report'
            ]
        }
    }
}
