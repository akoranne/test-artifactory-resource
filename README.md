# Test Artifactory Resource

Deploys and retrieves artifacts from a JFrog Artifactory server for a Concourse pipeline.

1. Generate keys for docker compose
```
   $> cd docker
   $> ./generate-keys.sh
```

2. Run docker compose
```
  $> docker-compose -f docker-compose-artifactory.yml up
  Starting artifactory      ... done
  Starting concourse-db     ... done
  Starting concourse-web    ... done
  Starting concourse-worker ... done
```

3. Access Concourse and Artifactory
    * Artifactory:  http://localhost:8001/artifactory/webapp
      - Creds: admin / password
    * Concourse:    http://localhost:8080
		- Creds: test / test

4. Deploy the pipeline(s)
    * __pipeline-pivotal-resource__
      - This pipeline uses [pivotalservices/artifactory-resource](https://github.com/pivotalservices/artifactory-resource)
    * __pipeline-springio-resource__
      - This pipeline uses [spring-io/artifactory-resource](https://github.com/spring-io/artifactory-resource)

## Using SpringIO Artifactory Resource

#### The `put` task
* The input folder on the `put` task (e.g. "build") must match the output of the `build-file` task.
* If using standard file layout in Artifactory
  - The 'module_layout' must be set to "none", when using the regular file layout in Artifactory.
  - The `strip_snapshot_timestamps` must be false
* If using Maven folder structure under Artifactory
  - set the `module_layout` to `maven`
  - The `strip_snapshot_timestamps` must be true


## Credits / References

*  https://github.com/pivotalservices/concourse-pipeline-samples/tree/master/pipelines/jfrog/artifactory-integration
* https://github.com/spring-io/artifactory-resource
