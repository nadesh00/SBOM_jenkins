pipeline {
    agent any
    tools { go 'go1.19'}

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
//     stage('NPM Build') {
//         steps {
//             bat 'npm install'
//             }
//         }
//     stage('Build') {
//                 steps {
//                     nodejs(nodeJSInstallationName: 'Node 6.x', configId: '38807f22-9655-4bdd-afa6-a4a42c938a43') {
//                         bat 'npm config ls'
//                     }
//                 }
//             }

    stage ('Generating Software Bill of Materials') {
        steps {
            //Building the dependencies to generate SBoM
            bat './gradlew cyclonedxBom'
            //bat 'echo JENKINS HOME DIRECTORY'
            //bat 'cyclonedx-bom -o /{JENKINS HOME DIRECTORY}/reports/sbom.xml'
            }
        }
    }

    post {
            always {
                archiveArtifacts artifacts: 'build/reports/bom.xml', onlyIfSuccessful: true
            }
        }
}
