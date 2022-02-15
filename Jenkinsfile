pipeline{
    agent any
    environment {
           BRANCH_NAME = "${GIT_BRANCH.split("/")[1]}"
    }
    stages{
        stage('Git Branch') {
            steps {
               checkout([$class: 'GitSCM', branches: [[name: '*/*']], userRemoteConfigs: [[credentialsId: 'b271cfaf-6789-4c9e-a00a-e7ccab300d39', url: 'git@github.com:fmerchant31/CICDRepo.git' ]]])
            }
        }
        stage('Branch Name') {
            steps { 
                   echo "Current Branch Name:  "+ env.BRANCH_NAME
            }
        }
    }
}
