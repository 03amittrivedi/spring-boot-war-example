pipeline{
    agent any
     tools{
         maven "Mav363"
     }
        

    stages{
        stage("Show Maven Version"){
            steps{
                sh "mvn --version"
                echo "This stage will show only MVN Version"
            }
        }
        stage("Deploy On test Server Tomcat9"){
            steps{
                // Deploy the WAR to Tomcat9 server 172.31.46.104
                deploy adapters: [tomcat9(credentialsId: '829818ec-ed33-421d-bca4-abae502f9426', path: '', url: 'http://172.31.46.104:8080')], contextPath: '/app', war: '***/*.war'
                echo "This stage will Deploy WAR file to Tomcat9 Server"
            }
        }
    }

    post{
        always{
            echo "============Always========"
        }
        success{
            echo "=============Sucess========"
        }
        failure{
            echo "============failure========="
        }
    }
}
