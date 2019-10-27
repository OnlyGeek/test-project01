pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'echo "Hello World"'
        sh '''
                    echo "Multiline shell steps works too"
                    ls -lah
                '''
        archiveArtifacts 'test.sh'
      }
    }
    stage('Test') {
      steps {
        sh 'echo "testing..."'
        sh '''
                    echo "Multiline shell steps works too"
                    ls -lah
                '''
      }
    }
    stage('Deploy') {
      steps {
        sh 'echo "Deploying"'
        sshPublisher(publishers: [sshPublisherDesc(configName: 'test', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'pwd && ls -al', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: '', sourceFiles: 'test.sh')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
      }
    }
  }
}