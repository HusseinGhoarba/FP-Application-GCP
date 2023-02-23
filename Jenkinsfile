pipeline {
    agent { label 'jenkins-slave' }
    stages {
        stage('build') {
            steps {
                    sh   """
                        docker build -t gcr.io/hussein-ghoraba/hello-vois ./app/
                        docker push gcr.io/hussein-ghoraba/hello-vois
                    """
            }
        }
        stage('deploy') {
            steps {
                    sh    """
                        kubectl apply -f k8s-files
                    """
            }
        }
    }
}
