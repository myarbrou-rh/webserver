
create a project
oc new-project web-server-test

# create a new application
oc new-app nginx~https://github.com/myarbrou-rh/webserver

# create a new application using a branch
oc new-app nginx~https://github.com/myarbrou-rh/webserver#use-s2i

# create a new application using a branch and a sub directory
oc new-app nginx~https://github.com/myarbrou-rh/webserver#use-s2i --context-dir=simple

# remove the application
oc delete all -l app=webserver