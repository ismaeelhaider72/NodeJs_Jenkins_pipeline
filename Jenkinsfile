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
        sh "echo Installing remote directory --------------------------"
        sh "ssh -o 'StrictHostKeyChecking no' -i $ssshke  ubuntu@44.201.172.55 < command.txt"
        sh "echo Copying artifact to remote host directory ----------------------" 
        sh " scp -i  $ssshke Node.tar.gz  ubuntu@44.201.172.55:/home/ubuntu/node-app/"
        sh "echo Starting Node app on remote host ---------------------------------" 
        sh "ssh -o 'StrictHostKeyChecking no' -i $ssshke  ubuntu@44.201.172.55 < startNode.txt"
        
      }
    }
  }
}
