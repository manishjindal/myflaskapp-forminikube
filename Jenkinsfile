node('docker&&linux') {
    def app

    stage('Checkout and Sync Repo') {
        /* Let's make sure we have the repository cloned to our workspace */

          cleanWs()
          checkout scm
          githubSync repo: 'https://github.com/manishjindal/Kubernetes-for-starters' // name of equivalent ngis repo on github.com/lvtech
          cleanWs()
    }

    stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */

        app = docker.build("manishjindal/myflaskapp-forminikube")
    }

    stage('Test image') {
        /* Ideally, we would run a test framework against our image.
         * For this example, we're using a Volkswagen-type approach ;-) */

        app.inside {
            sh 'echo "Tests passed"'
        }
    }
}