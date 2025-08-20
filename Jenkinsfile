pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh '''
                  echo "Building project..."
                  date
                '''
            }
        }
    }
    post {
        always {
            emailext (
                to: 'Tanish.Pathania@iiitb.ac.in,Rutul.Patel@iiitb.ac.in,Hemang.Seth@iiitb.ac.in',
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