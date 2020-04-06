pipeline {
    agent {
        dockerfile {
            filename 'Dockerfile.build'
        }
    }
    stages {
        stage('Dependencies') {
            steps {
                sh 'cargo fetch'
            }
        }
        stage('Build') {
            steps {
                sh 'cargo build --release'
            }
        }
        stage('Test') {
            steps {
                sh 'cargo test --release'
            }
        }
        stage('Publish') {
            steps {
                archiveArtifacts 'flat-manager-client'
                archiveArtifacts 'target/release/delta-generator-client'
                archiveArtifacts 'target/release/flat-manager'
                archiveArtifacts 'target/release/gentoken'
            }
        }
    }
}
