node {
    stage('Download from Git') {
        git branch: 'dev', url: 'https://github.com/anagendrakumar/mvn.git'
    }

    stage('Build Artifact') {
        sh 'mvn clean package'
    }

    stage('Deploy to Tomcat9') {
        deploy adapters: [
            tomcat9(
                credentialsId: 'dev-env',
                path: '',
                url: 'http://13.233.156.177:8080',
                alternativeDeploymentContext: ''
            )
        ],
        contextPath: 'devapp',
        war: '**/*.war'
    }
}

