@Library('my-first-shared-library') _

pipeline{

    agent any

    tools{
        maven 'MAVEN3.9'
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