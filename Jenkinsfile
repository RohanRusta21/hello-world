pipeline{
    agent any
    stages{
        stage ('code checkout'){
            steps{
                echo 'Checkout'
            }
        }
        stage ('Build'){
            steps{
                sh 'mvn clean package'
            }
            post{
                success{
                    echo "Archiving the Artifacts"
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
        stage ('tomcat depoyment'){
            steps{
                echo 'deployment starting'
                deploy adapters: [tomcat8(credentialsId: '91b08ab4-698b-42d2-b38f-9954197caa41', path: '', url: 'http://43.204.147.127:8081')], contextPath: 'hello-world', war: '**/*.war'
            }
        }
    }
}
