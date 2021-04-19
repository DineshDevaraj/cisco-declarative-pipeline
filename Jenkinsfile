pipeline {
    agent any 
    stages {
        stage('get-email') {
            steps {
                script {
                    def username = input(message:'enter the username', parameters:[string(name:'username')])
                    def contact = sh(script:"python3 /home/dinesh/programs/python/get-contact.py ${username}", returnStdout:true)
                    def (emailId, mobile, work) = contact.split(";")
                    print("contact details for ${username} is ")                    
                    print("   emailId : ${emailId}")
                    print("   mobile : ${mobile}")
                    print("   work : ${work}")
                }
            }
        }
    }
}
