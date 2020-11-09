/**
 * Bugscout Jenkinsfile
 */

def config = [
    "PIPE_LINE":"iast"];

timeout(time: 12, unit: 'HOURS') {
    node('maven') {

        library "jenkins-ci-cd-shared-library@develop";

        def jenkins;

        try {

            jenkins = configurePipeline(config);

            runWorkflow(jenkins);

            notifySuccess(jenkins);

        } catch (Exception e) {

            notifyFailure(jenkins, e);

            throw e;

        } finally {
            cleanWs();
        }

    }
}
