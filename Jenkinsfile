pipeline {
    agent any 
    stages {
        stage('get-email') {
            steps {
                input("click proceed if you are ready")
                script {
                     input(id:'userInput', message:'enter the username', parameters:[string(name:'username')])
                    print("username is ${userInput.username}")
                }
            }
        }
    }
}
