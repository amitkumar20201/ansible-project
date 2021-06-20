
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


    stage('Execute Maven') {
           steps {
                sh 'mvn package'             
          }
        }
       
        
    stage('Ansible Deploy') {
             
            steps {
			   //sh "ansible-playbook playbooks/install-tomcat.yaml"
			   sh "ansible-playbook ~/playbooks/install-tomcat.yaml -i etc/ansible/hosts --user ansible --key-file ~/.ssh/id_rsa"
            }
        }
    }
}
