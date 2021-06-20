
pipeline {
    agent any
    
    tools
    {
       maven "Maven"
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
			   sh "ansible-playbook playbooks/install-tomcat.yaml"
            }
        }
    }
}
