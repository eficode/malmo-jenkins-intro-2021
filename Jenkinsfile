
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh './gradlew build'
            }
        }

        stage('Test') {
            steps {
                sh './gradlew test'
            }
        }

        stage('Deploy') {
            steps {
                rtUpload (
            serverId: 'artifactory',
            spec: """ {
                "files": [
                {
                    "pattern": "build/distributions/menkins.zip",
                    "target": "example-repo-local/helloLaroy/${env.BUILD_NUMBER}/"
]
                }
        }""")
            }
        }
}}
