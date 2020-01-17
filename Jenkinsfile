pipeline{
    agent none
    stages{
        stage('Compile'){
            agent any
            steps{
                sh 'mvn compile'
            }
        }
        stage('Unit Test'){
            agent any
            steps{
                sh 'mvn test'
            }
            post{
                always{
                    junit 'gameoflife-web/target/surefire-reports/*.xml'
                }
            }
        }
        stage('Package'){
            agent {label 'linux_slave'}
            steps{
                git 'https://github.com/azatrump/game-of-life.git'
                sh 'mvn package'
            }
        }
    }
}
