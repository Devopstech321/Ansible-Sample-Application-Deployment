pipeline {
    agent any
     
    stages {
      stage('checkout') {
           steps {
             
                git branch: 'master', url: 'https://github.com/Devopstech321/Ansible-Sample-Application-Deployment.git'
             
          }
        }
        
        
        
          stage('Ansible Init') {
            steps {
                script {
                
               def tfHome = tool name: 'Ansible'
                env.PATH = "${tfHome}:${env.PATH}"
                 sh 'ansible --version'
                    
            }
            }
        }

        stage('Execute Maven') {
           steps {
             
                sh 'mvn package'             
          }
        }
        
        stage('Ansible Deploy') {
             
            steps {
                 
             
               
               sh "ansible-playbook main.yml -i inventories/dev/hosts --user jenkins --key-file ~/.ssh/id_rsa -e '@configs/dev.yml'"

               
            
            }
        }
    }
}
