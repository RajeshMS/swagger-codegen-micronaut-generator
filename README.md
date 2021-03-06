[![Build Status](https://travis-ci.org/franz-see/swagger-codegen-micronaut-generator.svg?branch=master)](https://travis-ci.org/franz-see/swagger-codegen-micronaut-generator) 
[![codecov](https://codecov.io/gh/franz-see/swagger-codegen-micronaut-generator/branch/master/graph/badge.svg)](https://codecov.io/gh/franz-see/swagger-codegen-micronaut-generator)
[![Download](https://api.bintray.com/packages/franz-see/maven-repo/swagger-codegen-micronaut-generator/images/download.svg) ](https://bintray.com/franz-see/maven-repo/swagger-codegen-micronaut-generator/_latestVersion)

# swagger-codegen-micronaut-generator
Template to Generate Micronaut-based server side java application from a swagger/openapi specification

# How to Use

First, Download the jars

```
# download swagger cli
curl -O https://repo1.maven.org/maven2/io/swagger/codegen/v3/swagger-codegen-cli/3.0.10/swagger-codegen-cli-3.0.10.jar

# download micronaut generator
curl -O https://dl.bintray.com/franz-see/maven-repo/ph/net/see/swagger-codegen-micronaut-generator/1.0.1/swagger-codegen-micronaut-generator-1.0.1.jar
```

Next, use both jars to generate a micronaut project based on your swagger.yaml

```
java -cp swagger-codegen-micronaut-generator-1.0.1.jar:swagger-codegen-cli-3.0.10.jar \
  io.swagger.codegen.v3.cli.SwaggerCodegen \
  generate \
  -l ph.net.see.swaggercodegenmicronautgenerator.MicronautCodegen \
  -i /path/to/your/swagger.yaml \
  -o /where/you/want/the/project/to/be/generated
``` 

This will read your swagger/openapi configuration `/path/to/your/swagger.yaml` and generate the project directory in `/where/you/want/the/project/to/be/generated`. 


The project it will generate will contain dtos for your API, config files, and the actual Api intefaces themselves. By default, these Api interfaces throw `UnsupportedOperationException`. 

The next step would be to implement those Api interfaces with your `@Controller` classes, and start implementing those methods with actual logic. 

# Appendix

 * This code base has currently been donated into swagger-codegen-generators. If it does get merged to that project, then you should be able to create a micronaut based java application diretly from core swagger libraries. https://github.com/swagger-api/swagger-codegen-generators/issues/429
