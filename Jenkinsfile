pipeline {
    agent any
    stages {
        stage("Build") {
            steps {
                sh './mvnw -Dmaven.test.failure.ignore=true clean verify'
            }
        }
        stage("Reports") {
            steps {
                allure([
         includeProperties: false,
         jdk: '',
         properties: [[key: 'allure.issues.tracker.pattern', value: 'http://tracker.company.com/%s']],
         reportBuildPolicy: 'ALWAYS',
         results: [[path: 'target/allure-results'], [path: 'other_target/allure-results']]
         ])
            }
        }
    }
    post {
        always {
            deleteDir()
        }
    }
}
