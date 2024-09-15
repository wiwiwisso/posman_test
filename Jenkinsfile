pipeline{
    agent any
    stages{
        stage('newman version'){
            steps{
                sh 'newman -v'
            }
        }

        stage('newman version'){
            steps{
                sh 'newman -run collection.postman_collection.json -e env1.json'
            }
        }
    }
}