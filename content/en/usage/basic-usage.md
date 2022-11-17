---
title: Basic Usage
weight: 1
---

{{< toc >}}


# OverridePolicy

{{< hint type=note >}}
OverridePolicy and ClusterOverridePolicy are only different by sphere of influence, no other difference.
{{< /hint >}}

## PlainText

> wip

## Cue

> wip

## Template

### Annotations

```yaml
kind: OverridePolicy
apiVersion: policy.kcloudlabs.io/v1alpha1
metadata:
  name: add-anno-op-plaintext
  namespace: default
  labels:
    kinitiras.kcloudlabs.io/webhook: enabled
spec:
  resourceSelectors:
    # match Pod with below label
    - apiVersion: v1
      kind: Pod
      labelSelector:
        matchLabels:
          kinitiras.kcloudlabs.io/webhook: enabled
  overrideRules:
    # rule-1
    - targetOperations: # affect when pod create and update any times
        - UPDATE
        - CREATE
      overriders:
        template:
          # remove /metadata/annotations/xxxi-d from current object if exist.
          type: annotations # operate annotations
          operation: remove
          path: "xxx-id" # no need provide whole path only need key of annotations
    - targetOperations:
        - UPDATE
      overriders:
        template:
          type: annotations
          operation: replace
          path: "owned-by" # replace (delete & add) `owned-by:cue` to annotations
          value:
            string: "cue"
    - targetOperations:
        - UPDATE
      overriders:
        template:
          # replace key1:value2 and key2:value2 to annotations when pod update
          type: annotations
          operation: replace
          value:
            stringMap:
              key1: value1
              key2: value2
```

### Labels

```yaml
kind: OverridePolicy
apiVersion: policy.kcloudlabs.io/v1alpha1
metadata:
  name: add-labels-op-plaintext
  namespace: default
  labels:
    kinitiras.kcloudlabs.io/webhook: enabled
spec:
  resourceSelectors:
    - apiVersion: v1
      kind: Pod
      labelSelector:
        matchLabels:
          kinitiras.kcloudlabs.io/webhook: enabled
  overrideRules:
    - targetOperations:
        - UPDATE
      overriders:
        template:
          type: labels
          operation: remove
          path: "xxx-id"
    - targetOperations:
        - UPDATE
      overriders:
        template:
          type: labels
          operation: replace
          path: "owned-by"
          value:
            string: "cue"
```

### Resources

```yaml
kind: OverridePolicy
apiVersion: policy.kcloudlabs.io/v1alpha1
metadata:
  name: add-resource-op-plaintext
  namespace: default
  labels:
    kinitiras.kcloudlabs.io/webhook: enabled
spec:
  resourceSelectors:
    # matches Deployment contains below label
    - apiVersion: apps/v1
      kind: Deployment
      labelSelector:
        matchLabels:
          kinitiras.kcloudlabs.io/webhook: enabled
  overrideRules:
    - targetOperations:
        - CREATE
        - UPDATE
      overriders:
        template:
          type: resources
          operation: replace
          # replace (add if not exist) resource limitation to 100c and 4Ti memory
          resources:
            limits:
              cpu: 100
              memory: 4096Gi # support all format of memory
    - targetOperations:
        - CREATE
        - UPDATE
      overriders:
        template:
          type: resources
          operation: remove
          # delete resource request from deployment
          # only remove cpu and memory field
          resources:
            requests:
              cpu: 0 # zero just a placeholder here
              memory: 0
              ephemeral-storage: 0
```

### ResourceOversell

```yaml
kind: OverridePolicy
apiVersion: policy.kcloudlabs.io/v1alpha1
metadata:
  name: add-oversell-op-plaintext
  namespace: default
  labels:
    kinitiras.kcloudlabs.io/webhook: enabled
spec:
  resourceSelectors:
    # matches Deployment with below label
    - apiVersion: apps/v1
      kind: Deployment
      labelSelector:
        matchLabels:
          kinitiras.kcloudlabs.io/webhook: enabled
  overrideRules:
    - targetOperations:
        - CREATE
        - UPDATE
      overriders:
        template:
          type: resourcesOversell
          operation: replace # set remove to reset oversell
          resourcesOversell:
            cpuFactor: "0.5" # use half of limit / set 0 as placeholder when it needed remove
            memoryFactor: "0.2" # use 1/5 of limit
            diskFactor: "0.1" # use 1/10 of limit
```

### Tolerations

```yaml
kind: OverridePolicy
apiVersion: policy.kcloudlabs.io/v1alpha1
metadata:
  name: add-tolerations-op-plaintext
  namespace: default
  labels:
    kinitiras.kcloudlabs.io/webhook: enabled
spec:
  resourceSelectors:
    # match Pod with below label
    - apiVersion: v1
      kind: Pod
      labelSelector:
        matchLabels:
          kinitiras.kcloudlabs.io/webhook: enabled
  overrideRules:
    - targetOperations:
        - CREATE
        - UPDATE
      overriders:
        template:
          type: tolerations
          operation: replace # replace(add if key not exist)
          tolerations:
          - effect: NoExecute
            key: node.kubernetes.io/no-cpu # match with this key when replace or remove
            operator: Exists
            tolerationSeconds: 500
          - effect: NoExecute
            key: node.kubernetes.io/no-xxx
            operator: Exists
            tolerationSeconds: 500
```

### Affinity

```yaml
kind: OverridePolicy
apiVersion: policy.kcloudlabs.io/v1alpha1
metadata:
  name: add-affinity-op-plaintext
  namespace: default
  labels:
    kinitiras.kcloudlabs.io/webhook: enabled
spec:
  resourceSelectors:
    # match Pod with below label
    - apiVersion: v1
      kind: Pod
      labelSelector:
        matchLabels:
          kinitiras.kcloudlabs.io/webhook: enabled
  overrideRules:
    - targetOperations:
        - CREATE
      overriders:
        template:
          type: affinity
          operation: add
          affinity:
            nodeAffinity:
              preferredDuringSchedulingIgnoredDuringExecution:
                - preference:
                    matchExpressions:
                      - key: prefer
                        operator: In
                        values:
                          - zzc
                  weight: 2
              requiredDuringSchedulingIgnoredDuringExecution:
                nodeSelectorTerms:
                  - matchExpressions:
                      - key: required
                        operator: In
                        values:
                          - zzc
    - targetOperations:
        - CREATE
        - UPDATE
      overriders:
        template:
          type: affinity
          operation: add
          affinity:
            nodeAffinity:
              preferredDuringSchedulingIgnoredDuringExecution:
                - preference:
                    matchFields:
                      - key: bromo
                        operator: In
                        values:
                          - abcd
                  weight: 100
              requiredDuringSchedulingIgnoredDuringExecution:
                nodeSelectorTerms:
                  - matchExpressions:
                      - key: bromo
                        operator: In
                        values:
                          - abc
            podAffinity:
              # replace the preferredDuringSchedulingIgnoredDuringExecution if the field is empty
              # and add as a new element if it's not
              preferredDuringSchedulingIgnoredDuringExecution:
                - podAffinityTerm:
                    labelSelector:
                      matchExpressions:
                        - key: bromo_deployment
                          operator: In
                          values:
                            - "221019111032552325"
                        - key: bromo_service
                          operator: In
                          values:
                            - szdevops-yushan-test-sg
                    topologyKey: kubernetes.io/hostname
                  weight: 100
            podAntiAffinity:
              # replace the preferredDuringSchedulingIgnoredDuringExecution if the field is empty
              # and add as a new element if it's not
              preferredDuringSchedulingIgnoredDuringExecution:
                - podAffinityTerm:
                    labelSelector:
                      matchExpressions:
                        - key: bromo_deployment
                          operator: In
                          values:
                            - "221019111032552325"
                        - key: bromo_service
                          operator: In
                          values:
                            - szdevops-yushan-test-sg
                    topologyKey: kubernetes.io/hostname
                  weight: 100
```


# ClusterValidatePolicy

## PlaintText

## Cue

## Template

### Condition

```yaml
apiVersion: policy.kcloudlabs.io/v1alpha1
kind: ClusterValidatePolicy
metadata:
  name: test-multi-validate
  labels:
    kinitiras.kcloudlabs.io/webhook: enabled
spec:
  resourceSelectors:
    - apiVersion: v1
      kind: Namespace
  validateRules:
    - targetOperations:
      - DELETE
      template:
        type: condition
        condition:
          cond: Exist
          message: "cannot delete this ns"
          dataRef:
            from: current
            path: "/metadata/annotations/no-delete"
    - targetOperations:
      - DELETE
      template:
        type: condition
        condition:
          cond: Equal
          message: "cannot delete this ns"
          dataRef:
            from: current
            path: "/metadata/annotations/owned-by"
          value: # reject when field value equals bormo
            string: "bromo"
    - targetOperations:
        - DELETE
      template:
        type: condition
        condition:
          cond: In
          message: "cannot delete this ns"
          value:
            stringSlice:
              - bromo
              - ecp
              - oam
              - leap
          dataRef:
            from: current
            path: "/metadata/annotations/owned-by"
```