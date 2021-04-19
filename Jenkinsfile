pipeline {
    agent any 
    stages {
        stage('get-email') {
            steps {
                script {
                    def username = input(message:'enter the username', parameters:[string(name:'username')])
                    def emailId = sh(script:"python3 /home/dinesh/programs/python/get-emailId.py ${username}", returnStdout:true)
                    print("emailId for ${username} is ${emailId}")
                }
            }
        }
    }
}
