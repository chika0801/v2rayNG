# v2rayNG

**Compile the APK file for v2rayNG using the latest commit code from Xray-core and the latest version of go in order to test some features.**

# 使用keytool生成apk签名证书

1. 下载 [**JDK Development Kit**](https://download.oracle.com/java/20/latest/jdk-20_windows-x64_bin.zip)

2. 解压后在 `\bin` 文件夹中点击右键，选择 `在终端中打开`，在 `命令提示符` 窗口中粘贴命令

```
keytool -genkey -v -keystore keystore.jks -alias chika -storepass lovelive -keypass lovelive -validity 365 -keyalg RSA -keysize 2048
```

将 `-alias chika` `-storepass lovelive` `-keypass lovelive` `-validity 365` 替换成你的值

3. 将生成的 **keystore.jks** 文件上传到你的VPS，在SSH终端中粘贴命令

```
openssl base64 < keystore.jks | tr -d '\n' | tee keystore_base64.txt
```

4. Fork本仓库后，点击 `Settings` —> `Secrets and variables` —> `Actions` —> `New repository secret`

5. 新增以下项目，替换成你的值

| Name | Secret |
| :--- | :--- |
| ALIAS | `chika` |
| KEYPASSWORD | `lovelive` |
| KEYSTOREPASSWORD | `lovelive` |
| SIGNINGKEYBASE64 | `粘贴 keystore_base64.txt 中的内容` |
