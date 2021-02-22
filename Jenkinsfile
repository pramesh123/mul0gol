pipeline {
    agent { label 'ltecomm'}
    triggers { cron('H * * * 1-5') }
    stages {
        stage ('scm') {
            steps {
                git branch : 'developer' , url 'https://github.com/pramesh123/mul0gol.git'
            }

        }
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage ('post build') {
            steps {
            archiveArtifacts artifacts: 'gameoflife-web/target/gameoflife.war', fingerprint: true
            stash name: 'warfile', includes: 'gameoflife-web/target/*.war'
        }
        }
        
        
    }


}