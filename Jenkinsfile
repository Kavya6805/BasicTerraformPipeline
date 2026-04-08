pipeline {
    agent any

    stages{
        stage('Verify Terraform') {
            steps {
                sh 'terraform --version'
            }
        }
        stage('Terraform init') {
            steps {
                withCredentials([[ $class: 'AmazonWebServicesCredentialsBinding', 
                                   credentialsId: 'aws-global-creds']]) {
                    sh 'terraform init' 
                }
            }
        }
        stage('Terraform plan') {
            steps {
                sh 'terraform plan'
            }
        }
        stage('Terraform apply') {
            steps {
                sh 'terraform apply -auto-approve'
            }
        }
        stage('Complete pipeline') {
            steps {
                sh 'echo "Completed"'
            }
        }
    }
}