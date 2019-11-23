node('maven') {
  stage('SCM') {
    checkout poll: false, scm: [$class: 'GitSCM', branches: [[name: 'refs/heads/develop']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/CodeBabel/MEANStackApp.git']]]
    }
  stage('SonarQube Analysis') {
        def scannerLoc = tool 'sonar-scanner1'
        withSonarQubeEnv(credentialsId:'sonar_token',installationName:'sonarqube-server') {
        sh "${scannerLoc}/bin/sonar-scanner  -Dsonar.host.url=http://10.168.0.11:9000 -Dsonar.projectName=maven -Dsonar.projectVersion=1.0 -Dsonar.projectKey=maven "
    }
  }
}
