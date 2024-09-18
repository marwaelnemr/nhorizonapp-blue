pipeline {
    agent any  // Use any available agent
    
    stages {
        
        
        stage('Pull Docker Image') {
            steps {
                // Pull the Docker image
                sh 'docker pull webdevops/php-apache:8.2'
            }
        }
        
        stage('Run Docker Container') {
            steps {
                sh 'docker run -it --rm -d -p 80:80 -v webapproot:/app/ --name apa webdevops/php-apache:8.2'
            }
        }
        
        stage('Run Selenium Test') {
            steps {
                // Run your Selenium test script
                sh 'python3 /testmodules/test_webapp.py'  // Update with your test script name
            }
        }

    }
    post   {
        always {
            // Clean up (optional)
            sh 'docker rm apa -f'
        }
    }
}
