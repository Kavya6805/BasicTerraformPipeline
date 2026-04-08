pipeline {
    agent any

    stages{
        stage("Cleaning"){
            steps{
                deleteDir()
            }
        }
        stage('Verify Terraform') {
            steps {
                sh 'terraform --version'
            }
        }
        stage('Terraform init') {
            steps {
                sh 'terraform init'
            }
        }
        stage('Terraform plan') {
            steps {
                sh 'terraform plan'
            }
        }
        stage('Terraform apply') {
            steps {
                sh 'terraform apply'
            }
        }
        stage('Complete pipelie') {
            steps {
                sh 'echo "Completed"'
            }
        }
    }
}