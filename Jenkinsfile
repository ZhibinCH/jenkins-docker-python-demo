node {
    stage('Cleanup') {
        step([$class: 'WsCleanup'])
	echo sh(returnStdout: true, script:'env')
    }
    stage('Checkout SCM') {
        checkout scm
    }
    def pythonImage
    stage('build docker image') {
        pythonImage = docker.build("maxsum:test")
    }
    /*stage('test') {
        pythonImage.inside {
            sh 'python -m pytest --junitxml=build/results.xml'  
        }
    }
    stage('collect test results') {
        junit 'build/results.xml'
    }*/
    stage('clean up the build image'){
    	sh 'docker image rm maxsum:test'
    }
}
