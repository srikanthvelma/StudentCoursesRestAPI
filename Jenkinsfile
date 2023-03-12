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
                sh 'docker image build -t srikanthvelma/SCR:latest .'
            }
        }
        stage('scan and push') {
            steps{
                sh 'docker image push srikanthvelma/SCR:latest'
                sh 'docker scan srikanthvelma/SCR'
            }
        }
    }
}