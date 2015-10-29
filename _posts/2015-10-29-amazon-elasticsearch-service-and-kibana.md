---
layout: post
title:  "Amazon's ElasticSearch Service and Kibana"
---

All the nice stuff is there — easy deployment, (relatively) easy ElasticSearch scaling, redundancy (multi-AZ), backups, etc. But this post is about the problems in the new service from AWS.

  - **Access control**: Current options are limited to AWS account or IP addresses. I would ideally like more fine grained control here. Kibana is essentially useless if it cannot be used from the browser. Ideally, something like access from a particular VPN or Security Group should be available.
  - **Logstash integration**: Thankfully I stumbled across https://github.com/awslabs/logstash-output-amazon_es. But, considering that getting an ELK stack running is the primary reason for coming to Amazon’s ElasticSearch service for many people — the logstash part should be documented much better.
