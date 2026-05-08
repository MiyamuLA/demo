pipeline {
    agent any
    tools {
        maven 'maven'
        jdk 'jdk17'
    }
    stages {
        stage('1. 拉取代码') {
            steps {
                git url: 'https://github.com/MiyamuLA/demo.git', branch: 'master'
            }
        }
        stage('2. 单元测试') {
            steps {
                sh 'mvn test'
            }
        }
        stage('3. 打包构建') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }
    }
    post {
        success {
            echo "============================================="
            echo " ✅ 构建成功！"
            echo " jar 包在你阿里云服务器这里："
            echo " /root/docker/jenkins/jenkins_home/workspace/second-pipeline/target/demo-0.0.1-SNAPSHOT.jar"
            echo "============================================="
        }
        failure {
            echo "❌ 构建失败！"
        }
    }
}
