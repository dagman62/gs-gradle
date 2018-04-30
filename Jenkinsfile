node {
  def myGradleContainer = docker.image('dagman62/gradle-alpine')
  myGradleContainer.pull()
  stage('prep') {
    checkout scm
  }
  stage('test') {
     myGradleContainer.inside("-v ${env.HOME}/.gradle:/home/gradle/.gradle") {
       sh 'cd complete && ./gradlew test'
     }
  }
  stage('run') {
     myGradleContainer.inside("-v ${env.HOME}/.gradle:/home/gradle/.gradle") {
       sh 'cd complete && ./gradlew run'
     }
  }
}
