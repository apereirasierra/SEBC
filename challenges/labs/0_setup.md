cloud provider : AWS 

Instances by IP address: 172.31.30.111, 172.31.17.111, 172.31.25.158, 172.31.17.189, 172.31.24.238

Instances by DNS name ec2-52-89-163-140.us-west-2.compute.amazonaws.com, ec2-34-211-247-48.us-west-2.compute.amazonaws.com, ec2-35-160-165-91.us-west-2.compute.amazonaws.com, ec2-52-26-101-212.us-west-2.compute.amazonaws.com, ec2-52-34-122-45.us-west-2.compute.amazonaws.com

Linux release cat /etc/redhat-release Red Hat Enterprise Linux Server release 7.3 (Maipo) 

File system capacity sudo df -h 
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda2       80G  8.7G   72G  11% /
devtmpfs         15G     0   15G   0% /dev
tmpfs            15G     0   15G   0% /dev/shm
tmpfs            15G   25M   15G   1% /run
tmpfs            15G     0   15G   0% /sys/fs/cgroup
tmpfs           3.0G     0  3.0G   0% /run/user/1000
tmpfs           3.0G     0  3.0G   0% /run/user/0
cm_processes     15G     0   15G   0% /run/cloudera-scm-agent/process
tmpfs           3.0G     0  3.0G   0% /run/user/996

Command and output for: yum repolist enabled
Loaded plugins: amazon-id, rhui-lb, search-disabled-repos
Repo rhui-REGION-client-config-server-7 forced skip_if_unavailable=True due to: /etc/pki/rhui/cdn.redhat.com-chain.crt
Repo rhui-REGION-client-config-server-7 forced skip_if_unavailable=True due to: /etc/pki/rhui/product/rhui-client-config-server-7.crt
Repo rhui-REGION-client-config-server-7 forced skip_if_unavailable=True due to: /etc/pki/rhui/rhui-client-config-server-7.key
Repo rhui-REGION-rhel-server-releases forced skip_if_unavailable=True due to: /etc/pki/rhui/cdn.redhat.com-chain.crt
Repo rhui-REGION-rhel-server-releases forced skip_if_unavailable=True due to: /etc/pki/rhui/product/content-rhel7.crt
Repo rhui-REGION-rhel-server-releases forced skip_if_unavailable=True due to: /etc/pki/rhui/content-rhel7.key
Repo rhui-REGION-rhel-server-rh-common forced skip_if_unavailable=True due to: /etc/pki/rhui/cdn.redhat.com-chain.crt
Repo rhui-REGION-rhel-server-rh-common forced skip_if_unavailable=True due to: /etc/pki/rhui/product/content-rhel7.crt
Repo rhui-REGION-rhel-server-rh-common forced skip_if_unavailable=True due to: /etc/pki/rhui/content-rhel7.key

Add the following Linux accounts to all nodes
sudo groupadd comets;
sudo groupadd planets;
sudo useradd –u 2800 -G planets saturn;
sudo useradd –u 2900 –G comets haley;

List the /etc/passwd 
haley:x:2900:2900::/home/haley:/bin/bash
saturn:x:2800:2800::/home/saturn:/bin/bash

List the /etc/group 
comets:x:1001:haley
planets:x:1002:saturn

