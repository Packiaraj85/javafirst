pipeline {
    agent any

    tools {
        maven 'maven'
    }

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
                        stage('Unit Test'){
                            steps{
                                script{
                                    echo("Unit Test")
                                    sh 'mvn test'
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
                stage('validate'){
                    steps{
                        script{

                            sh 'mvn validate'
                            echo('validate Test success')
                        }
                    }
                }
              stage('Quvality verify'){
                    steps{
                        script{
                            sh 'mvn verify'
                            echo('verify Test success')
                        }
                    }
                }
            }
        }
        stage('Deploy'){
            steps{
                script{
                    sh 'mvn install'
                    echo('Deploy success')                
                }
            }
        }
    }
}
