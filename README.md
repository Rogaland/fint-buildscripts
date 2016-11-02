# Common buildscripts

Common build scripts that can be used in module by using `apply from: <url to buildscript>`

## xsd.gradle

`apply from: 'https://raw.githubusercontent.com/FINTprosjektet/fint-buildscripts/master/xsd.gradle'`

| Task | Description |
|------|-------------|
| downloadXsd | Download xsd files. The list of xsd files should be defined in project build.gradle with `project.ext { xsdUrls = [...]  }` |
| xjc | Generates code from the downloaded xsd files |

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
