pipeline {
    agent any 
    stages {
      stage ('Build Account update') {
        steps{
    sh 'ls -lrth'
  sshagent(['sshkey-bastion-dev']) {
    sh '''
    hostname
    ls -lrth
    export bastiondevip=`echo $bastiondevip`
    scp -r -o StrictHostKeyChecking=no dev.sh root@${bastiondevip}:/home/satya/
    ssh -o StrictHostKeyChecking=no root@${bastiondevip} <<EOF
    hostname
    pwd
    ls -lrth
    echo environment is $env    
    sh -x ${env}.sh
EOF
    '''
  }
}
}
}
}
