pipeline{
    agent {
        docker{
            image 'barbaraclo/rubywd'
        }
    }
    
    stages{
        stage('Build'){
            steps {
                echo 'Building or Resolving deendences'
                sh 'rm -f Gemfile.lock'
                sh 'bundle install'
            }
        }
        stage('Test'){
            steps {
                echo 'Running regression tests'
                sh 'bundle exec cucumber -p ci'
            }
        }
        stage('UAT'){
            steps {
                echo 'Wait for user accepatance'
                input(message:'Publicsh to production?', ok:'Yes')
            }
        }
        stage('Prod'){
            steps {
                echo 'Web app is ready :)'
            }
        }
    }
}