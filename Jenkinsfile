[2:52 PM] Praveen Reddy Narayana
pipeline {
agent any
options {
skipStagesAfterUnstable()
}
stages {
stage('Clone repository') {
steps {
script{
checkout scm
}
}
} stage('Build') {
steps {
script{
app = docker.build("underwater")
}
}
}
stage('Test'){
steps {
echo 'Empty'
}
}
stage('Deploy') {
steps {
script{
docker.withRegistry('https://223466935663.dkr.ecr.us-east-1.amazonaws.com/underwater', 'ecr:us-east-1:aws-credentials') {
app.push("${env.BUILD_NUMBER}")
app.push("latest")
}
}
}
}
}
}


