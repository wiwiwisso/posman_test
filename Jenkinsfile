pipeline{
    agent {docker {
        image 'postman/newman'
    } }
    stages{
        stage('newman version'){
            steps{
                sh 'newman -v'
            }
        }

        stage('run postman collecttion with postman'){
            steps{
                sh 'newman run collection.postman_collection.json -e env1.json -r cli,json --reporter-junit-export results.xml'
                    
            }
        }
    }
    post {
        always {
            junit 'results.xml'
        }
    }
}