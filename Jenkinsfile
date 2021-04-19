pipeline {
    agent any 
    stages {
        stage('get-contacts') {
            steps {
                script {

                    def username = input(
                        message:'enter the username', 
                        parameters:[
                            string(name:'username')
                        ]
                    )
                    
                    def operation = input(
                        message: "Choose the operation",
                        parameters: [
                            [
                                $class: "ChoiceParameterDefinition",
                                choices: ["Add", "Get", "Update", "Delete"].join('\n'),
                                name: 'operation'
                            ]
                        ]
                    )
                    
                    if (operation == "Add" or operation == "Update") {
                        
                        def username = input(
                            message:'enter the field name and value', 
                            parameters:[
                                string(name:'fieldname'),
                                string(name:'fieldvalue')
                            ]
                        )
                        
                        def response = sh(
                            script:"python3 /home/dinesh/programs/python/get-contact.py ${operation} ${username} ${fieldname} ${fieldvalue}", 
                            returnStdout:true
                        )
                        
                    } else {
                        
                        def response = sh(
                            script:"python3 /home/dinesh/programs/python/get-contact.py ${operation} ${username}", 
                            returnStdout:true
                        )
                        
                    }
                    
                    def (key, value) = response.split(":")
                    if (key == "result") {
                        def (emailId, mobile, work) = value.split(";")
                        print("contact details for ${username} is ")                    
                        print("emailId : ${emailId}")
                        print("mobile : ${mobile}")
                        print("work : ${work}")
                    } else {
                        print(value)
                    }
                    
                }
            }
        }
    }
}
