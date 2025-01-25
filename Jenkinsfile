properties([
    parameters([
        string(description: 'version', name: 'tag'),
        choice(choices: ['development','production'], description: "target deployment environment", name: "target"),
    ])
])
node("${target}") {
    // we need to add ssh executor here to execute this 
    stage("checkout"){
        checkout scm
    }
    stage("promote"){
        env.SOBEAMVERSION = env.tag
        withCredentials([
            string(credentialsId: 'DBNAME', variable: 'DBNAME'),
            string(credentialsId: 'DBUSER', variable: 'DBUSER'),
            string(credentialsId: 'DBPASS', variable: 'DBPASS'),
        ]) {
            sh "docker compose up sobeam -d"
        }
    }
    stage("notification"){
        echo "add notification here"
    }
}