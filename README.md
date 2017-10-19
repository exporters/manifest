# Exporters

## Abstract
A lot of exporters for Prometheus are out there in the wild. We want to have a community driven approach of validating and approving exporters regarding various topics.
This specification will document all the moving parts that need to be taken into account for approval by this community.

## 1. Introduction

### 1.1 Purpose

### 1.2 Requirements

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in RFC 2119 [34].

An implementation is not compliant if it fails to satisfy one or more of the MUST or REQUIRED level requirements for the protocols it implements. An implementation that satisfies all the MUST or REQUIRED level and all the SHOULD level requirements for its protocols is said to be "unconditionally compliant"; one that satisfies all the MUST level requirements but not all the SHOULD level requirements for its protocols is said to be "conditionally compliant."

### 2.1 Development

* MUST follow the official [Writing Exporters](https://prometheus.io/docs/instrumenting/writing_exporters/) guide
* MUST allocate a free port in [Prometheus Wiki](https://github.com/prometheus/prometheus/wiki/Default-port-allocations)
* SHOULD use collector pattern if doing API calls in the background only
* SHOULD test as much as possible
* SHOULD use timeouts when communicating with other software via network
* SHOULD initialize with a useful zero value, e.g. counter set to `0`

### 2.2 Distribution

* MUST use SemVer for versions
* MUST release Binaries and Docker Images on Docker Hub (quay?)
* MUST contain example alerts and recording rules
* SHOULD use alpine or busybox whenever possible

### 3.1 Exporters written in Go

* MUST vendor all dependencies with [golang/dep](https://github.com/golang/dep)
* MUST be compliant to tools like: lint, fmt, vet
* SHOULD add a goreportcard badge to the README.md
