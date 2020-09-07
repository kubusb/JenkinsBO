pipeline {
  agent any
  stages {
    stage('CheckoutCode') {
      steps {
        git(branch: 'master', url: 'https://github.com/kubusb/gol', poll: true)
      }
    }

    stage('Build') {
      steps {
        node(label: 'master') {
          sh 'mvn clean install'
        }

      }
    }

    stage('error') {
      steps {
        emailext(subject: 'Build complete', body: 'Build completed', attachLog: true, compressLog: true, from: 'jenkins@redbit.pl', to: 'jenkins@redbit.pl')
      }
    }

  }
}