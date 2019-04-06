def username = 'Jenkins'
env.CC = 'clang'
node {
    stage('Build') {
        env.DEBUG_FLAGS = '-g'
        echo 'Building..'
        echo "Hello Mr. ${username}"
        echo "Running ${env.JOB_NAME} (${env.BUILD_ID}) at ${env.JENKINS_URL}"  
        deleteDir()
        checkout scm
        sh "echo 'res' > result"
        stash includes: '**/result', name: 'app'
            if (env.BUILD_ID.toInteger() % 2 == 0) {
                echo 'Execucao PAR'
            } else {
                echo 'Execucao IMPAR'
            }
    }
    stage('Test') {
        echo 'Testing..'
        sh "sudo docker run -v /home/docker/devops/exercicio3/srv/jenkins/workspace/${JOB_NAME}:/workspace -w /workspace maven:latest mvn install"    
    }
    stage('Deploy') {
        echo 'Deploying....'
    }
}
