pipeline{
    agent any
    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub')
    }

    stages {
            stage ('Build') {
            steps {
                    sh 'docker build -t kellylight/kelly:002 .'
            }
            }

        stage ('Login') {
            steps {
                    sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }

        stage ('Push') {
            steps {
                    sh 'docker push kellylight/kelly:002'
            }

            post {
                always {
                    sh 'docker logout'
                }
            }
        }
    }
}
