import groovy.json.JsonSlurper

pipeline {

    agent any

    stages {

        stage('get contact details') {

            steps {

                script {

                    def username = null
                    stage('enter the username') {

                        username = input(
                            message:'enter the username',
                            parameters:[
                                string(name:'username')
                            ]
                        )
                    }

                    def operation = null
                    stage('choose the operation') {

                        operation = input(
                            message: "Choose the operation",
                            parameters: [
                                [
                                    $class: "ChoiceParameterDefinition",
                                    choices: ["Add", "Get", "Update", "Delete"].join('\n'),
                                    name: 'operation'
                                ]
                            ]
                        )
                    }

                    def response = null
                    stage('talk to backend') {

                        if (operation == "Add" || operation == "Update") {

                            def fieldRecord = input(
                                message:'enter the field name and value',
                                parameters:[
                                    string(name:'fieldname'),
                                    string(name:'fieldvalue')
                                ]
                            )

                            response = sh(
                                script:"python3 /home/dinesh/programs/python/get-contact.py ${operation} ${username} ${fieldRecord.fieldname} ${fieldRecord.fieldvalue}",
                                returnStdout:true
                            )

                        } else {

                            response = sh(
                                script:"python3 /home/dinesh/programs/python/get-contact.py ${operation} ${username}",
                                returnStdout:true
                            )

                        }

                    }
                    
                    stage('process response') {

                        print(response)
                        def slurper = new JsonSlurper()
                        def jsonObj = slurper.parseText(response)
                        def value = jsonObj.values()[0]

                        if (jsonObj.containsKey("result")) {
                            
                            def (emailId, mobile, work) = value.split(";")
                            
                            input(message:
                                "contact details for ${username} are \n" +
                                "--------------------------------------------- \n" +
                                "emailId: ${emailId}\n" +
                                "mobile: ${mobile}\n" +
                                "work:${work}\n" +
                                "--------------------------------------------- \n" +
                                "click proceed to finish build"
                            )
                                  
                        } else {
                            
                            input(message:
                                "message \n" +
                                "--------------------------------------- \n" +
                                value + "\n" +
                                "--------------------------------------- \n" +
                                "click proceed to finish build"
                            )
                            
                        }
                        
                        print("process response end")

                    } /* process response end */

                } /* script end */

            } /* steps end */

        } /* get contact details end */

    } /* stages end */

} /* pipeline end */
