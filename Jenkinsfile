
pipeline {
    agent any
    
    tools
    {
       maven "mymvn"
    }
     
    stages {
      stage('checkout') {
           steps {
                git branch: 'master', url: 'https://github.com/amitkumar20201/maven-app.git'
          }
        }
    stage('Tools Init') {
            steps {
                script {
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
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
			   //sh "ansible-playbook playbooks/install-tomcat.yaml"
			   sh "ansible-playbook playbooks/install-tomcat.yaml -i etc/ansible/hosts --user ansible --key-file ~/.ssh/id_rsa"
            }
        }
    }
}
