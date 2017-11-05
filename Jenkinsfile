pipeline {
    agent any 

    stages {
        stage('Build Orion-DB Cassandra Docker Image') { 
            steps { 
                sh 'sudo docker run -d -it --name orion-db -p 0.0.0.0:9042:9042 -p 7000-7001:7000-7001 -p 7199:7199 -p 9160:9160 cassandra:latest bash
' 
            }
        }
    }
}
