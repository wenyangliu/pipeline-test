pipeline {
    //指定运行此流水线的节点
    agent any

    options {
        timestamps()
        timeout(time: 5, unit: 'MINUTES')
        skipDefaultCheckout()
    }

    //流水线的阶段
    stages {
        //阶段1 获取代码
        stage("CheckOut"){
            steps {
                script{
                    println("获取代码")
                }
            }
        }
        stage("Build"){
            steps{
                script{
                    println("运行构建")
                }
            }
        }
    }

    post {
        always {
            script{
                println("流水线结束后，经常做的事情")
            }
            emailext(
                subject: "Hi: Job '${env.PROJECT_NAME} [${env.BUILD_NUMBER}]'",
                body: """<p>SUCCESSFUL: Job '${env.PROJECT_NAME} [${env.BUILD_NUMBER}]':</p>
                <p>Check console output at "<a href="${env.BUILD_URL}">${env.PROJECT_NAME} [${env.BUILD_NUMBER}]</a>"</p>""",
                to: "1753439422@qq.com,2079905596@qq.com",
                from: "18860469266admin@163.com"
            )
        }

        success{
            script{
                println("流水线成功后，要做的事情")
            }
        }

        failure{
            script{
                println("流水线失败后，要做的事情")
            }
        }

        aborted{
            script{
                println("流水线取消后，要做的事情")
            }
        }
    }
}
