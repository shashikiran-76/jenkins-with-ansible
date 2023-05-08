pipeline {
  agent { 
  label 'ansiblenodes'
  }
  
  environment {
   AWS_EC2_PRIVATE_KEY=credentials('ec2instance-private-key') 
  }
  
  stages {
    
    //Get the Code from GitHub Repo
    stage('CheckOutCode'){
      steps{
      git credentialsId: '20ecd865-5685-433a-89c1-b6a3f95eb541', url: 'https://github.com/shashikiran-76/jekins-ansible-dynimc-inv.git'          
  }
    }
    //Run the playbook
    stage('RunPlaybook') {
      steps {
        sh "ansible-playbook -i inventory/walmart.hosts --private-key=$AWS_EC2_PRIVATE_KEY playbooks/installTomcat9.yaml --ssh-common-args='-o StrictHostKeyChecking=no'"
      }
    }
  
  }//stages closing
}//pipeline closing
