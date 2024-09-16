pipeline{

    agent any
    stages{
        stage('node version'){
            steps{
                sh 'npm -v'
            }
        }

        stage('newman version'){
            steps{
                sh 'newman -v'
            }
        }

        stage('run postman collecttion with postman'){
            steps{
                sh 'newman run collection.postman_collection.json -e env1.json'
                    
            }
        }


        stage('run postman collecttion with postman'){
            steps{
               eccho '${params.env}'
                    
            }
        }

        
    }

    
}