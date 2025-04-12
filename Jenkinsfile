@Library('my-first-shared-library') _

pipeline{

    agent any

    tools{
        maven 'MAVEN3.9'
    }

    environment{
        MAVEN_OPTS = '--add-opens jdk.compiler/com.sun.tools.javac.processing=ALL-UNNAMED'
    }

    parameters{
        choice(name: 'action', choices: 'create\ndelete', description: 'choose create/destroy')
    }


    stages{
        
        stage('Git Checkout'){
            
            when{
                expression{ params.action == 'create' }
            }

            steps{                
                
                script{
                    
                    checkoutCode("https://github.com/svishal16/java_app.git", "main")
                }
            }
        }

        stage('Maven Test'){

            when{
                expression{ params.action == 'create' }
            }
            
            steps{                
                
                script{
                    
                    mvnTest()
                }
            }
        }

        stage('Maven Int Test'){

            when{
                expression{ params.action == 'create' }
            }
            
            steps{                
                
                script{
                    
                    mvnIntegrationTest()
                }
            }
        }

        stage('Static Code Analysis: Sonarqube'){

            when{
                expression{ params.action == 'create' }
            }
            
            steps{                
                
                script{
                    
                    staticCodeAnalysis()
                }
            }
        }



    }


}