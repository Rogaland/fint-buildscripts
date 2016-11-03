# Common buildscripts

Common build scripts that can be used in module by using `apply from: <url to buildscript>`

## xsd.gradle

`apply from: 'https://raw.githubusercontent.com/FINTprosjektet/fint-buildscripts/master/xsd.gradle'`  

Requires a `jaxb-bindings.xml` file in root of the project  
The xsd-files are downloaded to `src/main/resources/schema`  
The generated code is stored in `src/main/java`  

| Task | Description |
|------|-------------|
| downloadXsd | Download xsd files. The list of xsd files should be defined in project build.gradle with `project.ext { xsdUrls = [...]  }` |
| processXsd | Generates code from the downloaded xsd files |

Plugin: https://github.com/dmak/jaxb-xew-plugin

## bintray.gradle

```
plugins {
    id "com.jfrog.bintray" version "1.7"
}
...
if (project.hasProperty('bintrayUser') && project.hasProperty('bintrayKey')) {
    apply from: 'https://raw.githubusercontent.com/FINTprosjektet/fint-buildscripts/master/bintray.gradle'
}
```

| Task | Description |
|------|-------------|
| bintrayUpload | Upload artifact to bintray:<br>`./gradlew bintrayUpload -PbintrayUser=<username> -PbintrayKey=<apiKey>` |

## schemagen.gradle

`apply from: 'https://raw.githubusercontent.com/FINTprosjektet/fint-buildscripts/master/schemagen.gradle'`

| Task | Description |
|------|-------------|
| schemagen | Generate xsd file from Java class. The xsd name used for the generated file and the model directory should be defined in project build.gradle:<br> `project.ext { schemagenXsd = '...xsd' schemagenModelDir = 'src/main/java'}` |
