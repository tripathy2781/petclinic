pipeline {
	agent any
    stages {
        stage('Build on k8 ') {
            steps {           
                        sh 'pwd'
                        sh 'cp -R helm/* .'
		                sh 'ls -ltr'
                        sh 'pwd'
                        sh '/usr/local/bin/helm upgrade --install petclinic-app petclinic'
              			
            }           
        }

        stage('Check upstream job status'){
            steps{
                script{
                    def upstreamjob = buildjob: 'tripathy2781/cloudfreak', propagate: false
                    if(upstreamjob != "SUCCESS"){
                        echo "upstream job status: ${upstreamjob.result}"
                        sh "exit 1"
                    }
                }
            }
        }

    }

}
