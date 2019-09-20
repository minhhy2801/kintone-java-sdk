---
id: version-0.2.0-authentication
title: Authentication
sidebar_label: Authentication
original_id: authentication
---

Authentication module will be used by [Connection](./connection).
This module allow we authenticate with kintone app by password authenticator or API token authenticator. This module is also support basic authenticator.

!!! warning

    - If both the Token and Password Authentication are specified, the Token Authentication will be ignored and the Password authentication will be used.

## Constructor

**Parameter**

(none)

**Sample code**

<details class="tab-container" open>
<Summary>Init authentication module</Summary>

**Source code**

```java
Auth kintoneAuth = new Auth();
```

</details>

## Methods

### setPasswordAuth(username, password)

> Set password authentication for Authentication module.

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| username | String | yes | The username that is able to authenticate on kintone app
| password | String | yes | The password that is able to authenticate on kintone app

**Return**

[Auth](./authentication)

**Sample code**

<details class="tab-container" open>
<Summary>Set password authentication</Summary>

**Source code**

```java
String username = "cybozu";
String password = "cybozu";
kintoneAuth.setPasswordAuth(username, password);
```

</details>


### setApiToken(apiTokenString)

> Set Api Token for Authentication module.

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| apiToken | String | yes | The apiToken that is able to authenticate on kintone app

**Return**

[Auth](./authentication)


<details class="tab-container" open>
<Summary>Set APIToken authentication</Summary>

**Source code**

```java
String apiToken = "123456789abcdefghijklmnopqrstuvwxyz";
kintoneAuth.setApiToken(apiToken);
```

</details>


### setBasicAuth(username, password)

> Set Basic authentication for Authentication module.

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| username | String | yes | The username that is able to authenticate on kintone app
| password | String | yes | The password that is able to authenticate on kintone app

**Return**

[Auth](./authentication)

**Sample code**

<details class="tab-container" open>
<Summary>Set basic authentication</Summary>

**Source code**

```java
String username = "cybozu";
String password = "cybozu";
kintoneAuth.setBasicAuth(username, password);
```

</details>


### createHeaderCredentials()

> Provide the list of HTTP Headers which use to authentication in.

**Parameter**

(none)

**Return**

Array&lt;HTTPHeader&gt;

**Sample code**

<details class="tab-container" open>
<Summary>Provide the list of HTTP Headers which use to authentication in</Summary>

**Source code**

```java
for (HTTPHeader header : kintoneAuth.createHeaderCredentials()) {
	connection.setRequestProperty(header.getKey(), header.getValue());
}
```

</details>

### setClientCert(cert, password)

Set certificate by certificate data

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| cert | InputStream | yes | Data read from certificate file received from kintone
| password | String | yes | The password from kintone to decode the cert file

**Return**

[Auth](./authentication)

**Sample code**

<details class="tab-container" open>
<Summary>Set certificate by certificate data</Summary>

**Source code**

```java
Auth certAuth = new Auth();
certAuth.setPasswordAuth("YOUR_KINTONE_ID", "YOUR_KINTONE_PASSWORD");
String certPassword = "YOUR_CERT_PASSWORD"
String certPath = "YOUR_CERT_PATH"
InputStream cert = new FileInputStream(certPath);
auth.setClientCert(cert, certPassword)
Connection connection = new Connection("YOUR_DOMAIN", certAuth, -1);
```

</details>

### setClientCertByPath(filePath, password)

Set certificate by path

**Parameter**

| Name| Type| Required| Description |
| --- | --- | --- | --- |
| filePath | String | yes | Path to kintone certificate file
| password | String | yes | The password from kintone to decode the cert file

**Return**

[Auth](./authentication)

**Sample code**

<details class="tab-container" open>
<Summary>Set certificate by path</Summary>

**Source code**

```java
Auth certauth = new Auth();
certAuth.setPasswordAuth("YOUR_KINTONE_ID", "YOUR_KINTONE_PASSWORD");
String certPassword = "YOUR_CERT_PASSWORD"
String certPath = "YOUR_CERT_PATH"
certauth.setClientCertByPath(certPath, certPassword);
Connection connection = new Connection("YOUR_DOMAIN", certAuth);
```

</details>
