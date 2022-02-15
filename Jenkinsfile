pipeline{
    agent any
    stages{
        stage('git added') {
            steps {
                git branch: '/*',
                credentialsId: 'b271cfaf-6789-4c9e-a00a-e7ccab300d39',
                url: 'git@github.com:fmerchant31/CICDRepo.git'
            }
        }
        stage('Branch Name') {
            steps { 
                   echo "Current Barnch Name:  "+ env.BRANCH_NAME 
            }
        }
    }
}
