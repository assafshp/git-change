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
                    // myfarr = myf.split(' ');
                    myfarr = myf.split()
                    myfl = myfarr.size()
                    echo '--------------'
                    echo "$myfarr"
                    echo '--------------'
                    echo "$myfl"
                    echo '--------------'
                    for (int i = 0; i < myfarr.size(); i++) {
                        // sh "echo Hello ${myfarr[i]}"
                        sh(returnStdout: true, script: 'echo aaa' )
                    }
                    //for( String values : myfarr )
                    //    println('aaa' + values);
                }
                
                //echo "changed folders: $myf"
                //echo "changed folders arr: $myfarr"
                //int_for_loop(myfarr)
                
                // for file in $myf
                //     do echo file
                // done
            
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
        // stage('Test 4') {
        //     steps{
        //         int_for_loop(myfarr) 
        //     }
           
        // }
        // stage('Test 2: loop of sh commands') {
            
        // }
    }
}


// def int_for_loop(list) {
//     sh "echo Going to echo a list"
//     for (int i = 0; i < list.size(); i++) {
//         sh "echo Hello ${list[i]}"
//     }
// }


