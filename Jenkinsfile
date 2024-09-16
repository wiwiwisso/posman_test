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
                sh 'newman run collection.postman_collection.json -e env1.json -r --reporters cli,junit,html  --reporter-html-export results.html'
                    
            }
        }
    
        stage('Run Newman tests') {
                    steps {
                        sh '''
                        mkdir -p reports
                        newman run newman_collections.json \
                        --reporters cli,json,junit,htmlextra \
                        --reporter-htmlextra-export ./reports/myreport.html \
                        --reporter-htmlextra-theme default

                        // Vérifier le contenu du répertoire reports
                        ls -la ./reports

                        // Afficher le contenu du rapport HTML
                        cat ./reports/myreport.html
                        '''
                    }
        }
    }

    post {
        always {
            // Archiver les rapports générés
            archiveArtifacts artifacts: 'reports/*.html', allowEmptyArchive: true

            // Publier le rapport HTML
            publishHTML(target: [
                allowMissing: false,
                alwaysLinkToLastBuild: true,
                keepAll: true,
                reportDir: 'reports',
                reportFiles: 'myreport.html',
                reportName: 'My Reports',
                reportTitles: 'The Report'
            ])
        }
    }