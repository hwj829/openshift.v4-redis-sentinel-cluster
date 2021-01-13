## Reliable, Scalable Redis on Openshift

The following document describes the deployment of a reliable, multi-node Redis on Openshift.  It deploys a master with replicated slaves, as well as replicated redis sentinels which are use for health checking and failover.

### Prerequisites

This example assumes that you have a Openshift cluster installed and running, and that you have installed the ```oc``` command line tool somewhere in your path.


### Run 
    # note: path = redis-openshift'directory path
    #make sure you have base image available
    oc create -f #{path}/redis-openshift/master/openshift/is-base.yaml -n openshift
    #create all components
    oc create -f #{path}/redis-openshift/master/list.yaml
    #start build and watch 
    oc start-build redis-build
    
    #modify the redis image path in dc/redis-master
    #modify the redis image path in dc/redis-sentinel
    
### delete 
    oc delete -f #{path}/redis-openshift/master/openshift/list.yaml -mdc
    oc delete -f #{path}/redis-openshift/master/openshift/is-base.yaml -n mdc
