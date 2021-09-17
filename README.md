# webserver
git clone git@github.com:myarbrou-rh/webserver.git
cd webserver
oc new-project webserver
oc new-app --name default .
oc start-build default --from-dir=.
oc expose service/default