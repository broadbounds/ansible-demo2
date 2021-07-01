pipeline {
    agent any
     
    environment {
    VAULT_PASSWORD_FILE = credentials('VAULT_FILE')
   }
    
    stages {
      stage('checkout') {
           steps {
             
                git branch: 'main', url: 'https://github.com/broadbounds/ansible-demo2.git'
             
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
        
        
        
        stage('Ansible Deploy') {
             
            steps {
                 
             
               
                sh "ansible-playbook -i inventory.ini playbook.yml  --vault-password-file '$VAULT_PASSWORD_FILE'"

}
}
}
}
