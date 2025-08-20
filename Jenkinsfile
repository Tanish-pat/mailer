pipeline {
    agent any

    stages {
        stage('Repeated Build') {
            steps {
                script {
                    // Run for 5 minutes (300s) in 30s intervals
                    def start = System.currentTimeMillis()
                    while ((System.currentTimeMillis() - start) < (5 * 60 * 1000)) {
                        echo "Running build cycle at ${new Date()}"
                        sh '''
                          echo "Doing build work..."
                          date
                        '''
                        sleep time: 30, unit: 'SECONDS'
                    }
                }
            }
        }
    }

    post {
        always {
            emailext (
                to: 'Tanish.Pathania@iiitb.ac.in',
                subject: "Build #${env.BUILD_NUMBER} - ${currentBuild.currentResult}",
                body: """
                Project: ${env.JOB_NAME}
                Build: #${env.BUILD_NUMBER}
                Status: ${currentBuild.currentResult}
                URL: ${env.BUILD_URL}
                """.stripIndent()
            )
        }
    }
}
