pipeline {
    agent any
    tools {nodejs "null"}
//     {
//         docker {
//             image 'node:lts-bullseye-slim'
//             args '-p 3000:3000'
//         }
//     }
  stages {
//     stage('hello') {
//       steps {
//         bat 'echo "Hello World"'
//       }
//     }
    stage('NPM Build') {
        steps {
            bat 'npm install'
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
