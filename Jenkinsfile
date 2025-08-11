pipeline {
    agent any
    tools {
        maven "MAVEN3.9"
        jdk "JDK17"
    }
    
    environment {
        SNAP_REPO = 'vprofile-snapshot'
		NEXUS_USER = 'admin'
		NEXUS_PASS = '2002'
		RELEASE_REPO = 'vprofile-release'
		CENTRAL_REPO = 'vpro-maven-central'
		NEXUSIP = '172.31.29.120'
		NEXUSPORT = '8081'
		NEXUS_GRP_REPO = 'vpro-maven-group'
        NEXUS_LOGIN = 'nexuslogin'
    }

    stages {
        stage('Build'){
            steps {
                sh 'mvn -s settings.xml -DskipTests install'
            }
            post {
                success {
                    echo ' Now archiving artifacts.'
                    archiveArtifacts artifacts: '**/*.war'
                }
                failure {
                    echo 'Build failed.'
                }
            }
        }

        stage('Test') {
            steps {
                sh 'mvn -s settings.xml test'
            }
            post {
                success {
                    echo 'Test completed successfully.'
                }
                failure {
                    echo 'Test failed.'
                }
            }
        }
        stage('Checkstyle analysis'){
            steps {
                sh 'mvn checkstyle:checkstyle'
            }
        }
    }
}