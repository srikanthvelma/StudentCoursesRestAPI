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
                sh 'docker image build -t srikanthvelma/scr:latest .'
            }
        }
        stage('scan and push') {
            steps{
                sh 'docker image push srikanthvelma/scr:latest'
                sh 'docker scan srikanthvelma/scr'
            }
        }
    }
}