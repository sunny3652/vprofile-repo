pipeline {
   agent any

   tools {
      // Install the Maven version configured as "M3" and add it to the path.
      maven "maven"
   }

   stages {
      stage('git') {
         steps {
            // Get some code from a GitHub repository
            git credentialsId: '34c57263-6151-4845-b217-9c22fd3694e9', url: 'https://github.com/sunny3652/game-of-life.git'
}
}
stage('maven'){
    steps{

            // Run Maven on a Unix agent.
            sh label: '', script: 'mvn install'
}
}
stage('nexus')
{
    steps{
        nexusPublisher nexusInstanceId: '1234', nexusRepositoryId: 'releases', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: '', filePath: 'gameoflife-web/target/gameoflife.war']], mavenCoordinate: [artifactId: 'game-of-life', groupId: 'dev', packaging: '.war', version: '$BUILD_ID']]]
    }
}
   
    }
}
            
