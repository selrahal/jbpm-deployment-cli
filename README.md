# jBPM Deployments CLI

Some scripts to facilitate creating and removing process deployments in Red Hat JBoss BPM Suite 6.

## Requirements
1. Bash - These scripts are using your /bin/bash executable
2. cURL - These scripts are expected the 'curl' executable to be on your PATH

## Deploy a kjar

Usage:

```sh
[selrahal@localhost bin]$ ./deploy_kjar --help
Script used to create and perform HTTP POST to BPMS6 to deploy a deployment unit.
USAGE: deploy_kjar [OPTIONS]
        -u username [bpmsAdmin]
        -p password [abcd1234!]
        -h hostname [localhost]
        --port port [8080]
        -g group_id [org.kie.example]
        -a artifact_id [project1]
        -v version [1.0.0-SNAPSHOT]
        -k kbase []
        -s ksession []
        -r runtime_strategy []
        --protocol (http|https) [http]
```

Example:

```sh
[selrahal@localhost bin]$ ./deploy_kjar -g org.kie.example -a project1 -v 1.0.0-SNAPSHOT
```

```sh
<?xml version="1.0" encoding="UTF-8" standalone="yes"?><deployment-job-result><identifier>32</identifier><operation>DEPLOY</operation><deploymentUnit><groupId>org.kie.example</groupId><artifactId>project1</artifactId><version>1.0.0-SNAPSHOT</version><strategy>PER_PROCESS_INSTANCE</strategy><status>ACCEPTED</status></deploymentUnit><success>true</success><explanation>deploy job accepted.</explanation></deployment-job-result>
Deployed org.kie.example:project1:1.0.0-SNAPSHOT
```

## Undeploy a kjar

```sh
[selrahal@localhost bin]$ ./undeploy_kjar --help
Script used to create and perform HTTP POST to BPMS6 to undeploy a deployment unit.
USAGE: undeploy_kjar [OPTIONS]
        -u username [bpmsAdmin]
        -p password [abcd1234!]
        -h hostname [localhost]
        --port port [8080]
        -g group_id [org.kie.example]
        -a artifact_id [project1]
        -v version [1.0.0-SNAPSHOT]
        -k kbase []
        -s ksession []
        --protocol (http|https) [http]
```

Example:

```sh
[selrahal@localhost bin]$ ./undeploy_kjar -g org.kie.example -a project1 -v 1.0.0-SNAPSHOT
```

```sh
<?xml version="1.0" encoding="UTF-8" standalone="yes"?><deployment-job-result><identifier>33</identifier><operation>UNDEPLOY</operation><deploymentUnit><groupId>org.kie.example</groupId><artifactId>project1</artifactId><version>1.0.0-SNAPSHOT</version><strategy>PER_PROCESS_INSTANCE</strategy><status>ACCEPTED</status></deploymentUnit><success>true</success><explanation>undeploy job accepted.</explanation></deployment-job-result>
Uneployed org.kie.example:project1:1.0.0-SNAPSHOT
```
