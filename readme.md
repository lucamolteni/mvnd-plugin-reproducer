The bootstrap module is a simple maven plugin that generates a class in generated-sources

The startup module uses this plugin and print the constant generated in the class

This fails with `mvnd clean install` but runs with `mvn clean install`

```
mvn clean install
java -cp startup/target/java -cp startup/target/startup-1.0.0-SNAPSHOT.jar org.reproducer.MainClass```
```

By removing this section in startup module

<!-- the following is used to provide a SLF4j binding to the ValidationBootstrapMain and related CP. Set src/test/resources/logback.xml root to DEBUG for debugging -->
<includePluginDependencies>true</includePluginDependencies>
<additionalClasspathElements>
<additionalClasspathElement>${project.basedir}/src/test/resources/</additionalClasspathElement>
</additionalClasspathElements>

Mvnd compiles
