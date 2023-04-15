pipeline{

agent any

stages{

stage('Checkout'){

steps{

git branch: "main", url: 'https://github.com/SURJEET3010/spring-gateway.git'

}

}

stage('Build'){

steps{

sh 'chmod a+x mvnw'

sh './mvnw clean package -DskipTests=true'

}

post{

always{

archiveArtifacts 'target/*.jar'

}

}

}

stage('DockerBuild') {

steps {

sh 'docker build -t surjeet007/g2-api-gateway-service:latest .'

}

}

stage('Login') {

steps {

sh 'echo QAZwsx@1234 | docker login -u surjeet007 --password-stdin'

}

}

stage('Push') {

steps {

sh 'docker push surjeet007/g2-api-gateway-service'

}

}

}

post {

always {

sh 'docker logout'

}

}

}
