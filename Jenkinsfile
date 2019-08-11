pipeline {
    agent any

    stages {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'localmaven') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'localmaven') {
                    sh 'mvn test'
                }
            }
        }

        stage ('Package stage')
        {
            steps {
                        withMaven(maven : 'localmaven')
                        {
                            sh 'mvn package'
                        }            
        }
      
        }
        
        
        stage ('delploy on tomcat')
        {
            steps {
                    sshagent(['tomcat-dev']){
                     
                       sh 'scp -o StrictHostKeyChecking=no target/*.war -p 22 ec2-user@http://13.57.204.176:/var/lib/tomcat/webapps/'
                 }
        }
        }
}
}
