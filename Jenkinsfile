def repository_name = 'JenkinsTest'
def git_url = "git@github.com:085astatine/${repository_name}.git"

node {
    stage('echo') {
        echo 'Hello World'
        sh(script: "pwd")
    }
    stage('git') {
        if(fileExists("./${repository_name}")) {
            sh(script: "cd ./${repository_name} && git fetch origin")
            sh(script: "cd ./${repository_name} && git pull origin master")
        } else {
            sh(script: "git clone ${git_url}")
        }
    }
    stage('make') {
        sh(script: "cd ./${repository_name} && clang++ main.cpp")
    }
    stage('run') {
        sh(script: "cd ./${repository_name} && ./a.out")
    }
}
