pipeline{
    agent any
     tools{
         maven "Mav363"
     }
        

    stages{
        stage("MVN Unit Test"){
            steps{
                sh "mvn test"
                echo "This stage will perform Unit test"
            }
        }
        stage("Cretae WAR"){
            steps{
                sh "mvn package"
                echo "This stage will cerate WAr package"
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
