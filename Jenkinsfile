pipeline {
    agent any 
    stages {
        stage('get-email') {
            steps {
                input("click proceed if you are ready")
                script {
                    def userInput = input(message:'enter the username', parameters:[string(name:'username')])
                    print("username is ${userInput}")
                }
            }
        }
    }
}
