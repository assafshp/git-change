# git-change

pipeline {
    agent any
    //agent { docker { image 'node:14-alpine' } }
    // parameters {
    //     string(name: 'FOLDERS', defaultValue: 'product1 product3')
    // }



    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Clone sources') {
            steps {
                git url: 'https://github.com/assafshp/git-change.git', branch: 'change-3'
            }
        }
        stage('build') {
            steps {
                sh 'ls'
                sh 'pwd'
                sh 'git status'
                script {
                    myf = sh(returnStdout: true, script: 'git diff --dirstat=noncumulative --name-only master| grep  .')
                }
                echo "changed folders: $myf"
            
                //myf = sh(returnStdout: true, script: 'ls')
                //echo 'myf=$myf'
                
                //sh 'ls'
                //sh 'git status'
                //sh 'git diff --dirstat=noncumulative --name-only master| grep  .'
                //echo 'assaf'
                //git diff --dirstat=noncumulative --name-only master
                //def MY_FILES = sh ('git diff --dirstat=noncumulative --name-only master')
                //powershell 'git status'
                //sh 'echo $MY_FILES'
                //echo "Hello ${params.FOLDERS}"
            }
        }
    }
}




