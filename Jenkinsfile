pipeline {
    agent any
    stages {
        stage('Linting') {
            steps {
                echo 'cfn-lint -t templates/aws-vpc.template.yaml'
            }
        }
        stage('Unittesting') {
            steps {
                echo 'taskcat test run'
            }
        }
    }
    post { 
        always { 
            echo 'I will always say Hello again!'
        }
    }
}
