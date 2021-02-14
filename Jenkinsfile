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
    parameters {  // 3종류의 parameter가 있음.
        string(name: 'VERSION', defaultValue: '', description: 'version to deploy on prod')
        choice(name: 'VERSION', choices: ['1.1.0', '1.2.0', '1.3.0'], description: '')
        booleanParam(name: 'executeTests', defaultValue: true, description: '')
    }

    stages {
        stage("build") {
            steps {
                echo "building..."
            }
        }

        stage("test") {
            when {
                expresstion {
                    params.executeTests
                }
            }

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
