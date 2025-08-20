pipeline {
    agent any

    stages {
        stage('Repeated Build') {
            steps {
                script {
                    def start = System.currentTimeMillis()
                    def duration = 5 * 60 * 1000  // 5 minutes

                    while ((System.currentTimeMillis() - start) < duration) {
                        echo "Running build cycle at ${new Date()}"

                        sh '''
                          echo "Doing build work..."
                          date
                        '''

                        emailext (
                            to: 'Tanish.Pathania@iiitb.ac.in,Rutul.Patel@iiitb.ac.in,Hemang.Seth@iiitb.ac.in',
                            subject: "Mailer iteration at ${new Date()}",
                            body: """\
Build cycle iteration finished.

Job: ${env.JOB_NAME}
Build: #${env.BUILD_NUMBER}
Time: ${new Date()}
"""
                        )

                        sleep time: 30, unit: 'SECONDS'
                    }
                }
            }
        }
    }
}
