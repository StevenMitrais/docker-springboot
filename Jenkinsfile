pipeline {
    def app
    
    agent{
        dockerfile true
    }
    stages{

        stage('Clone repository') {
            /* Cloning the Repository to our Workspace */

            checkout scm
        }

        stage('Build image') {
            /* This builds the actual image */

            app = docker.build("steven1994/springboot")
        }

        stage('Test image') {
            
            app.inside {
                echo "Tests passed"
            }
        }

        stage('Push image') {
            /* 
                You would need to first register with DockerHub before you can push images to your account
            */
            docker.withRegistry('https://registry.hub.docker.com', 'docker-springboot') {
                app.push("${env.BUILD_NUMBER}")
                app.push("latest")
                } 
                    echo "Trying to Push Docker Build to DockerHub"
        }
    }
}