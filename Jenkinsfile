def exitCode = 0
node {
    stage('Build') {
      node("master") {
        echo 'Building..'
        deleteDir()
        checkout scm

//        def ambiente = input id: 'test', message: 'Please Provide Parameters', ok: 'Next',
//           parameters: [
//              choice(name: 'Deseja continuar com a execução do JOB?',
//                  choices: ['Sim!','Não!'].join('\n'),
//                  description: 'Selecione a opção desejada'),
//              string(name: 'EXIT',
//                  defaultValue: '0',
//                  description: 'Informe o código para continuar.')
//           ]
//        exitCode = ambiente['EXIT']
//        echo "${ambiente}"
          
//        sh "echo 'res' > result"
        stash includes: '**', name: 'app'
        
//        try {
//            sh "exit ${exitCode}"
//            echo 'Testes Unitários - Sucesso!'
//        }
//        catch (e) {
//            echo 'Falha na execução!'
//            // throw e
//        }
//        finally {
//            echo '..'
//       }
      }    
    }
    stage('Test') {
      node("slave") {
        echo 'Testing..'
        deleteDir()
        unstash 'app'
        sh "sudo chown -R jenkins: ${WORKSPACE}" 
        sh "mvn clean install"
//      sh "sudo docker run -v /Users/iss/devops/exercicio3/srv/jenkins/workspace/${JOB_NAME}@2:/workspace -w /workspace maven:latest mvn install"    
      }
    }    
//    stage('Deploy') {
//      node() {
//        echo 'Deploying....'
          
//        deleteDir()
//        unstash 'app'
//        sh 'cat result'
//        archiveArtifacts artifacts: '**/result', fingerprint: true
//      }  
//    }
}
