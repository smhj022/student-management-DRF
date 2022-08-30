pipeline{
    agent any
    parameters {
        string(name:"VERSION", defaultValue:"1.1.1", description:"This show the verison of the build")
        choice(name:"VERSION", choice:['1.1.0', '1.2.4', '1.4.3'], description:"Some description")
        booleanparam(name: 'executeTests', defaultValue: True, description:"")
    }
    stages {

        stage("init") {
            steps {
                script{
                    gv = load "script.groovy"
                }
            }
        }
        // Different stages of the pipeline is defined in this way
        stage(build) {

            steps {
                script {
                    gv.buildApp()
                }
            }
        }
        stage(test) {
            when {
                expression {
                    params.executeTests == True
                }
            }
            steps {
                script {
                    gv.testApp()
                }
            }

        }
        stage(deploy) {
            steps {
                script {
                    gv.deployApp()
                }
            }
            }
        }
}
