@Library('my-first-shared-library') _

pipeline{

    agent any

    tools{
        maven 'MAVEN3.9'
    }

    environment{
        MAVEN_OPTS = '--add-opens jdk.compiler/com.sun.tools.javac.processing=ALL-UNNAMED'
    }


    stages{
        
        stage('Git Checkout'){
            
            steps{                
                
                script{
                    
                    checkoutCode("https://github.com/svishal16/java_app.git", "main")
                }
            }
        }

        stage('Maven Test'){
            
            steps{                
                
                script{
                    
                    mvnTest()
                }
            }
        }



    }


}