pipeline {
    agent any

    stages {
        stage('Create File') {
            steps {
                script {
                    sh '''
                    echo '#include <iostream>' > program.cpp
                    echo 'using namespace std;' >> program.cpp
                    echo 'int main() {' >> program.cpp
                    echo '    cout << "Hello, Jenkins!" << endl;' >> program.cpp
                    echo '    return 0;' >> program.cpp
                    echo '}' >> program.cpp
                    '''
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    sh 'g++ -o PES2UG22CS564 program.cpp' 
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    sh './PES2UG22CS564' 
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    sh '''
                    git config --global user.name "PES2UG22CS564"
                    git config --global user.email "snehagowdasnehagowda912@gmail.com"
                    git add program.cpp
                    git commit -m "Added new C++ file"
                    git push origin main
                    '''
                }
            }
        }
    }

    post {
        failure {
            echo 'pipeline failed'
        }
    }
}
