pipeline {
    agent any
    stages {
        stage('Linting') {
            steps {
                echo 'cfn-lint -t templates/aws-vpc.template.yaml'
            }
        }

    }
    post { 
        always { 
            echo 'I will always say Hello again!'
        }
    }
}
