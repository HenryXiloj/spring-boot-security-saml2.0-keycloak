# 🔐 Spring Boot SAML 2.0 SSO with Keycloak 18.0.1

This project demonstrates how to implement **Single Sign-On (SSO)** using the **SAML 2.0 protocol** with **Spring Boot** as the service provider (SP) and **Keycloak 18.0.1** as the identity provider (IdP).

🔗 [Read the Full Guide on jarmx.blogspot.com »](https://jarmx.blogspot.com/2022/09/single-sign-on-with-saml-20-spring-boot.html)

---

## 🚀 Quick Start

### 1. Clone the Repository

```bash
git clone https://github.com/HenryXiloj/spring-boot-security-saml2.0-keycloak.git
cd spring-boot-security-saml2.0-keycloak
```

### 2. Start Keycloak (IdP)

**Option A: Docker CLI**

```bash
docker run -p 8080:8080 \
  -e KEYCLOAK_ADMIN=admin \
  -e KEYCLOAK_ADMIN_PASSWORD=admin \
  quay.io/keycloak/keycloak:18.0.1 start-dev
```

**Option B: Docker Compose**

```bash
docker-compose -f docker-compose-keycloak18.yml up -d
```

### 3. Run the Spring Boot Application

```bash
mvn spring-boot:run
```

Access the app at: [http://localhost:8081](http://localhost:8081)

---

## 🔧 Keycloak Configuration Summary

> You only need to configure this once. Full instructions with screenshots are in the [blog post](https://jarmx.blogspot.com/2022/09/single-sign-on-with-saml-20-spring-boot.html).

1. Go to [http://localhost:8080](http://localhost:8080)
   Login with:

   * **Username**: `admin`
   * **Password**: `admin`

2. Create Realm: `IDP_REALM`

3. Add Client:

   * ID: `spring-boot-keycloak`
   * Protocol: `saml`
   * Root URL: `http://localhost:8081`
   * Valid Redirect URIs: `/saml/*`
   * Assertion Consumer URL: `/saml/SSO`
   * Logout URL: `/saml/logout`

4. Export and replace the `keystore.jks` in `src/main/resources/saml/`

5. Create test user:

   * **Username**: `user1`
   * **Password**: `user1`

---

## 🔪 Test the Application

* Open: [http://localhost:8081](http://localhost:8081)
* Click **Login**
* Authenticate via Keycloak as `user1`
* Redirects back to Spring Boot app

---

## 📂 Project Structure

```
src/
├── java/com/henry/...    → Controllers, config, auth
└── resources/
    ├── saml/              → keystore.jks
    ├── templates/         → Thymeleaf views
    └── application.yml    → App config
```

---

## 🛠 Key Features

* 🔐 Spring Security + SAML 2.0 integration
* 🗺️ Keycloak 18 as a SAML Identity Provider
* ⚙️ Secure keystore and metadata management
* 🧾 Sample Thymeleaf pages
* 👨‍💻 Java 17 and Spring Boot 2.7.3

---

## 🔍 Useful URLs

* **Spring Boot App**: [http://localhost:8081](http://localhost:8081)
* **Keycloak Admin**: [http://localhost:8080](http://localhost:8080)
* **IdP SAML Metadata**: [http://localhost:8080/realms/IDP\_REALM/protocol/saml/descriptor](http://localhost:8080/realms/IDP_REALM/protocol/saml/descriptor)
* **SP Metadata**: [http://localhost:8081/saml/metadata](http://localhost:8081/saml/metadata)

---

## ❗ Troubleshooting

* 🔄 **Keycloak not starting?**
  Make sure port 8080 is free and Docker is running

* 🔐 **Keystore errors?**
  Confirm `keystore.jks` is valid and password is `store123`

* 💣 **Login issues?**
  Double-check SAML client settings and valid redirect URIs in Keycloak

---

## 📖 Read More

📘 Full tutorial with screenshots and explanations:
👉 [Single Sign-On with SAML 2.0, Spring Boot and Keycloak](https://jarmx.blogspot.com/2022/09/single-sign-on-with-saml-20-spring-boot.html)

📦 Source Code:
👉 [GitHub Repository](https://github.com/HenryXiloj/spring-boot-security-saml2.0-keycloak)


