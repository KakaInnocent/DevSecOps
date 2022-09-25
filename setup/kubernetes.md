 kubernetes are containers run on pods. A pod is the smallest deployable unit within kubernetes in which you can run one or multiple containers
 For high availability you run multiple pods
 Make use of a replica set to define how many replicas of your instance you want to have.

 If you have multiple versions you can use a deployment to switch to the next version without downtime,

 Make sure you cat /root/.kube/config and add it as a management to Jenkins as a secret file
