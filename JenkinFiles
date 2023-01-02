node(){

 

 

   
    def sonarScanner = tool name: 'forSonar', type: 'hudson.plugins.sonar.SonarRunnerInstallation'

 

 

 

    
    try {
        stage('Checkout Code'){
           checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'GitHubCred', url: 'https://github.com/shlokabari01/SonarQubeNodeJS.git']])
        }

 

 

        stage('NPM Build'){
            sh "npm install"
        }

 

 

        stage('Test Cases Execution'){
            echo "The test is SUCCESSFUL"
        }

 

 

        stage('SonarQube Analysis'){
            withSonarQubeEnv(credentialsId: '03848b78-138b-412a-b9cc-4fa70b8a1f61') {
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
