## Labs to do with OpenShift Origin VM ##

To get the VM:

````
vagrant init jmorales/origin-labs && vagrant init
````

To get latest image:

````
vagrant destroy && vagrant box update --box jmorales/origin-labs && vagrant up
````

This labs are included in origin-labs vm and installed like this:
````
oc adm new-project labs
oc create -f https://raw.githubusercontent.com/jorgemoralespou/strapdown-lighttpd-s2i/master/ose3/strapdown-lighttpd-s2i-template.json -n labs
oc new-app strapdown-lighttpd-s2i-template -p APP_NAME=labs -p TITLE='Red Hat Summit Labs' -p GIT_REF=summit-labs -p APP_HOSTNAME=labs.apps.10.2.2.2.xip.io -n labs
````

To update to latest content (As it is installed as admin user, need to login as such):

````
oc login https://10.2.2.2:8443 --insecure-skip-tls-verify -u admin -p admin
oc start-build labs -n labs
oc logout
````
