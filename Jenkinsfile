pipeline {
    agent {
        label 'agent' // This matches the label you gave the node in Manage Jenkins
    }

    stages {
        stage('Verify Node') {
            steps {
                echo "Checking where this job is running..."
                // This command prints the hostname and kernel info of the machine
                sh 'uname -a'
                sh 'hostname'
            }
        }
        
        stage('Build') {
            steps {
                sh 'echo "Building on the Agent node..."'
                // Add your build logic here if needed
            }
        }
    }
    
    post {
        always {
            echo "Execution finished."
        }
    }
}