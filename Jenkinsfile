pipeline {
    agent any 
    stages {
        stage('get-email') {
            steps {
                input("click proceed if you are ready")
                script {
                    def username = input("enter the username")
                }
            }
        }
    }
}
