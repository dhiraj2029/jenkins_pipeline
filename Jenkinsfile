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
                      sh 'ssh -t -t -p 22 root@http://13.57.209.47:/var/lib/tomcat/webapps/'
                       sh 'scp -o StrictHostKeyChecking=no target/*.jar -p 22 root@http://13.57.209.47:/var/lib/tomcat/webapps/'
                 }
        }
        }
}
}
