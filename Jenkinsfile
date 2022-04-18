pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Running build automation'
                sh './gradlew build --no-daemon'
                archiveArtifacts artifacts: 'dist/trainSchedule.zip'
            }
        }
        stage('Build Docker Image') {
            when {
                branch 'master'
            }
                app = docker.build("ishankharel/train-schedule")
        }
        stage('Test Image') {
            app.inside {
               sh 'echo "test passed"'
            }
        }
    }
}
