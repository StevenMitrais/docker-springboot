pipeline {
    agent any
    tools {
      // Install the Maven version configured as "M3" and add it to the path.
      maven "M3"
    }
    stages{
        stage('Clone repository') {
            steps{
            /* Cloning the Repository to our Workspace */
                git 'https://github.com/StevenMitrais/docker-springboot'
            }
        }

        stage('Build image') {
           
            steps {
                sh 'mvn --version'
                sh 'mvn clean install'
                sh 'docker build -t steven1994/springboot .'
            }
        }

        stage('Run image') {
            steps{
                sh 'docker run -d -p 8081:8080 steven1994/springboot'
                echo "Finish"
            }
       }
    }
        // stage('Push image') {
            
        //     docker.withRegistry('https://registry.hub.docker.com', 'docker-springboot') {
        //         app.push("${env.BUILD_NUMBER}")
        //         app.push("latest")
        //         } 
        //             echo "Trying to Push Docker Build to DockerHub"
        // }
}