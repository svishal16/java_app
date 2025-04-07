pipeline{

    agent any

    stages{
        
        stage('Git Checkout'){
            steps{                
                script{
                    gitCheckout(
                        branch: "main",
                        url: "https://github.com/svishal16/java_app.git"
                    )
                }
            }
        }



    }


}