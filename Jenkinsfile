pipeline{
    agent{ label 'UBUNTU_NODE1' }
    triggers{ pollSCM('* 23 * * 1-5') }
    stages{
        stage('vcs'){
            steps{
                git url: 'https://github.com/srikanthvelma/StudentCoursesRestAPI.git',
                    branch: 'sprint_1_rel'
            }
        }
        stage('build'){
            steps{
                sh 'docker image build -t srikanthvelma/scr:latest .'
            }
        }
        stage('scan and push'){
            steps{
                sh 'docker scan srikanthvelma/scr'
                sh 'docker image push srikanthvelma/scr:latest'
            }
        }
    }
}