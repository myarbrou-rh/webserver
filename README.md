
# create a project
oc new-project web-server-test

# create a new application
oc new-app nginx~https://github.com/myarbrou-rh/webserver

# create a new application using a branch
oc new-app nginx~https://github.com/myarbrou-rh/webserver#use-s2i

# create a new application using a branch and a sub directory
oc new-app nginx~https://github.com/myarbrou-rh/webserver#use-s2i --context-dir=simple

# expose the webserver service to the outside world
oc expose service/webserver

# start a new build (after updating the repo)
oc start-build webserver

# remove the application
oc delete all -l app=webserver