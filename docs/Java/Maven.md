### Update the version number of the project and all of its submodules
```bash
mvn versions:set 
```

### Use non default mvn settings file
```bash
mvn [command] --settings=path\to\special\settings.xml
```

### List all declared and transitive dependencies in tree form
```bash
mvn dependency:tree
```