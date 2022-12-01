pipeline {
  agent any
  stages {
    stage('hello') {
      steps {
        bat 'echo "Hello World"'
      }
    }
    stage ('Generating Software Bill of Materials') {
        steps {
            //Building the dependencies to generate SBoM
            bat 'npm install'
            bat 'cyclonedx-bom -o /{JENKINS HOME DIRECTORY}/reports/sbom.xml'
        }
    }
  }
}
