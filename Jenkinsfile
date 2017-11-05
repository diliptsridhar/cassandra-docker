pipeline {
    agent any 
    
    parameters {
         string(name: 'cassandra_dev',  defaultValue: '35.166.210.154', description: 'Cassandra Dev Server')
         string(name: 'cassandra_prod', defaultValue: '34.209.233.6', description: 'Cassandra Production Server')
    }


    stages {
        stage('Cleaning Orion-DB Cassandra Docker Image') { 
            steps { 
           
                sh '''
                    echo 'Stopping  orion-db ...'
                    sudo -n docker ps -a |  grep "orion-db" | awk '{print $1}' | xargs docker stop bash
                    echo 'Removing  orion-db ...'
                    sudo -n docker ps -a |  grep "orion-db" | awk '{print $1}' | xargs docker rm   bash
                   ''' 
            }
            post {
                success {
                    echo 'Post Success...'
                    echo "${params.cassandra_dev}"
                    
                }
            }
        }        
        stage('Build Orion-DB Cassandra Docker Image') { 
            steps { 
           
                sh '''
                    sudo  -n docker run -d -it --name orion-cassandra-db -p 0.0.0.0:9042:9042 -p 7000-7001:7000-7001 -p 7199:7199 -p 9160:9160 cassandra:latest bash
                   ''' 
            }
            post {
                success {
                    echo 'Post Success...'
                    echo "${params.cassandra_dev}"
                    
                }
            }
        }
    }
}
