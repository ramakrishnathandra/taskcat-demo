def awsCredentials = [[$class: 'AmazonWebServicesCredentialsBinding', credentialsId: 'aws-personal']]

pipeline {
    agent any
    stages {
        stage('Linting') {
            steps {
                sh 'cfn-lint -t templates/aws-vpc.template.yaml'
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
        }
    }
}
