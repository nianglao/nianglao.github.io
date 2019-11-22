---
title: "Golang UML Generator"
date: 2019-11-22 11:39:00 +0800
categories: tools
---

This post introduce how to use goplantuml and plantuml to generate UML graph.

# Prerequisites

## goplantuml

URL: https://github.com/jfeliu007/goplantuml

Install

```sh
go get github.com/jfeliu007/goplantuml/parser
go get github.com/jfeliu007/goplantuml/cmd/goplantuml
cd $GOPATH/src/github.com/jfeliu007/goplantuml
go install ./...
```

Ensure $GOPATH/bin is in $PATH.

## PlantUML

### Dependency

- Java
- Graphviz https://www.graphviz.org/download/
- PlantUML Jar http://plantuml.com/zh/download

Ensure java and graphviz-dot is in \$PATH

# Generate UML graph

## Step 1: Generate UML txt with goplantuml

```sh
goplantuml [-recursive] path/to/gofiles > uml_example.txt
```

This will generate PlantUML format UML texts.

## Step 2: Generate graph with PlantUML

```sh
java -jar plantuml.jar -tpng uml_example.txt
```

This will generate uml_example.png file.

# Generate large grapth

Refer http://plantuml.com/zh/faq

```
I want to generate huge diagrams!
PlantUML limits image width and height to 4096. There is a environment variable that you can set to override this limit: PLANTUML_LIMIT_SIZE. You have to define this variable before launching PlantUML, something like:


set PLANTUML_LIMIT_SIZE=8192
or


setenv PLANTUML_LIMIT_SIZE 8192
Another way is an option in the command line:


java -DPLANTUML_LIMIT_SIZE=8192 -jar /path/to/plantuml.jar ...
Note that if you generate very big diagrams, (for example, something like 20 000 x 10 000 pixels), you can have some memory issues. The solution is to add this parameter to the java vm : -Xmx1024m.
```
