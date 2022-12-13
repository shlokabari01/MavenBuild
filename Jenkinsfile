pipeline{
agent any
stages('CI CD Pipeline'){
  stage('Code Checkout'){
    steps{
        script{
            git credentialsId: '78a21b74-cac5-48b8-be2d-05065af02ae67', url: 'https://github.com/shlokabari01/MavenBuild.git'            }
        }
    }
  
  stage('Build'){
    steps{
        script{
            sh "mvn clean install -Dmaven.test.skip=true"
        }
    }  
  }
  stage('Test'){
    steps{
        script{
            sh "mvn clean org.jacoco:jacoco-maven-plugin:prepare-agent install -Pcoverage-per-test"
        }
    }  
  }
}
}
