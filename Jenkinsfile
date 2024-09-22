pipeline {
    agent any  // Use any available agent

    environment {
        TF_VAR_example = 'value' // Example of passing variables
    }

    stages {
        stage('Checkout Code') {
            steps {
                // Checkout your code from version control
                git 'https://github.com/kashan-1/tf_example.git'  // Replace with your repo URL
            }
        }
        
        stage('Terraform Init') {
            steps {
                script {
                    // Initialize Terraform
                    sh 'terraform init'
                }
            }
        }

        stage('Terraform Plan') {
            steps {
                script {
                    // Create an execution plan
                    sh 'terraform plan -out=tfplan'
                }
            }
        }

        stage('Terraform Apply') {
            steps {
                script {
                    // Apply the changes
                    // Using `-auto-approve` to skip confirmation
                    sh 'terraform apply -auto-approve tfplan'
                }
            }
        }
    }

    post {
        always {
            // Cleanup or notify steps can go here
            echo 'Pipeline completed.'
        }
        success {
            echo 'Terraform applied successfully!'
        }
        failure {
            echo 'Terraform failed.'
        }
    }
}
