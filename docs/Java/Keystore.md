### how to list contents of a keystore file
Precondition:
  working folder is path/to/java_jdk/bin
```PowerShell
keytool -list -v -keystore [keystore_file.jks] -storepass [keystore password]
```

### export ca from keystore file
Precondition:
  working folder is path/to/java_jdk/bin
```PowerShell
keytool -export -alias [ca_alias] -file [certificate.crt] -keystore [keystore_file.jks] -storepass [keystore password]
```

### import ca into keystore file
Precondition:
  working folder is path/to/java_jdk/bin
```PowerShell
keytool -import -trustcacerts -alias [ca_alias] -file [certificate.crt] -keystore [keystore_file.jks] -storepass [keystore password]
```

**Default cacerts password: “changeit”**