# slurm

![Version: 0.1.0](https://img.shields.io/badge/Version-0.1.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 24.05](https://img.shields.io/badge/AppVersion-24.05-informational?style=flat-square)

Helm Chart for Slurm HPC Workload Manager

## Requirements

| Repository | Name | Version |
|------------|------|---------|
| oci://ghcr.io/slinkyproject/charts | slurm-exporter | ~0.1.0 |
| oci://registry-1.docker.io/bitnamicharts | mariadb | ~16.3 |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| accounting.affinity | object | `{}` |  Set affinity for Kubernetes Pod scheduling. Ref: https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node/#affinity-and-anti-affinity |
| accounting.enabled | bool | `true` |  Enables accounting services. |
| accounting.external.enabled | bool | `false` |  Use an external acounting instance (slurmdbd) instead of deploying one. |
| accounting.external.host | string | `""` |  The external acounting instance (slurmdbd) host. |
| accounting.external.port | integer | `6819` |  The external acounting instance (slurmdbd) port. |
| accounting.image.repository | string | `"ghcr.io/slinkyproject/slurmdbd"` |  Set the image repository to use. |
| accounting.image.tag | string | `"24.05-ubuntu-24.04"` |  Set the image tag to use. |
| accounting.imagePullPolicy | string | `"IfNotPresent"` |  Set the image pull policy. |
| accounting.replicas | integer | `1` |  Set the number of replicas to deploy. |
| accounting.resources | object | `{}` |  Set container resource requests and limits for Kubernetes Pod scheduling. Ref: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/#resource-requests-and-limits-of-pod-and-container |
| authcred.image.repository | string | `"ghcr.io/slinkyproject/sackd"` |  Set the image repository to use. |
| authcred.image.tag | string | `"24.05-ubuntu-24.04"` |  Set the image tag to use. |
| authcred.resources | object | `{}` |  Set container resource requests and limits for Kubernetes Pod scheduling. Ref: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/#resource-requests-and-limits-of-pod-and-container |
| compute.image.repository | string | `"ghcr.io/slinkyproject/slurmd"` |  Set the image repository to use. |
| compute.image.tag | string | The Release appVersion. |  Set the image tag to use. |
| compute.imagePullPolicy | string | `"IfNotPresent"` |  Set the image pull policy. |
| compute.nodesets | list | `[{"affinity":{},"enabled":true,"image":{"repository":"","tag":""},"imagePullPolicy":"IfNotPresent","minReadySeconds":0,"name":"debug","nodeFeatures":[],"nodeGres":"","nodeSelector":{"kubernetes.io/os":"linux"},"nodeWeight":1,"partition":{"config":"State=UP MaxTime=INFINITE","enabled":true},"persistentVolumeClaimRetentionPolicy":{"whenDeleted":"Retain"},"priorityClassName":"","replicas":1,"resources":{"limits":{"cpu":1,"memory":"1Gi"}},"updateStrategy":{"rollingUpdate":{"maxUnavailable":"20%","partition":0,"paused":false},"type":"RollingUpdate"},"volumeClaimTemplates":[]}]` |  Slurm NodeSets by object list. |
| compute.nodesets[0] | string | `{"affinity":{},"enabled":true,"image":{"repository":"","tag":""},"imagePullPolicy":"IfNotPresent","minReadySeconds":0,"name":"debug","nodeFeatures":[],"nodeGres":"","nodeSelector":{"kubernetes.io/os":"linux"},"nodeWeight":1,"partition":{"config":"State=UP MaxTime=INFINITE","enabled":true},"persistentVolumeClaimRetentionPolicy":{"whenDeleted":"Retain"},"priorityClassName":"","replicas":1,"resources":{"limits":{"cpu":1,"memory":"1Gi"}},"updateStrategy":{"rollingUpdate":{"maxUnavailable":"20%","partition":0,"paused":false},"type":"RollingUpdate"},"volumeClaimTemplates":[]}` |  Name of NodeSet. Must be unique. |
| compute.nodesets[0].affinity | object | `{}` |  Set affinity for Kubernetes Pod scheduling. |
| compute.nodesets[0].enabled | bool | `true` |  Enables the NodeSet in Slurm. |
| compute.nodesets[0].image.repository | string | `""` |  Set the image repository to use. |
| compute.nodesets[0].image.tag | string | `""` |  Set the image tag to use. |
| compute.nodesets[0].imagePullPolicy | string | `"IfNotPresent"` |  Set the image pull policy. |
| compute.nodesets[0].minReadySeconds | int | `0` |  The minimum number of seconds for which a newly created NodeSet Pod should be ready without any of its container crashing, for it to be considered available. |
| compute.nodesets[0].nodeFeatures | list | `[]` |  Set Slurm node Features as a list(string). Ref: https://slurm.schedmd.com/slurm.conf.html#OPT_Features |
| compute.nodesets[0].nodeGres | string | `""` |  Set Slurm node GRES. Ref: https://slurm.schedmd.com/slurm.conf.html#OPT_Gres_1 |
| compute.nodesets[0].nodeSelector | map | `{"kubernetes.io/os":"linux"}` |  Selector which must match a node's labels for the pod to be scheduled on that node. |
| compute.nodesets[0].nodeWeight | string | `1` |  Set Slurm node weight for Slurm scheduling. Ref: https://slurm.schedmd.com/slurm.conf.html#OPT_Weight |
| compute.nodesets[0].partition | object | `{"config":"State=UP MaxTime=INFINITE","enabled":true}` |  Partition describes the partition created specifically for this NodeSet to be added. |
| compute.nodesets[0].partition.config | string | `"State=UP MaxTime=INFINITE"` |  Extra Slurm partition configuration appended onto the partition line. Ref: https://slurm.schedmd.com/slurm.conf.html#lbAI |
| compute.nodesets[0].partition.enabled | bool | `true` |  Enables this NodeSet's partition line to be added in Slurm. |
| compute.nodesets[0].persistentVolumeClaimRetentionPolicy | object | `{"whenDeleted":"Retain"}` |  The policy used for PVCs created from the NodeSet VolumeClaimTemplates. |
| compute.nodesets[0].persistentVolumeClaimRetentionPolicy.whenDeleted | string | `"Retain"` |  WhenDeleted specifies what happens to PVCs created from NodeSet VolumeClaimTemplates when the NodeSet is deleted. The default policy of `Retain` causes PVCs to not be affected by NodeSet deletion. The `Delete` policy causes those PVCs to be deleted. |
| compute.nodesets[0].priorityClassName | string | `""` |  Set the priority class to use. Ref: https://kubernetes.io/docs/concepts/scheduling-eviction/pod-priority-preemption/#priorityclass |
| compute.nodesets[0].replicas | integer | `1` |  Set the number of replicas to deploy. NOTE: if empty, all nodes matching affinity will have a replica (like DaemonSet). |
| compute.nodesets[0].resources | object | `{"limits":{"cpu":1,"memory":"1Gi"}}` |  Set container resource requests and limits for Kubernetes Pod scheduling. Ref: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/#resource-requests-and-limits-of-pod-and-container |
| compute.nodesets[0].updateStrategy | object | `{"rollingUpdate":{"maxUnavailable":"20%","partition":0,"paused":false},"type":"RollingUpdate"}` |  Set the update strategy configuration. |
| compute.nodesets[0].updateStrategy.rollingUpdate | object | `{"maxUnavailable":"20%","partition":0,"paused":false}` |  Define the rolling update policy. Only used when "updateStrategy.type=RollingUpdate". |
| compute.nodesets[0].updateStrategy.rollingUpdate.maxUnavailable | string | `"20%"` |  The maximum number of pods that can be unavailable during the update. Value can be an absolute number (ex: 5) or a percentage of desired pods (ex: 10%). Absolute number is calculated from percentage by rounding up. This can not be 0. Defaults to 1. |
| compute.nodesets[0].updateStrategy.rollingUpdate.partition | int | `0` |  Partition indicates the number of NodeSet pods that should be not be updated to the latest version. |
| compute.nodesets[0].updateStrategy.rollingUpdate.paused | bool | `false` |  Pause will halt rollingUpdate while this value is true. |
| compute.nodesets[0].updateStrategy.type | string | `"RollingUpdate"` |  Set the update strategy type. Can be either: "RollingUpdate"; "OnDelete". |
| compute.nodesets[0].volumeClaimTemplates | list | `[]` |  List of claims that pods are allowed to reference. The NodeSet controller is responsible for mapping network identities to claims in a way that maintains the identity of a pod. |
| compute.partitions | list | `[{"config":"State=UP Default=YES MaxTime=INFINITE","enabled":true,"name":"all","nodesets":["ALL"]}]` |  Slurm Partitions by object list. |
| compute.partitions[0] | string | `{"config":"State=UP Default=YES MaxTime=INFINITE","enabled":true,"name":"all","nodesets":["ALL"]}` |  Name of Partition. Must be unique. |
| compute.partitions[0].config | string | `"State=UP Default=YES MaxTime=INFINITE"` |  Extra Slurm partition configuration appended onto the partition line. Ref: https://slurm.schedmd.com/slurm.conf.html#lbAI |
| compute.partitions[0].enabled | bool | `true` |  Enables the partition in Slurm. |
| compute.partitions[0].nodesets | list | `["ALL"]` |  NodeSets to put into this Partition by name/key. NOTE: 'ALL' is a Slurm meta value to mean all nodes in the system. |
| controller.affinity | object | `{}` |  Set affinity for Kubernetes Pod scheduling. Ref: https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node/#affinity-and-anti-affinity |
| controller.enabled | bool | `true` |  Enables the controller node. |
| controller.image.repository | string | `"ghcr.io/slinkyproject/slurmctld"` |  Set the image repository to use. |
| controller.image.tag | string | `"24.05-ubuntu-24.04"` |  Set the image tag to use. |
| controller.imagePullPolicy | string | `"IfNotPresent"` |  Set the image pull policy. |
| controller.persistence.accessModes | list | `["ReadWriteOnce"]` |  Create a `PersistentVolumeClaim` with these access modes. |
| controller.persistence.annotations | object | `{}` |  Create a `PersistentVolumeClaim` with these annotations. |
| controller.persistence.existingClaim | string | `""` |  Name of an existing `PersistentVolumeClaim` to use instead of creating one from definition. NOTE: When not empty, the other persistence fields will be ignored. |
| controller.persistence.labels | object | `{}` |  Create a `PersistentVolumeClaim` with these labels. |
| controller.persistence.selector | object | `{}` |  Selector to match an existing `PersistentVolume`. |
| controller.persistence.size | string | `"4Gi"` |  Create a `PersistentVolumeClaim` with this storage size. |
| controller.persistence.storageClass | string | `"standard"` |  Create a `PersistentVolumeClaim` with this storage class. |
| controller.priorityClassName | string | `nil` |  Set the priority class to use. Ref: https://kubernetes.io/docs/concepts/scheduling-eviction/pod-priority-preemption/#priorityclass |
| controller.replicas | integer | `1` |  Set the number of replicas to deploy. |
| controller.resources | object | `{}` |  Set container resource requests and limits for Kubernetes Pod scheduling. Ref: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/#resource-requests-and-limits-of-pod-and-container |
| fullnameOverride | string | `""` |  Overrides the full name of the release. |
| imagePullPolicy | string | `"IfNotPresent"` |  Set the image pull policy. |
| imagePullSecrets | list | `[]` |  Set the secrets for image pull. Ref: https://kubernetes.io/docs/tasks/configure-pod-container/pull-image-private-registry/ |
| jwt.hs256.existingSecret | string | `""` |  The existing secret to use otherwise one will be generated. |
| mariadb.affinity | object | `{}` |  |
| mariadb.auth.database | string | `"slurm_acct_db"` |  |
| mariadb.auth.existingSecret | string | `"slurm-mariadb-passwords"` |  |
| mariadb.auth.username | string | `"slurm"` |  |
| mariadb.enabled | bool | `true` |  |
| mariadb.initdbScripts."slurm-accounting.sql" | string | `"SET GLOBAL innodb_buffer_pool_size=(4 * 1024 * 1024 * 1024);\nSET GLOBAL innodb_log_file_size=(64 * 1024 * 1024);\nSET GLOBAL innodb_lock_wait_timeout=900;\nSET GLOBAL max_allowed_packet=(16 * 1024 * 1024);"` |  |
| mariadb.metrics.enabled | bool | `false` |  |
| mariadb.metrics.serviceMonitor.enabled | bool | `false` |  |
| mariadb.primary.persistence.accessModes[0] | string | `"ReadWriteOnce"` |  |
| mariadb.primary.persistence.annotations | object | `{}` |  |
| mariadb.primary.persistence.enabled | bool | `false` |  |
| mariadb.primary.persistence.existingClaim | string | `""` |  |
| mariadb.primary.persistence.labels | object | `{}` |  |
| mariadb.primary.persistence.selector | object | `{}` |  |
| mariadb.primary.persistence.size | string | `"8Gi"` |  |
| mariadb.primary.persistence.storageClass | string | `"standard"` |  |
| mariadb.primary.priorityClassName | string | `""` |  |
| mariadb.resources | object | `{}` |  |
| nameOverride | string | `""` |  Overrides the name of the release. |
| namespaceOverride | string | `""` |  Overrides the namespace of the release. |
| priorityClassName | string | `""` |  Set the priority class to use. Ref: https://kubernetes.io/docs/concepts/scheduling-eviction/pod-priority-preemption/#priorityclass |
| restapi.affinity | object | `{}` |  Set affinity for Kubernetes Pod scheduling. Ref: https://kubernetes.io/docs/concepts/scheduling-eviction/assign-pod-node/#affinity-and-anti-affinity |
| restapi.enabled | bool | `true` |  Enables restapi services. |
| restapi.image.repository | string | `"ghcr.io/slinkyproject/slurmrestd"` |  Set the image repository to use. |
| restapi.image.tag | string | `"24.05-ubuntu-24.04"` |  Set the image tag to use. |
| restapi.imagePullPolicy | string | `"IfNotPresent"` |  Set the image pull policy. |
| restapi.priorityClassName | string | `""` |  Set the priority class to use. Ref: https://kubernetes.io/docs/concepts/scheduling-eviction/pod-priority-preemption/#priorityclass |
| restapi.replicas | integer | `1` |  Set the number of replicas to deploy. |
| restapi.resources | object | `{}` |  Set container resource requests and limits for Kubernetes Pod scheduling. Ref: https://kubernetes.io/docs/concepts/configuration/manage-resources-containers/#resource-requests-and-limits-of-pod-and-container |
| slurm-exporter.exporter.enabled | bool | `true` |  |
| slurm-exporter.exporter.secretName | string | `"slurm-token-exporter"` |  |
| slurm.auth.existingSecret | string | `""` |  The existing secret to use otherwise one will be generated. |
| slurm.configFiles | map[string]string | `{}` |  Optional raw Slurm configuration files, as a map. The map key represents the config file by name; the map value represents config file contents as a string. Ref: https://slurm.schedmd.com/man_index.html#configuration_files |
| slurm.epilogScripts | map[string]string | `{}` |  The Epilog scripts for compute nodesets, as a map. The map key represents the filename; the map value represents the script contents. WARNING: The script must include a shebang (!) so it can be executed correctly by Slurm. Ref: https://slurm.schedmd.com/slurm.conf.html#OPT_Epilog Ref: https://slurm.schedmd.com/prolog_epilog.html Ref: https://en.wikipedia.org/wiki/Shebang_(Unix) |
| slurm.extraSlurmConf | string | `"SchedulerParameters=batch_sched_delay=20,bf_continue,bf_interval=300,bf_min_age_reserve=10800,bf_resolution=600,bf_yield_interval=1000000,partition_job_depth=500,sched_max_job_start=200,sched_min_interval=2000000\nDefMemPerCPU=1"` |  Extra slurm configuration lines to append to `slurm.conf`. WARNING: Values can override existing ones. Ref: https://slurm.schedmd.com/slurm.conf.html |
| slurm.extraSlurmdbdConf | string | `"CommitDelay=1"` |  Extra slurmdbd configuration lines to append to `slurmdbd.conf`. WARNING: Values can override existing ones. Ref: https://slurm.schedmd.com/slurmdbd.conf.html |
| slurm.prologScripts | map[string]string | `{}` |  The Prolog scripts for compute nodesets, as a map. The map key represents the filename; the map value represents the script contents. WARNING: The script must include a shebang (!) so it can be executed correctly by Slurm. Ref: https://slurm.schedmd.com/slurm.conf.html#OPT_Prolog Ref: https://slurm.schedmd.com/prolog_epilog.html Ref: https://en.wikipedia.org/wiki/Shebang_(Unix) |

