pipeline{
    agent{
        docker{
            image 'maven:3-alpine'
            args '-v /root/.m2:/root/.m2'
        }
    }
    stages{
        stage("Build"){
            steps{
                echo "========executing Build========"
                sh 'mvn -B -DskipTests clean package'
            }
            post{
                always{
                    echo "========always========"
                }
                success{
                    echo "========A executed successfully========"
                }
                failure{
                    echo "========A execution failed========"
                }
            }
        }
        stage("Test"){
            steps{
                echo "====++++executing Test++++===="
                sh 'mvn test'
            }
            post{
                always{
                    echo "====++++always++++===="
                    junit 'target/surefire-reports/*.xml'
                }
                success{
                    echo "====++++Test executed succesfully++++===="
                }
                failure{
                    echo "====++++Test execution failed++++===="
                }
        
            }
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}