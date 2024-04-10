# maven-parent-kotlin-base

A common maven parent for usage in kotlin library or application projects. 

[![stable](https://img.shields.io/badge/lifecycle-STABLE-green.svg)](https://github.com/holisticon#open-source-lifecycle)
[![Build Status](https://github.com/toolisticon/maven-parent-kotlin-base/workflows/Development%20branches/badge.svg)](https://github.com/toolisticon/maven-parent-kotlin-base/actions)
[![sponsored](https://img.shields.io/badge/sponsoredBy-Holisticon-RED.svg)](https://holisticon.de/)
[![Maven Central](https://maven-badges.herokuapp.com/maven-central/io.toolisticon.maven.parent/maven-parent-kotlin-base/badge.svg)](https://maven-badges.herokuapp.com/maven-central/io.toolisticon.maven.parent/maven-parent-kotlin-base)

## About

Maven poms are quite bloated, Most of the settings (how to compile, how to deploy) are repeated over and over.
This maven-parent aims to reduce the xml in your `pom.xml` to the things you really want to express in your library or application project.

By nature of this module, it is a highly opinionated approach. It might fit your needs, but it is explicitly designed to support open source library 
projects we are currently building and maintaining under `toolisticon`, `holunda-io` and `holixon`.

### Versioning

Since this parent countless versions of other libs and plugins, it cannot have any meaningful version itself.

The semantic versioning conventions is `YEAR.MONTH.COUNT`, so the first build in September would be `version=2023.9.0` ... and counting.

## How to use?

This is a maven parent. So just include it on the top of your root `pom.xml`:

```xml
 <parent>
  <groupId>io.toolisticon.maven.parent</groupId>
  <artifactId>maven-parent-kotlin-base</artifactId>
  <version>LATEST_VERSION</version>
  <relativePath/>
</parent>
```

Carefully analyse your pom (and the effective pom) and remove duplications, unintended overwrites and possible conflicts ... and you are done. 

## Features

### Kotlin only compilation

Following the [x-compile guide](https://kotlinlang.org/docs/maven.html#compile-kotlin-and-java-sources) for maven/kotlin the correct kotlin and java compilers
are included.

## Versions

### Language

| Type                  | Version | Info                                     | 
|-----------------------|---------|------------------------------------------|
| kotlin                | 1.9.23  | used in kotlin compiler und kotlin libs. |
| java                  | 17      | compile target                           |
| kotlinx-serialization | 1.6.0   | compiler plugin                          |
| kotlin-logging        | 3.0.5   | logging support                          |

## Libs

| Lib    | Version  | Info                         |
|--------|----------|------------------------------|
| junit5 | 5.10.2   | bom dependency, unit testing |

## Plugins

see [official plugins](https://maven.apache.org/plugins/index.html)

| Plugin                                                                                                                       | Version | Info                                        |
|------------------------------------------------------------------------------------------------------------------------------|---------|---------------------------------------------|
| [maven-compiler](https://maven.apache.org/plugins/maven-compiler-plugin/)                                                    | 3.13.0  | disabling java compiler for kotlin projects |
| [maven-javadoc](https://maven.apache.org/plugins/maven-javadoc-plugin/)                                                      | 3.6.3   | include javadoc                             |
| [dokka](https://kotlinlang.org/docs/dokka-maven.html#apply-dokka)                                                            | 1.9.20  | use dokka for javadoc                       |
| [avro-maven](https://avro.apache.org/docs/1.11.1/getting-started-java/)                                                      | 1.11.3  | avro code generation                        |
| [maven-clean](https://maven.apache.org/plugins/maven-clean-plugin/)                                                          | 3.3.2   | clean project                               |
| [maven-dependency](https://maven.apache.org/plugins/maven-dependency-plugin/)                                                | 3.6.1   | check/update dependency versions            |
| [maven-deploy](https://maven.apache.org/plugins/maven-deploy-plugin/)                                                        | 3.1.1   | -                                           |
| [maven-enforcer](https://maven.apache.org/enforcer/maven-enforcer-plugin/)                                                   | 3.4.1   | enforce project setup                       |
| [maven-failsafe](https://maven.apache.org/surefire/maven-failsafe-plugin/)                                                   | 3.2.5   | testing                                     |
| [maven-gpg](https://maven.apache.org/plugins/maven-gpg-plugin/)                                                              | 3.2.1   | sign artifacts for release                  |
| [maven-install](https://maven.apache.org/plugins/maven-install-plugin/)                                                      | 3.1.1   | -                                           |
| [maven-jar-plugin](https://maven.apache.org/plugins/maven-jar-plugin/)                                                       | 3.3.0   | -                                           |
| [maven-resources](https://maven.apache.org/plugins/maven-resources-plugin/)                                                  | 3.3.1   | filter resources                            |
| [maven-surefire](https://maven.apache.org/surefire/maven-surefire-plugin/)                                                   | 3.2.5   | testing                                     |
| [build-helper](https://www.mojohaus.org/build-helper-maven-plugin/)                                                          | 3.5.0   | define source directories                   |
| [gitflow-maven](https://aleksandr-m.github.io/gitflow-maven-plugin/)                                                         | 1.21.0  | gitflow relase master/develop/release       |
| [jacoco-maven](https://www.eclemma.org/jacoco/trunk/doc/maven.html)                                                          | 0.8.11  | test reports                                |
| [jgiven-maven](https://jgiven.org/userguide/#_maven)                                                                         | 1.3.1   | jgiven test reports                         |
| [openapi-generator](https://github.com/OpenAPITools/openapi-generator/tree/master/modules/openapi-generator-maven-plugin)    | 7.4.0   | openapi/swagger code generation             |
| [properties-maven](https://www.mojohaus.org/properties-maven-plugin/)                                                        | 1.2.1   | generate build properties for project       |
| [versions-maven](https://www.mojohaus.org/versions/versions-maven-plugin/index.html)                                         | 2.16.2  | modify versions of project                  |
| [nexus-staging-maven](https://github.com/sonatype/nexus-maven-plugins/blob/main/staging/maven-plugin/README.md)              | 1.6.13  | release on maven central                    |


## Release a new version

1. close milestone in GitHub
1. on local console: `mvn release:start` - wait for action
1. on local console: `mvn release:finish` - wait for action - sonatype pipeline will run
1. publish a release on GitHub (prepared version is in drafts)
