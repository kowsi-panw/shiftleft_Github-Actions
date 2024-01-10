//this method doesn't work as it needs cross NS access from Jenkins - TODO check 

node {

    stage('Clone repository') {
        checkout scm
    }

    //initial setup
    stage('Initial setup') {
        withCredentials([usernamePassword(credentialsId: 'PCC_CONSOLE_URL', passwordVariable: 'PRISMA_SECRET_KEY', usernameVariable: 'PRISMA_ACCESS_KEY')]) {
            sh('chmod +x prep/setup.sh && ./prep/setup.sh')
        }     
    }

    //policy creation
    stage('Apply initial policies') {
        withCredentials([usernamePassword(credentialsId: 'PCC_CONSOLE_URL', passwordVariable: 'PRISMA_SECRET_KEY', usernameVariable: 'PRISMA_ACCESS_KEY')]) {
            sh('chmod +x prep/extra_policies.sh && ./prep/extra_policies.sh')
        }
    }
}