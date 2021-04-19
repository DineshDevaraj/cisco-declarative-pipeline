pipeline {
    agent any 
    stages {
        stage('get-email') {
            steps {
                script {
                    def userInput = input(message:'enter the username', parameters:[string(name:'username'), string(name:'mobile')])
                    print("username is ${userInput}")
                }
            }
        }
    }
}
