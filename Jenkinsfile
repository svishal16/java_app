@Library('my-first-shared-library') _

pipeline{

    agent any

    stages{
        
        stage('Git Checkout'){
            
            steps{                
                
                script{
                    
                    checkoutCode("https://github.com/svishal16/java_app.git", "main")
                }
            }
        }

        stage('Git Checkout'){
            
            steps{                
                
                script{
                    
                    mvnTest()
                }
            }
        }



    }


}