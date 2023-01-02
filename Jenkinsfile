

node(){
def sonarScanner = tool name: 'SonarScanner', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
stage('Code Checkout'){
    git credentialsId: 'Repourl', url: 'https://github.com/hellopriya123/SonarQubeNodeJS_new.git'
}


stage('Build & Test Automation'){
    sh """
        ls -lart
        npm install
       """

}
stage('Deployment'){
      withSonarQubeEnv(credentialsId: 'SonarQubeToken') {
    sh "${sonarScanner}/bin/sonar-scanner"
    }
}
}
