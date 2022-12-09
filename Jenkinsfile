pipeline{
    agent {label 'OPENJDK-11'}

    stages{
        stage('cloning git repo into node'){
            steps{
                sh 'git clone https://github.com/DevprojectsForDevOps/StudentCoursesRestAPI'
                sh 'cd StudentCoursesRestAPI'    
            }
        }
        stage('build image'){
            steps{
                sh 'docker image build -t mystudentapi:1.0 .'    
            }
        }
        stage('pushing image into docker hub '){
            steps{
                sh 'docker tag mystudentapi:1.0 sufiyan/mystudentapi:1.0 '
                sh 'docker login -u sfn411 -p sufiyankhan@786'
                sh 'docker push sufiyan/mystudentapi:1.0'    
            }
        }
    }
}