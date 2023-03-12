pipeline {
    agent { label 'UBUNTU_NODE1' }
    triggers { pollSCM('* * * * *') }
    stages {
        stage('vcs') {
            steps{
                git url: 'https://github.com/srikanthvelma/StudentCoursesRestAPI.git',
                    branch: 'develop'
            }
        }
        stage('build') {
            steps{
                sh 'docker build image -t srikanthvelma/SCR:latest .'
            }
        }
        stage('scan and push') {
            steps{
                sh 'docker push image srikanthvelma/SCR:latest'
                sh 'docker scan srikanthvelma/SCR'
            }
        }
    }
}