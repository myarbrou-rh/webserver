
# create a project
oc new-project web-server-test

# create a webserver
oc new-app nginx~https://github.com/myarbrou-rh/webserver

# create a webserver using a branch
oc new-app nginx~https://github.com/myarbrou-rh/webserver#use-s2i

# create a webserver using a branch and a sub directory
oc new-app nginx~https://github.com/myarbrou-rh/webserver#use-s2i --context-dir=subdir

# create a webserver with a custom nginx.conf
oc new-app nginx~https://github.com/myarbrou-rh/webserver#use-s2i --context-dir=configured

# expose the webserver service to the outside world
oc expose service/webserver

# start a new build (after updating the repo)
oc start-build webserver

# remove the application
oc delete all -l app=webserver

# add webhook for continuous deployment
# see step 5 here https://developer.ibm.com/tutorials/continuous-deployment-s2i-and-webhooks/