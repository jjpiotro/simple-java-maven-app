pipeline{
    agent{
        docker {
            image 'maven:3-alpine'
            args '-v /root/.m2:/root/.m2'
        }
        label "node"
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