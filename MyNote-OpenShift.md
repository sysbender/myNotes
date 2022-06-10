# MyNote-OpenShift


# install minishift

```
minishift config set hyperv-virtual-switch "external-switch"

minishift config set skip-check-hyperv-driver true
 

minishift config set warn-check-hyperv-driver true

 .\minishift.exe start --hyperv-virtual-switch "external-switch"
 
 
```

log

```

V:\tmp\minishift-1.34.3-windows-amd64> .\minishift.exe start --hyperv-virtual-switch "external-switch"                  -- Starting profile 'minishift'                                                                                         -- Check if deprecated options are used ... OK
-- Checking if https://github.com is reachable ... OK
-- Checking if requested OpenShift version 'v3.11.0' is valid ... OK
-- Checking if requested OpenShift version 'v3.11.0' is supported ... OK
-- Checking if requested hypervisor 'hyperv' is supported on this platform ... OK
-- Checking if Powershell is available ... OK
-- Checking if Hyper-V driver is installed ... SKIP
-- Checking if Hyper-V driver is configured to use a Virtual Switch ... SKIP
-- Checking if user is a member of the Hyper-V Administrators group ... SKIP
-- Checking the ISO URL ... OK
-- Downloading OpenShift binary 'oc' version 'v3.11.0'
 53.59 MiB / 53.59 MiB [===================================================================================] 100.00% 0s-- Downloading OpenShift v3.11.0 checksums ... OK
-- Checking if provided oc flags are supported ... OK
-- Starting the OpenShift cluster using 'hyperv' hypervisor ...
-- Minishift VM will be configured with ...
   Memory:    4 GB
   vCPUs :    2
   Disk size: 20 GB

   Downloading ISO 'https://github.com/minishift/minishift-centos-iso/releases/download/v1.17.0/minishift-centos7.iso'
 375.00 MiB / 375.00 MiB [=================================================================================] 100.00% 0s
-- Starting Minishift VM ............................. OK
-- Checking for IP address ... OK
-- Checking for nameservers ... OK
-- Checking if external host is reachable from the Minishift VM ...
   Pinging 8.8.8.8 ... OK
-- Checking HTTP connectivity from the VM ...
   Retrieving http://minishift.io/index.html ... OK
-- Checking if persistent storage volume is mounted ... OK
-- Checking available disk space ... 1% used OK
-- Writing current configuration for static assignment of IP address ... OK
   Importing 'openshift/origin-control-plane:v3.11.0' . CACHE MISS
   Importing 'openshift/origin-docker-registry:v3.11.0' . CACHE MISS
   Importing 'openshift/origin-haproxy-router:v3.11.0' . CACHE MISS
-- OpenShift cluster will be configured with ...
   Version: v3.11.0
-- Pulling the OpenShift Container Image ................... OK
-- Copying oc binary from the OpenShift container image to VM ... OK
-- Starting OpenShift cluster ...............................................................
Getting a Docker client ...
Checking if image openshift/origin-control-plane:v3.11.0 is available ...
Pulling image openshift/origin-cli:v3.11.0
E0224 02:20:29.549288    3790 helper.go:173] Reading docker config from /home/docker/.docker/config.json failed: open /home/docker/.docker/config.json: no such file or directory, will attempt to pull image docker.io/openshift/origin-cli:v3.11.0 anonymously
Image pull complete
E0224 02:20:30.359587    3790 helper.go:173] Reading docker config from /home/docker/.docker/config.json failed: open /home/docker/.docker/config.json: no such file or directory, will attempt to pull image docker.io/openshift/origin-node:v3.11.0 anonymously
Pulling image openshift/origin-node:v3.11.0
Pulled 5/6 layers, 85% complete
Pulled 6/6 layers, 100% complete
Extracting
Image pull complete
Checking type of volume mount ...
Determining server IP ...
Using public hostname IP 192.168.1.194 as the host IP
Checking if OpenShift is already running ...
Checking for supported Docker version (=>1.22) ...
Checking if insecured registry is configured properly in Docker ...
Checking if required ports are available ...
Checking if OpenShift client is configured properly ...
Checking if image openshift/origin-control-plane:v3.11.0 is available ...
Starting OpenShift using openshift/origin-control-plane:v3.11.0 ...
I0224 02:20:50.250921    3790 config.go:40] Running "create-master-config"
I0224 02:20:52.607572    3790 config.go:46] Running "create-node-config"
I0224 02:20:53.525251    3790 flags.go:30] Running "create-kubelet-flags"
I0224 02:20:53.899734    3790 run_kubelet.go:49] Running "start-kubelet"
I0224 02:20:54.086541    3790 run_self_hosted.go:181] Waiting for the kube-apiserver to be ready ...
I0224 02:21:36.100819    3790 interface.go:26] Installing "kube-proxy" ...
I0224 02:21:36.100863    3790 interface.go:26] Installing "kube-dns" ...
I0224 02:21:36.100871    3790 interface.go:26] Installing "openshift-service-cert-signer-operator" ...
I0224 02:21:36.100877    3790 interface.go:26] Installing "openshift-apiserver" ...
I0224 02:21:36.100905    3790 apply_template.go:81] Installing "openshift-apiserver"
I0224 02:21:36.101443    3790 apply_template.go:81] Installing "kube-dns"
I0224 02:21:36.101768    3790 apply_template.go:81] Installing "openshift-service-cert-signer-operator"
I0224 02:21:36.102808    3790 apply_template.go:81] Installing "kube-proxy"
I0224 02:21:40.011549    3790 interface.go:41] Finished installing "kube-proxy" "kube-dns" "openshift-service-cert-signer-operator" "openshift-apiserver"
I0224 02:24:12.044957    3790 run_self_hosted.go:242] openshift-apiserver available
I0224 02:24:12.045652    3790 interface.go:26] Installing "openshift-controller-manager" ...
I0224 02:24:12.045672    3790 apply_template.go:81] Installing "openshift-controller-manager"
I0224 02:24:15.228585    3790 interface.go:41] Finished installing "openshift-controller-manager"
Adding default OAuthClient redirect URIs ...
Adding sample-templates ...
Adding persistent-volumes ...
Adding centos-imagestreams ...
Adding registry ...
Adding router ...
Adding web-console ...
I0224 02:24:15.249065    3790 interface.go:26] Installing "sample-templates" ...
I0224 02:24:15.249075    3790 interface.go:26] Installing "persistent-volumes" ...
I0224 02:24:15.249083    3790 interface.go:26] Installing "centos-imagestreams" ...
I0224 02:24:15.249089    3790 interface.go:26] Installing "openshift-image-registry" ...
I0224 02:24:15.249094    3790 interface.go:26] Installing "openshift-router" ...
I0224 02:24:15.249116    3790 interface.go:26] Installing "openshift-web-console-operator" ...
I0224 02:24:15.249405    3790 apply_template.go:81] Installing "openshift-web-console-operator"
I0224 02:24:15.249525    3790 interface.go:26] Installing "sample-templates/django quickstart" ...
I0224 02:24:15.249533    3790 interface.go:26] Installing "sample-templates/nodejs quickstart" ...
I0224 02:24:15.249540    3790 interface.go:26] Installing "sample-templates/rails quickstart" ...
I0224 02:24:15.249546    3790 interface.go:26] Installing "sample-templates/jenkins pipeline ephemeral" ...
I0224 02:24:15.249551    3790 interface.go:26] Installing "sample-templates/mongodb" ...
I0224 02:24:15.249557    3790 interface.go:26] Installing "sample-templates/mariadb" ...
I0224 02:24:15.249562    3790 interface.go:26] Installing "sample-templates/mysql" ...
I0224 02:24:15.249567    3790 interface.go:26] Installing "sample-templates/cakephp quickstart" ...
I0224 02:24:15.249573    3790 interface.go:26] Installing "sample-templates/sample pipeline" ...
I0224 02:24:15.249579    3790 interface.go:26] Installing "sample-templates/postgresql" ...
I0224 02:24:15.249585    3790 interface.go:26] Installing "sample-templates/dancer quickstart" ...
I0224 02:24:15.249619    3790 apply_list.go:67] Installing "sample-templates/dancer quickstart"
W0224 02:24:15.250383    3790 create_secret.go:78] Error reading $HOME/.docker/config.json: open /home/docker/.docker/config.json: no such file or directory, imagestream import credentials will not be setup
I0224 02:24:15.250422    3790 apply_list.go:67] Installing "centos-imagestreams"
I0224 02:24:15.250815    3790 apply_list.go:67] Installing "sample-templates/mysql"
I0224 02:24:15.251218    3790 apply_list.go:67] Installing "sample-templates/django quickstart"
I0224 02:24:15.251328    3790 apply_list.go:67] Installing "sample-templates/nodejs quickstart"
I0224 02:24:15.251436    3790 apply_list.go:67] Installing "sample-templates/rails quickstart"
I0224 02:24:15.251576    3790 apply_list.go:67] Installing "sample-templates/jenkins pipeline ephemeral"
I0224 02:24:15.251677    3790 apply_list.go:67] Installing "sample-templates/mongodb"
I0224 02:24:15.251783    3790 apply_list.go:67] Installing "sample-templates/mariadb"
I0224 02:24:15.251993    3790 apply_list.go:67] Installing "sample-templates/cakephp quickstart"
I0224 02:24:15.252098    3790 apply_list.go:67] Installing "sample-templates/sample pipeline"
I0224 02:24:15.252236    3790 apply_list.go:67] Installing "sample-templates/postgresql"
I0224 02:24:30.817212    3790 interface.go:41] Finished installing "sample-templates/django quickstart" "sample-templates/nodejs quickstart" "sample-templates/rails quickstart" "sample-templates/jenkins pipeline ephemeral" "sample-templates/mongodb" "sample-templates/mariadb" "sample-templates/mysql" "sample-templates/cakephp quickstart" "sample-templates/sample pipeline" "sample-templates/postgresql" "sample-templates/dancer quickstart"
I0224 02:25:16.948479    3790 interface.go:41] Finished installing "sample-templates" "persistent-volumes" "centos-imagestreams" "openshift-image-registry" "openshift-router" "openshift-web-console-operator"
Login to server ...
Creating initial project "myproject" ...
Server Information ...
OpenShift server started.

The server is accessible via web console at:
    https://192.168.1.194:8443/console

You are logged in as:
    User:     developer
    Password: <any value>

To login as administrator:
    oc login -u system:admin


-- Exporting of OpenShift images is occuring in background process with pid 22256.

```

cmd

```

V:\tmp\minishift-1.34.3-windows-amd64>minishift oc-env
SET PATH=C:\Users\jason.JIGJOG\.minishift\cache\oc\v3.11.0\windows;%PATH%
REM Run this command to configure your shell:
REM     @FOR /f "tokens=*" %i IN ('minishift oc-env') DO @call %i

V:\tmp\minishift-1.34.3-windows-amd64>SET PATH=C:\Users\jason.JIGJOG\.minishift\cache\oc\v3.11.0\windows;%PATH%

V:\tmp\minishift-1.34.3-windows-amd64>oc login -u system:admin

```