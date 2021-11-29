def postmanImage = "projectrp/newman-reportportal:v12"

pipeline {
      agent {
        docker {
          image "${postmanImage}"
          args '-v $pwd/security/:/newman --entrypoint='
        }
      }
  stages {
    stage('Postman-Report-test') {
      steps {
        checkout scm
        catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
        sh "ls -la"
        sh "pwd"
        sh "which newman"
        sh "which node"
        sh "which npm"
        sh "node --version"
        sh "npm --version"
        
        sh "newman run jmeter/collection.json \
    -r @reportportal/agent-js-postman \
    --reporter-@reportportal/agent-js-postman-debug=true \
    --reporter-@reportportal/agent-js-postman-endpoint=https://reportportal.dev.juiceplus.net \
    --reporter-@reportportal/agent-js-postman-token=cee4c7e2-57f9-4b42-a29f-fdfdc683bd4a \
    --reporter-@reportportal/agent-js-postman-launch=superadmin_TEST_EXAMPLE \
    --reporter-@reportportal/agent-js-postman-project=juiceplus \
    --reporter-@reportportal/agent-js-postman-description=security_report \
    -x"
      }
     }
    }
    }
  }
