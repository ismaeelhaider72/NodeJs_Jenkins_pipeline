pipeline {
  agent any
  environment {
    ssshke = credentials("sshkey")
  }
  tools {nodejs "nodejs"}  
  stages {
        
    stage('Git') {
      steps {
        git branch: 'main', url: 'https://github.com/ismaeelhaider72/NodeJs_Jenkins_pipeline.git'
      }
    }
     
    stage('Build') {
      steps {
        sh 'npm install'
         sh 'tar czf Node.tar.gz node_modules index.js package.json'
      }
    }  
    
            
    stage('Deploy') {
      steps {
        sh "echo succsessszssfully created"
        sh "whoami"
        sh "ls -la"
        sh " scp o 'StrictHostKeyChecking no' -i  $ssh_K Node.tar.gz  ubuntu@3.84.55.80:/home/ubuntu/"
        sh " echo 'Some Text' | ssh -o 'StrictHostKeyChecking no' -i $ssshke  ubuntu@44.201.172.55 -T 'cat > /home/ubuntu/ismaeeltesting.txt' "
      }
    }
  }
}
