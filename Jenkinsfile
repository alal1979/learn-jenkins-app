pipeline {
  agent any

  stages {
    stage('Build'){
      agent {
        docker {
          image 'node:18-alpine'
          reuseNode true
        }
      }


      steps {
        sh '''
          ls -la
          node --version
          npm --version
          npm ci
          npm run build
          npm test
          ls -la
        '''
      } 
   
    }

    stage('Test'){
      steps  {
        sh '''
          if [-f "/build/index.html"  ]; then 
            echo "파일 존재 "
          else 
            echo "파일 없음 "
          fi

        '''
      } 
    }
  }
}