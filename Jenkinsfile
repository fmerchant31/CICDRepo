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
        stage('Branch Operations') {
            steps {
                script {
                    if(env.BRANCH_NAME == 'Master') {
                        echo "This is Master Branch"
                    }
                    else if(env.BRANCH_NAME == 'DevBranch') {
                        echo "This is DevBranch"
                    }
                    else if(env.BRANCH_NAME == 'QA') {
                        echo "This is QA Branch"
                    }
                    else if(env.BRANCH_NAME == 'Devf') {
                        echo "This is Devf Branch"
                    }
                    else if(env.BRANCH_NAME == 'Devh') {
                        echo "This is Devh Branch"
                    }
                }
                 
            }
           
         
        }
         stage ('Invoke_CD_pipeline') {
            when {
                expression {
                    return env.BRANCH_NAME == 'dev' || env.BRANCH_NAME == 'qa' || env.BRANCH_NAME == 'master';
                }
            }
            steps {
                //build job: 'microservice01-cd', parameters: [string(name: 'GIT_BRANCH_NAME', value: env.BRANCH_NAME)]
               build job: 'CD-demo', propagate: false, wait: false, parameters: [[$class: 'StringParameterValue', name: 'BRANCH_NAME', value: "${env.BRANCH_NAME}"]]
            }
        }
    
    }
      
    }
}
