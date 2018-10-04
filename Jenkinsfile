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
        pythonImage = docker.build("maxsum:build")
    }
    stage('test') {
        pythonImage.inside {
            python -m pytest --junitxml=build/results.xml' //sh '. /tmp/venv/bin/activate && 
        }
    }
    stage('collect test results') {
        junit 'build/results.xml'
    }
}
