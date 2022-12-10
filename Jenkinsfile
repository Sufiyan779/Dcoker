pipeline{
    agent {label 'OPENJDK-11'}

    environment{
        dockerhub=credentials('dockerhub')
    }

    stages{
        stage('pullig from svs'){
            steps{
                git url:'https://github.com/DevprojectsForDevOps/StudentCoursesRestAPI',
                branch: 'master'    
            }
        }
        stage('build image'){
            steps{
                sh 'docker image build -t mystudentapi:1.0 .'    
            }
        }
        stage('pushing image into docker hub '){
            steps{
                sh 'docker tag mystudentapi:1.0 sfn411/mystudentapi:1.0'
                sh 'echo $dockerhub_PSW | docker login -u $dockerhub_USR --password-stdin'
                sh 'docker push sfn411/mystudentapi:1.0'    
            }
        }
        stage('create container'){
            steps{
                sh 'docker container run -d -p 5000:8080 mystudentapi:1.0'
            }
        }
    }
}