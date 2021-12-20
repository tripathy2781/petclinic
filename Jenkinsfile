pipeline {
  agent any

  parameters {
    imageTag(name: 'DOCKER_IMAGE', description: '',
             image: 'trip27/petclinic', defaultTag: '14',
             registry: 'https://hub.docker.com', credentialId: '', tagOrder: 'ASCENDING')
  }

  stages {
    stage('Generate tag Input') {
      steps {
        echo "$DOCKER_IMAGE" // will print selected image name with tag (eg. trip27/petclinic:13)

    stage('Build on k8 ') {
       steps {           
        sh 'pwd'
        sh 'cp -R helm/* .'
		sh 'ls -ltr'
        sh 'pwd'
        sh '/usr/local/bin/helm upgrade --install petclinic-app petclinic ${DOCKER_IMAGE}'
    }    

      }
    }
  }
}
}
