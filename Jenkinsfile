pipeline {
    agent {
        node { 
            label 'ansible' 
        }
    }

    stages {
        stage('clean_directory') {
            steps {
                //sh 'sudo sh /home/jenkins/myscripts/deletemyfirstpipeline.sh'
                //sh 'rm -rf /home/jenkins/workspace/firstpipeline'
                sh 'ansible-playbook /etc/ansible/my_yaml/cleanwebappartifact.yaml'
                
            }
            /*steps {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    sh "exit 1"
                }
            }*/
            
        }
        stage('git_checkout') {
            steps {
                git 'https://github.com/nileshpatel111/hello-world.git'
            }
        }
        stage('build_hello-world') {
            steps {
                sh 'mvn clean verify'
            }
        }
        
        stage('deploy_hello-world') {
            steps {
                sh 'ansible-playbook /etc/ansible/my_yaml/copyhelloworldwar.yaml'
            }
        }
    }
}
