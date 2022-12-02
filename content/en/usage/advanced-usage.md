---
title: Advanced Usage
weight: 3
---

{{< toc >}}


{{< hint type=tip >}}
Can reference `http` api, current resource `ownerReference`, other resource from current `k8s cluster` as value for override and validate.
{{< /hint >}}

# OverridePolicy

# ClusterValidatePolicy

## PodAvailableBadge

PodAvailableBadge (PAB) provides a strategy to protect service can run in a limited size in any time to make sure service stability.

### Standard Workload

```yaml
apiVersion: policy.kcloudlabs.io/v1alpha1
kind: ClusterValidatePolicy
metadata:
  name: test-delete-protection
  labels:
    kinitiras.kcloudlabs.io/webhook: enabled
spec:
  resourceSelectors:
    - apiVersion: v1
      kind: Pod # match all Pod | can add label to test in part of Pods
  validateRules:
    - targetOperations:
        - DELETE
      template:
        type: pab
        podAvailableBadge:
          # minAvailable: 40%
          # maxUnavailable and minAvailable are mutually exclusive, maxUnavailable is priority to take effect.
          maxUnavailable: 60%
```
### Special Workload

In most case, no need to set replica reference since webhook will try to get replica from
current pod owner reference `spec.replica` and `status.replica`.
Only when pod running with custom workload or no k8s workload then set replica reference.

**Here is an example for all customized workload.**

```yaml
apiVersion: policy.kcloudlabs.io/v1alpha1
kind: ClusterValidatePolicy
metadata:
  name: test-delete-ns
  labels:
    kinitiras.kcloudlabs.io/webhook: enabled
spec:
  resourceSelectors:
    - apiVersion: v1
      kind: Pod # match all Pod | can add label to test in part of Pods
      labelSelector:
        matchLabels:
          controller: bromo
  validateRules:
    - targetOperations:
        - DELETE
      template:
        type: pab
        podAvailableBadge:
          maxUnavailable: 50%
          replicaReference:
            from: k8s
            currentReplicaPath: "/status/replica"
            targetReplicaPath: "/spec/replica"
            k8s:
              apiVersion: apps.xxx.io/v1
              kind: MyWorkload
              namespace: "{{metadata.namespace}}"
              name: "{{metadata.annotation.workload-name}}"
```

### No Workload

**Here is an example for no workload.**

```yaml
apiVersion: policy.kcloudlabs.io/v1alpha1
kind: ClusterValidatePolicy
metadata:
  name: test-delete-ns
  labels:
    kinitiras.kcloudlabs.io/webhook: enabled
spec:
  resourceSelectors:
    - apiVersion: v1
      kind: Pod # match all Pod | can add label to test in part of Pods
      labelSelector:
        matchLabels:
          controller: bromo
  validateRules:
    - targetOperations:
        - DELETE
      template:
        type: pab
        podAvailableBadge:
          maxUnavailable: 50%
          replicaReference:
            from: http
            currentReplicaPath: "body.result.deployment.running_task_count"
            targetReplicaPath: "body.result.deployment.target_task_count"
            http:
              url: "http://0.0.0.0:8081/api/deployment/{{metadata.annotations.deployment_id}}"
              method: GET
              params:
                cluster: "{{metadata.annotations.cluster_name}}"
              auth:
                authUrl: "http://xxxx"
                username: xxx
                password: xxx
```
