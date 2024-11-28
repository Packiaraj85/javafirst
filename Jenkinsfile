pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script{
                    sh 'mvn clean package'
                }
            }
        }
        stage('Tests') {
            parallel{
                stage('nested loop1') {
                    stages{
                        stage('Test A'){
                            steps{
                                script{
                                    echo("Test A")
                                }
                            }
                        }
                        stage('Test B'){
                            steps{
                                script{
                                    echo('Test B')
                                }
                            }
                        }
                    }
                }
                stage('Perfomance Test'){
                    steps{
                        script{
                            echo('Perfomance Test success')
                        }
                    }
                }
              stage('Quvality Test'){
                    steps{
                        script{
                            echo('Quvality Test success')
                        }
                    }
                }
            }
        }
        stage('Deploy'){
            steps{
                script{
                    echo('Deploy success')                
                }
            }
        }
    }
}
