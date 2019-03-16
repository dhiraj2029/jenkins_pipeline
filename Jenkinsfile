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
}
