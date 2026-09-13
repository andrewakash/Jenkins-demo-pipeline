pipeline{
    agent any
    environment{
        App_name = "Myapplication"
        Version = "1.0"
    }
    tools {
        maven 'Maven-3.9.16'
    }

    parameters{
            choice(
                name: 'Environment',
                choices: ['Development', 'Staging', 'Production'],
                description: 'Select the environment for deployment'
            )
        }          
    stages{
        stage('Build'){
            steps{
                bat 'mvn -version'
                bat 'mvn clean package'
            }
        }
        stage('Test'){
            steps{
                bat 'mvn test'
            }
        }
        stage('Deployment'){ 
            when{
                branch 'main'
            }
            steps{
                echo "Deploying the project....."
                echo "Deployment completed successfully"
                echo "current directory is ${env.WORKSPACE}"
            }
        }   
        }
        post{
            success{
                echo "Pipeline executed successfully"
            }
            failure{
                echo "Pipeline execution failed"
                }
            always{
                echo "Pipeline execution completed"
            }
        }   
        }

