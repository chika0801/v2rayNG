# [v2rayNG](https://github.com/2dust/v2rayNG)

**Compile the APK file for v2rayNG using the latest commit code from Xray-core and the latest version of go in order to test some features.**

# Generate apk signing certificate with keytool

1. Download [**JDK Development Kit**](https://download.oracle.com/java/20/latest/jdk-20_windows-x64_bin.zip)

2. Unzip the file, right-click in the `\bin` folder, select Open in Terminal, and paste the command in the Command Prompt window.

```
keytool -genkey -v -keystore keystore.jks -alias chika -storepass lovelive -keypass lovelive -validity 365 -keyalg RSA -keysize 2048
```

Replace `-alias chika` `-storepass lovelive` `-keypass lovelive` `-validity 365` with your values

3. Upload the generated **keystore.jks** file to your VPS and paste the command in the SSH terminal

```
openssl base64 < keystore.jks | tr -d '\n' | tee keystore_base64.txt
```

4. After forking this repository, click `Settings` -> `Secrets and Variables` -> `Options` -> `New Repository Secret`.

5. Add the following new item, replacing it with your value

| Name | Secret |
| :--- | :--- |
| ALIAS | `chika` |
| KEYPASSWORD | `lovelive` |
| KEYSTOREPASSWORD | `lovelive` |
| SIGNINGKEYBASE64 | `Paste the contents of keystore_base64.txt` |
