pipeline {
    agent any 
    stages {
        stage('get-email') {
            steps {
                input("click proceed if you are ready")
                script {
                    def username = input(message:"enter the username")
                    print("username is ${username}")
                }
            }
        }
    }
}
