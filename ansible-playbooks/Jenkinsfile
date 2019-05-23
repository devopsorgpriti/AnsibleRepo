node {
   
   
   stage ('Checkout') {
    checkout scm
  }
   
    stage('gitclone') {
       git credentialsId: '125e426e-8bec-43ab-9282-96a7f24dcea4', url: 'https://github.com/pragathi-devopsgroup/ansible-playbooks.git'
       sh label: '', script: '''cd /var/tmp
                                git clone https://github.com/pragathi-devopsgroup/ansible-code.git/
                                cd ansible-code
                                ls -al'''
    }
    
    stage ('ansible command') {
        sh ''' cd /var/tmp/ansible-code
                ansible-playbook --syntax-check $PlaybookName'''
    }
    
    stage ('removingdirectory') {
        
        sh 'rm -rf /var/tmp/ansible-code'
    }
   
    stage ('Notification') {
    mail from: "jenkinstesting@gmail.com",
         to: "premkumar.unix@gmail.com",
         subject: "ansible deployement status ",
         body: "Jenkins job ${env.JOB_NAME} - build ${env.BUILD_NUMBER}  ${currentBuild.currentResult}  ${env.JOB_URL} complete"
  }
    
}
