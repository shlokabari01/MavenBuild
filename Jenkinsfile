

node(){

    def mvnHome = tool 'MavenBuildTool'
    def sonarScanner = tool name: 'SonarQube', type: 'hudson.plugins.sonar.SonarRunnerInstallation'

 

    
    try {
        stage('Checkout Code'){
            checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'GitHubCred', url: 'https://github.com/shlokabari01/MavenBuild.git']])
        }

        stage('Maven Build'){
            sh "${mvnHome}/bin/mvn clean install -Dmaven.test.skip=true"
        }

        stage('Test Cases Execution'){
            sh "${mvnHome}/bin/mvn test"
        }

        stage('SonarQube Analysis'){
            withSonarQubeEnv(credentialsId: '5b27e7f4-248f-4da0-975d-6717cae07ec9') {
                sh "${sonarScanner}/bin/sonar-scanner"

}
        }


    }
    catch (Exception e){
        currentBuild.result = 'FAILURE'
        
        echo currentBuild.currentResult
    }finally{
        emailext body: 'Your project is done with deployment.', subject: 'Build Successfully', to: 'shlokabari5@gmail.com'
    }
}
