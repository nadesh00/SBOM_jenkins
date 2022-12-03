pipeline {
    agent any
    tools { go 'go1.19'}

    stages {
        stage ('Generating Software Bill of Materials') {
            steps {
                //Building the dependencies to generate SBoM
                bat './gradlew cyclonedxBom'
            }
        }
        stage ('Scanning the sbom') {
            steps {
                bat 'go install github.com/google/osv-scanner/cmd/osv-scanner@latest'
                bat 'go get github.com/google/osv-scanner/cmd/osv-scanner'
                bat 'go run github.com/google/osv-scanner/cmd/osv-scanner --json --sbom=build/reports/bom.json'
            }
        }
    }
    post {
            always {
                archiveArtifacts artifacts: 'build/reports/bom.json', onlyIfSuccessful: true
            }
        }
}
