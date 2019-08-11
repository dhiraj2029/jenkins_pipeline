pipeline {
    agent any

    stages {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'LocalMaven') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'LocalMaven') {
                    sh 'mvn test'
                }
            }
        }

        stage ('Package stage')
        {
            steps {
                        withMaven(maven : 'LocalMaven')
                        {
                            sh 'mvn package'
                        }            
        }
      
        }
        
        
        stage ('delploy on tomcat')
        {
            steps {
                    sshagent(['tomcat-dev']){
                     
                       sh 'scp -o StrictHostKeyChecking=no target/*.war http://13.232.136.207:8080/var/lib/tomcat/webapps/'
                 }
        }
        }
}
}
