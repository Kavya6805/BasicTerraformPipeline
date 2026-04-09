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
                withCredentials([[ $class: 'AmazonWebServicesCredentialsBinding', 
                                   credentialsId: 'aws-global-creds']]) {
                    sh 'terraform plan' 
                }
                input message: 'Do you want to proceed to the next stage?'
            }
        }
        stage('Terraform apply') {
            steps {
                withCredentials([[ $class: 'AmazonWebServicesCredentialsBinding', 
                                   credentialsId: 'aws-global-creds']]) {
                    sh 'terraform apply -auto-approve'
                }
            }
        }
        stage('Complete pipeline') {
            steps {
                sh 'echo "Completed"'
            }
        }
    }
    post{
        always{
            deleteDir()
        }
    }
}