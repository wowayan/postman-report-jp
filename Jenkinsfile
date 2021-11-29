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
        
     sh "newman run collection.json \ 
	-r @reportportal/agent-js-postman \
	--reporter-@reportportal/agent-js-postman-debug=true \
	--reporter-@reportportal/agent-js-postman-endpoint=http://localhost:8080/api/v1 \
	--reporter-@reportportal/agent-js-postman-token=5645304b-57fa-4896-87d7-48182574a1f4 \
	--reporter-@reportportal/agent-js-postman-launch=superadmin_TEST_EXAMPLE \
	--reporter-@reportportal/agent-js-postman-project=superadmin_personal \
	--reporter-@reportportal/agent-js-postman-description=security_report \  
	-x"
      }
     }
    }
    }
  }
