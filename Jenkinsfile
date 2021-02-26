pipeline {
  agent any
  stages {
    stage('Ejecucion') {
      // https://www.jenkins.io/doc/book/pipeline/syntax/#environment
      environment {
        AMBIENTE = "${params.ambiente}"
        DOMINIO = "${params.dominio}"
        MANAGED = "${params.managed}"
        AMBIENTE_PARAMS = "${AMBIENTE}"
        DOMINIO_PARAMS = "${DOMINIO}"
        MANAGED_PARAMS = "${MANAGED}"
        HOST = "${sh(script:'''grep "${AMBIENTE}" $WORKSPACE/AMBIENTES | cut -d " " -f 2''',returnStdout: true).trim()}"
        WLST = "/u01/app/oracle/product/fmw/oracle_common/common/bin/wlst.sh"
        //PY = "/home/orawl/JenkinsScriptWls/RestartManagedServerJenkins.py"
        //PY = "${$WORKSPACE/RestartManagedServerJenkins.py}"
        PROPERTIES_TXT = "/home/orawl/JenkinsScriptWls/ConnectionPropertiesJenkinsPreProd.txt"
      }
      steps {
        echo 'Ejecucion'
        echo '${AMBIENTE_PARAMS}'
        // Reemplazar credencial por la correcta en el credential store de jenkins
        // https://www.jenkins.io/doc/book/using/using-credentials/
        // https://www.jenkins.io/doc/pipeline/steps/ssh-agent/
        // https://www.jenkins.io/doc/pipeline/steps/workflow-durable-task-step/#sh-shell-script
      }
    }
  }
  // https://www.jenkins.io/doc/book/pipeline/syntax/#parameters
  parameters {
    string(name: 'ambiente', description: 'Ambiente')
    string(name: 'dominio', description: 'Dominio')
    string(name: 'managed', description: 'Secuencia de managed servers a reiniciar ( 1 2 3 ) o ESCALONADO')
  }
}
