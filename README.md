SPARK-ETL
---------


This repository contains several modules around ETL processes with a focus on
scalability and quality. It is based on various technologies among: 

- apache SPARK
- apache HIVE
- apache SOLR
- PostgreSQL


Building a release
------------------

This process is semi-automated. Follow these steps:

- Be sure to be on the branch ``dev``
- Be sure that every merge request are merged on the branch ``dev`` through gitlab or merge manually
- Merge the branch ``dev`` on the branch ``master``
- It is mandatory to create the release from the branch ``master``, so be on the branch ``master``
- Type this:

```shell
$ export MVN_GROUP_REPOSITORY=https://nexus.rsareth.dil.services/repository/rsareth-aphp-mvn
$ export MVN_RELEASE_REPOSITORY=https://nexus.rsareth.dil.services/repository/rsareth-aphp-mvn-release
$ export MVN_SNAPSHOT_REPOSITORY=https://nexus.rsareth.dil.services/repository/rsareth-aphp-mvn-snapshot
$ export NEXUS_USER=<NEXUS_USER>
$ export NEXUS_PASSWORD=<NEXUS_PASSWORD>
$ export CI_PROJECT_PATH=rsareth-aphp/data/spark-etl
$ export GIT_USER=<GIT_USER>
$ export GIT_PASSWORD=<GIT_PASSWORD>
$ ./build.sh --prepare-release
The current version is: 1.0.5-SNAPSHOT

Provide the release name
1.0.5
Provide the snapshot name
1.0.6
[...]
$
```

  At this moment, you should see a pipeline related to the new release.
- Now, you need to merge the branch ``master`` on the branch ``dev``. So type this:

```shell
$ git branch
[...]
* master
[...]
$ git checkout dev
$ git merge master
[...]
$ git push
```