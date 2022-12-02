---
title: Welcome to the Kinitiras
geekdocNav: false
geekdocAlign: center
geekdocAnchor: false
resources:
- name: logo
  src: "kinitiras.png"
  title: ""
---

{{< img name="logo" size="small" lazy=false >}}

[![Build Status](https://github.com/k-cloud-labs/kinitiras/actions/workflows/ci.yml/badge.svg)](https://github.com/k-cloud-labs/kinitiras/actions?query=workflow%3Abuild)
[![codecov](https://codecov.io/gh/k-cloud-labs/kinitiras/branch/main/graph/badge.svg?token=74uYpOiawR)](https://codecov.io/gh/k-cloud-labs/kinitiras)
[![Go Report Card](https://goreportcard.com/badge/github.com/k-cloud-labs/kinitiras)](https://goreportcard.com/report/github.com/k-cloud-labs/kinitiras)
[![Go doc](https://img.shields.io/badge/go.dev-reference-brightgreen?logo=go&logoColor=white&style=flat)](https://pkg.go.dev/github.com/k-cloud-labs/kinitiras)


A **lightweight** but **powerful** and **programmable** rule engine for kubernetes admission webhook.

If you want to use it in clientside with client-go, please use [pidalio](https://github.com/k-cloud-labs/pidalio).


{{< button size="large" relref="usage/quick-start/" >}}Getting Started{{< /button >}}

## Feature overview

{{< columns >}}

### One webhook for all

You can customize your own mutate/validate policy to override/validate any resource in the Cluster instead of writing a new webhook.

<--->

### Validate any resources

Kinitiras support validate all kind of resource including user CRD, can select resource by setting resource GVK and labels.

<--->

### Override any resources

Kinitiras support override all kind of resource including user CRD, can select resource by setting resource GVK and labels.

{{< /columns >}}

{{< columns >}}

### Provide simple template

Kinitiras provides very simple template to make it easy to use, it takes only few field to validate or override resources fields.

<--->

### Support Cue

Kinitiras also support [cue](https://cuelang.org) which provides a powerful method to write complex rule for any situation.

<--->

### Support clientside

Kinitiras also provides clientside package, click [here](https://github.com/k-cloud-labs/pidalio) to learn more.

{{< /columns >}}

<br>
<br>
<br>

> A **lightweight** but **powerful** and **programmable** rule engine for kubernetes admission webhook.