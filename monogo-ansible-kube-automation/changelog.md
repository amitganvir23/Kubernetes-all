# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/en/1.0.0/)
and this project adheres to [Semantic Versioning](http://semver.org/spec/v2.0.0.html).

## [0.0.1]
- Feature teams environments added
- affinity Fixes added for feature teams
- Kong http2 enabled for pre-prod cluster but not for non-prod

## [branch-vault-fix Date:24/Apr/2018]
- Affinity in couchbase/Kafka/Zookeeper
- Play to delete deploy/svc for kong and MS
- Resource Decrease for MS
- Comment the deploymnet for loginuimongo
- Remove part to create ELB for kong service (Replace it by creating kong api gtw ingress)
