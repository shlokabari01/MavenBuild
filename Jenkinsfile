

node(){
def sonarScanner = tool name: 'SonarQube: 'hudson.plugins.sonar.SonarRunnerInstallation'
stage('Code Checkout'){
    git credentialsId: 'GitHubCred', url: 'https://github.com/shlokabari01/MavenBuild.git'
}


stage('Build & Test Automation'){
    sh """
        ls -lart
        mvn clean install
       """

}
stage('Deployment'){
     withSonarQubeEnv(credentialsId: '03848b78-138b-412a-b9cc-4fa70b8a1f61') {
    sh "${sonarScanner}/bin/sonar-scanner"
    }
}
}
