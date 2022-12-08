# Deploying a webserver using s2i

1. fork this repo and replace the github url in the following commands with your repo

1. create a project<br/>
`oc new-project web-server-test`

1. create a webserver with one of the following options
    - using the top level directory on the main branch<br/>
      `oc new-app nginx~https://github.com/myarbrou-rh/webserver`
    - using the top level directory on a different branch<br/>
      `oc new-app nginx~https://github.com/myarbrou-rh/webserver#feature-branch`
    - using a sub directory<br/>
      `oc new-app nginx~https://github.com/myarbrou-rh/webserver --context-dir=subdir`
    - using a sub directory with a custom configuration<br/>
      `oc new-app nginx~https://github.com/myarbrou-rh/webserver --context-dir=configured`

1. expose the webserver service to the outside world<br/>
`oc expose service/webserver`

1. start a new build (after updating the repo)<br/>
`oc start-build webserver`<br/>
or add webhook for continuous deployment<br/>
see step 5 here https://developer.ibm.com/tutorials/continuous-deployment-s2i-and-webhooks/

1. remove the application<br/>
`oc delete all -l app=webserver`
