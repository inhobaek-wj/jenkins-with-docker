pipeline {
    agent any
    environment {
        NEW_VERSION = "1.0.0"
        SERVER_CREDENTIALS = credentials('id-of-credential')
    }

    stages {
        stage("build") {
            steps {
                echo "building..."
            }
        }

        stage("test") {
            steps {
                echo "testing..."
            }
        }

        stage("deploy") {
            steps {
                echo "deploying ${NEW_VERSION}"
            }
        }
    }

    // execute some logic AFTER all stages executed.
    post {
        always {

        }

        success {

        }

        failure {

        }
    }
}
