pipeline{

    agent { docker 'node:22.8'}
    stages{
        stage('install newman'){
            steps{
                sh 'npm i newman'
            }
        }

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
                sh 'newman run collection.postman_collection.json -e env1.json -r --reporters cli,junit,html  --reporter-html-export newman/results.html'
                    
            }
        }
    }
    post {
        always {
            junit 'newman/results.html'
        }
    }
}