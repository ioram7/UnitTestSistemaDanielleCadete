node {
    stage('Build') {
        echo 'Building..'
        deleteDir()
        checkout scm        
    }
    stage('Test') {
        echo 'Testing..'
        sh "sudo docker run -v /home/docker/devops/exercicio3/srv/jenkins/workspace/${JOB_NAME}:/workspace -w /workspace maven:latest mvn install"    
    }
    stage('Deploy') {
        echo 'Deploying....'
    }
}
