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
                    withMaven(maven : 'LocalMaven'){
                     
                       sh 'scp -o StrictHostKeyChecking=no **/*.jar /var/lib/tomcat/webapps/'
                 }
        }
        }
}
}
