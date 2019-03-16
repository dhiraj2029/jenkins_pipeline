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
            steps{
                    sshagent(['tomcat-dev'])
                       sh 'scp -o StrickHostKeyChecking=no target/*.war admin2@http://13.57.209.47:/opt/tomcat7/webapps/'
                 }
        }
}
}
