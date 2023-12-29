# [v2rayNG](https://github.com/2dust/v2rayNG)

**Compile the APK file for v2rayNG using the latest commit code from Xray-core and the latest version of go in order to test some features.**

# Generate apk signing certificate with keytool

1. Download [**JDK Development Kit**](https://www.oracle.com/java/technologies/downloads/).

2. Unzip the file, right-click in the `\bin` folder, select Open in Terminal, and paste the command in the Command Prompt window.

```
keytool -genkey -v -keystore keystore.jks -alias chika -storepass lovelive -keypass lovelive -validity 365 -keyalg RSA -keysize 2048
```

Replace `-alias chika` `-storepass lovelive` `-keypass lovelive` `-validity 365` with your values.

3. Upload the generated **keystore.jks** file to your VPS and paste the command in the SSH terminal.

```
openssl base64 < keystore.jks | tr -d '\n' | tee keystore_base64.txt
```

4. After forking this repository, click `Settings` -> `Secrets and Variables` -> `Options` -> `New Repository Secret`.

5. Add the following new item, replacing it with your value.

| Name | Secret |
| :--- | :--- |
| ALIAS | `chika` |
| KEYPASSWORD | `lovelive` |
| KEYSTOREPASSWORD | `lovelive` |
| SIGNINGKEYBASE64 | `Paste the contents of keystore_base64.txt` |

# 使用keytool生成apk签名证书

1. 下载 [**JDK Development Kit**](https://www.oracle.com/java/technologies/downloads/)。

2. 解压后在 `\bin` 文件夹中点击右键，选择在终端中打开，在命令提示符窗口中粘贴命令。

```
keytool -genkey -v -keystore keystore.jks -alias chika -storepass lovelive -keypass lovelive -validity 365 -keyalg RSA -keysize 2048
```

将 `-alias chika` `-storepass lovelive` `-keypass lovelive` `-validity 365` 替换成你的值。

3. 将生成的 **keystore.jks** 文件上传到你的VPS，在SSH终端中粘贴命令。

```
openssl base64 < keystore.jks | tr -d '\n' | tee keystore_base64.txt
```

4. Fork本仓库后，点击 `Settings` —> `Secrets and variables` —> `Actions` —> `New repository secret`。

5. 新增以下项目，替换成你的值。

| Name | Secret |
| :--- | :--- |
| ALIAS | `chika` |
| KEYPASSWORD | `lovelive` |
| KEYSTOREPASSWORD | `lovelive` |
| SIGNINGKEYBASE64 | `粘贴 keystore_base64.txt 中的内容` |
