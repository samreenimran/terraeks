pipeline {
    agent any

    stages {
        stage('install') {
            steps {
              sh 'mkdir /home/ec2-user/terra'
              sh 'cd terra'
              sh 'wget https://releases.hashicorp.com/terraform/0.12.23/terraform_0.12.23_linux_amd64.zip'
              sh 'yum install unzip -y'
              sh 'unzip terraform_0.12.23_linux_amd64.zip'
              sh 'echo $"export PATH=\$PATH:$(pwd)" >> ~/.bash_profile'
              sh 'source ~/.bash_profile'
              echo 'terraform done'             
              sh  'curl -o kubectl https://amazon-eks.s3-us-west-2.amazonaws.com/1.14.6/2019-08-22/bin/linux/amd64/kubectl'
	         	  sh  'curl -o kubectl.sha256 https://amazon-eks.s3-us-west-2.amazonaws.com/1.14.6/2019-08-22/bin/linux/amd64/kubectl.sha256'
              sh  'openssl sha1 -sha256 kubectl'
              sh  'chmod +x ./kubectl'
              sh  'mkdir -p $HOME/bin && cp ./kubectl $HOME/bin/kubectl && export PATH=$PATH:$HOME/bin'
              sh  'echo 'export PATH=$PATH:$HOME/bin' >> ~/.bashrc'
              sh  'kubectl version --short --client'
              sh  'mkdir ~/.kube'                                 
              sh  'touch ~/.kube/config-eks'
              echo 'kubectl done'
              sh  'curl -o aws-iam-authenticator https://amazon-eks.s3-us-west-2.amazonaws.com/1.14.6/2019-08-22/bin/linux/amd64/aws-iam-authenticator'
		          sh  'chmod +x ./aws-iam-authenticator'
		          sh  'mkdir -p $HOME/bin && cp ./aws-iam-authenticator $HOME/bin/aws-iam-authenticator && export PATH=$PATH:$HOME/bin'
		          echo 'iam done'
		
            }
        }
        
    }
}
