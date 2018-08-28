# Artifactory Resource

Deploys and retrieves artifacts from a JFrog Artifactory server for a Concourse pipeline.

## Setup Docker

1. Generate keys
```
   $> cd docker
   $> ./generate-keys.sh
```

2. Run docker compose
```
  $> docker-compose -f docker-compose-artifactory.yml start
  Starting artifactory      ... done
  Starting concourse-db     ... done
  Starting concourse-web    ... done
  Starting concourse-worker ... done
```

3. Access Concourse and Artifactory
  * Artifactory:  http://localhost:8001/artifactory/webapp
    - Creds: admin / password
  * Concourse:    http://localhost:8080

4. Deploy the pipeline(s)
  * __pipeline-pivotal-resource__
    - This pipeline uses [pivotalservices/artifactory-resource](https://github.com/pivotalservices/artifactory-resource)
  * __pipeline-springio-resource__
    - This pipeline uses [spring-io/artifactory-resource](https://github.com/spring-io/artifactory-resource)




## Credits / References

*  https://github.com/pivotalservices/concourse-pipeline-samples/tree/master/pipelines/jfrog/artifactory-integration
