@Library('my-first-shared-library') _

pipeline{

    agent any

    tools{
        maven 'MAVEN3.9'
    }

    environment {
        MAVEN_OPTS = '''
            --add-opens jdk.compiler/com.sun.tools.javac.processing=ALL-UNNAMED
            --add-opens jdk.compiler/com.sun.tools.javac.util=ALL-UNNAMED
            --add-opens jdk.compiler/com.sun.tools.javac.api=ALL-UNNAMED
            --add-opens jdk.compiler/com.sun.tools.javac.code=ALL-UNNAMED
            --add-opens jdk.compiler/com.sun.tools.javac.comp=ALL-UNNAMED
            --add-opens jdk.compiler/com.sun.tools.javac.model=ALL-UNNAMED
            --add-opens jdk.compiler/com.sun.tools.javac.tree=ALL-UNNAMED
            --add-opens jdk.compiler/com.sun.tools.javac.main=ALL-UNNAMED
            --add-opens jdk.compiler/com.sun.tools.javac.jvm=ALL-UNNAMED
            --add-opens jdk.compiler/com.sun.tools.javac.file=ALL-UNNAMED
        '''.trim()
        SONAR_SERVER = 'java-app-sonar' 
        SONAR_PROJECT_KEY = 'java-app-cicd'
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