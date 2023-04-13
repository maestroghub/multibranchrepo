pipeline{
    agent any 
    stages{
        stage('1-git-clone'){
            steps{
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'maestrog-id', url: 'https://github.com/maestroghub/jenkinspracticerepo.git']])
            }  
        }
        stage('2-system update'){
            steps{
                sh 'cat /etc/os-release'
            }
        }
        stage('parallel-job1'){
            parallel{
                stage('security script inject'){
                    steps{
                        sh 'free -g'
                        sh 'uptime'
                    }
                }
            }
        }
        stage('3-resources-check'){
            steps{
                sh 'lscpu'
                sh 'lsblk'
            }
        }
        stage('4-conditional deploy'){
            when{
                branch 'feature'
            }
            steps{
                sh 'uptime'
                sh 'date'
                sh 'pwd'
            }
        }
    }

}
