pipeline {
    agent any
    environment {
        NEW_VERSION = "1.0.0"
        SERVER_CREDENTIALS = credentials('id-of-credential')
    }
    tools {
        // 오직 아래 3개만 사용 가능. 나머진 따로 설치/설정이 필요.
        // maven
        // gradle
        // jdk
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
            when {
                expression {
                    BRANCH_NAME == "dev"
                }
            }

            steps {
                echo "deploying ${NEW_VERSION}"

                // Credentials Bindings plugin 필요.
                withCredentials([
                    usernamePassword(credentials: 'id-of-credential', 
                                     usernameVariable: USER, 
                                     passwordVariable: PWD)
                ]) {
                    sh "some script ${USER} ${PWD}"
                }
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
