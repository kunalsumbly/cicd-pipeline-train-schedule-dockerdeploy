pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Running build automation'
                sh './gradlew build --no-daemon'
                archiveArtifacts artifacts: 'dist/trainSchedule.zip'
            } // build step end
        } // build stage end 
        stage('Build Docker Image') { // build docker image stage
            when {
                branch 'master' // only when the branch is master
            }
            steps {
                script {
                    app = docker.build("kunalsumbly/train-schedule")
                    /*app.inside {
                        sh 'echo $(curl localhost:8080)'
                    }*/
                }
            } // build docker step ends
        } // build docker stage ends
        
        
        
        
    } // stage end
}// pipeline end
