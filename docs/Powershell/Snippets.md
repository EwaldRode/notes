## how to generate a new ssh key:
## how to generate a new ssh key:
```PowerShell
ssh-keygen -t rsa -b 4096 -C "insert.your@email-adress.here"
```

## keystore file

### how to list contents of keystore file
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

## how to decode base64 encoded strings with powershell
Condition: base64 encoded string: YmxhaGJsYWg=

```PowerShell
PS > [System.Text.Encoding]::UTF8.GetString([System.Convert]::FromBase64String("YmxhaGJsYWg="))
blahblah
```
