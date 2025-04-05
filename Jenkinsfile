pipeline {
    agent { label 'master' }

    stages {
        stage("Build") {
            parallel {
                stage('BACK_1') {
                    steps {
                        script {
                            build job: 'project/Templates/BACK_1', parameters: 
                            [string(name: 'BUILD_BRANCH', value: '${BUILD_BRANCH}'),
                            string(name: 'BUILD_PROJECT', value: '${BUILD_PROJECT}'),
                            string(name: 'BUILD_NUMBER', value: '${BUILD_NUMBER}')], 
                            propagate: true, wait: true
                        }
                    }
                }
                stage('BACK_2') {
                    steps {
                        script {
                            build job: 'project/Templates/BACK_2', parameters: 
                            [string(name: 'BUILD_BRANCH', value: '${BUILD_BRANCH}'), 
                            string(name: 'BUILD_PROJECT', value: '${BUILD_PROJECT}'), 
                            string(name: 'BUILD_NUMBER', value: '${BUILD_NUMBER}')], 
                            propagate: true, wait: true
                        }
                    }
                }
                stage('FRONT') {
                    steps {
                        script {
                            build job: 'project/Templates/FRONT', parameters: 
                            [string(name: 'BUILD_BRANCH', value: '${BUILD_BRANCH}'), 
                            string(name: 'BUILD_PROJECT', value: '${BUILD_PROJECT}'), 
                            string(name: 'BUILD_NUMBER', value: '${BUILD_NUMBER}')], 
                            propagate: true, wait: true
                        }
                    }
                }
            }
        }
    }
}