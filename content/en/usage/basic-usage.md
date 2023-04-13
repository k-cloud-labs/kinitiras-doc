---
title: Basic Usage
weight: 2
---

{{< toc >}}

# ResourceSelector

Resource selector is providing two kind of way to select resource which should affected by current policy, here is how to set selector:


{{< tabs "override" >}}
{{< tab "ByName" >}}

### Filter by name

```yaml
spec:
  resourceSelectors:
    # match Deployment
    - apiVersion: v1
      kind: Deployment
      namespace: custom-ns
      name: deployment1
```

{{< /tab >}}
{{< tab "ByLabels" >}}

### Filter by labels

```yaml
spec:
  resourceSelectors:
    # match Pod with below label
    - apiVersion: v1
      kind: Pod
      labelSelector:
        matchLabels:
          kinitiras.kcloudlabs.io/webhook: enabled
#       also support expression   
#        matchExpressions:
#          - key: xx.xx.io/key
#            operator: Exists
```

{{< /tab >}}
{{< tab "ByFields" >}}

### Filter by fields

```yaml
spec:
  resourceSelectors:
    # match Pod with below field
    - apiVersion: v1
      kind: Pod
      fieldSelector:
        matchFields:
          metadata.annotations.a1: value1
#       also support expression   
#        matchExpressions:
#          - field: metadata.name
#            operator: In
#            values:
#            - abc
#            - def
```

{{< /tab >}}
{{< /tabs >}}


# OverridePolicy

{{< hint type=note >}}
`OverridePolicy` and `ClusterOverridePolicy` are only different by sphere of influence, no other differences.
{{< /hint >}}

---
{{< hint type=important >}}
 From here let us tell you how to write an override policy. There are three types of override policy expression, you can
 write simple `plainText` rule, or you can write `cue` policy if you familiar with `cuelang`, you can also use the template
 mode to make it easy and more powerful.
{{< /hint >}}

## PlainText

Only need to specify `path`, `op` and the value (if remove field then no need to provide value).

example:

```yaml
spec:
  overrideRules:
    - targetOperations:
        - CREATE
      overriders:
        plaintext:
          - path: /metadata/labels/added-by
            op: add
            value: op
```

## Cue

In cue sector, it requires you to how `cue` works and how to write a simple `cue` script. The bottom line is the cue script must
contain `array of patches` and the element of this array must be a standard patch like this:

```js
{
  op: "add|replace|remove"
  path: "/path/to/field"
  value: "only provide when op is add or replace" 
}
```

example:

```yaml
spec:
  overrideRules:
    - targetOperations:
        - CREATE
      overriders:
        cue: |-
          object: _ @tag(object)

          patches: [
            if object.metadata.annotations == _|_ { // cue support go style coding like this
              {
                op: "add"
                path: "/metadata/annotations"
                value: {}
              }
            },
            {
              op: "add"
              path: "/metadata/annotations/added-by"
              value: "cue"
            }
          ]
```

## Template

Template provides a series type of policy module to make the override policy easy to configure and use. Users only need to 
specify few fields and value(value support const value and reference value) and `kinitiras` will render template to cue to run 
in runtime.

### Annotations

This type is aiming to override object's annotations.

example:

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

This type is aiming to override object's labels.

example:

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

This type is aiming to override object's resource(only support deployment and pod now).

example:

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

This type is aiming change the request resource to oversell resources.

example:

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

This type is aiming to override object's tolerations.

example:

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

This type is aiming to override object's affinity.

example:

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
                      - key: test
                        operator: In
                        values:
                          - abcd
                  weight: 100
              requiredDuringSchedulingIgnoredDuringExecution:
                nodeSelectorTerms:
                  - matchExpressions:
                      - key: test
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
                        - key: test_deployment
                          operator: In
                          values:
                            - "221019111032552325"
                        - key: test_service
                          operator: In
                          values:
                            - test-service
                    topologyKey: kubernetes.io/hostname
                  weight: 100
            podAntiAffinity:
              # replace the preferredDuringSchedulingIgnoredDuringExecution if the field is empty
              # and add as a new element if it's not
              preferredDuringSchedulingIgnoredDuringExecution:
                - podAffinityTerm:
                    labelSelector:
                      matchExpressions:
                        - key: test_deployment
                          operator: In
                          values:
                            - "221019111032552325"
                        - key: test_service
                          operator: In
                          values:
                            - test-service
                    topologyKey: kubernetes.io/hostname
                  weight: 100
```

# ClusterValidatePolicy

{{< hint type=important >}}
From here let us tell you how to write an validate policy(currently there is only cluster level validate policy). 
There are two types of validate policy expression, you can write `cue` policy if you familiar with `cuelang`, 
you can also use the template mode to make it easy and more powerful.
{{< /hint >}}

## Cue

In cue sector, it requires you to how `cue` works and how to write a simple `cue` script. The bottom line is the cue script must
contain `validate` object like this:

```js
{
  validate: true | false 
}
```

It will reject current operation if value is `false`.


```yaml
spec:
  validateRules:
    - cue: |-
        object: _ @tag(object)

        reject: object.metadata.labels != null && object.metadata.labels["kinitiras.kcloudlabs.io/webhook"] == "enabled"

        validate: {
          if reject{
                  reason: "operation rejected"
          }
          if !reject{
                  reason: ""
          }
          valid: !reject
        }
      targetOperations:
        - DELETE
```

## Template

Template provides a way to specify the field need to be verified and the values if it needed. Users only need to
specify few fields and value(value support const value and reference value) and `kinitiras` will render template to cue to run
in runtime.

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
            string: "test"
    - targetOperations:
        - DELETE
      template:
        type: condition
        condition:
          cond: In
          message: "cannot delete this ns"
          value:
            stringSlice:
              - test
              - ecp
              - oam
              - leap
          dataRef:
            from: current
            path: "/metadata/annotations/owned-by"
```
