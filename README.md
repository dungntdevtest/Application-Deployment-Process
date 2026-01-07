
# Application Deployment Process

**Flutter App – Dev / Staging / Production**
**Using Fastlane & Firebase App Distribution**

## 1. Overview

The application is deployed using **three separate environments** to ensure stability and quality:

* **Development (Dev)** – internal testing
* **Staging (Stg)** – client review / UAT
* **Production (Prod)** – official public release

Each environment is fully isolated with its own configuration and data.

---

## 2. Environment Separation

Each environment has its own:

* Application identifier (Bundle ID / Package Name)
* Firebase project
* Firebase services configuration (Chat via Firestore, Push via FCM)
* Build & deployment pipeline

This ensures:

* No data overlap between environments
* Safe testing and validation
* Controlled production releases

---

## 3. Deployment Tools

**Fastlane** is used as the **single deployment automation tool** for all environments.

* For **Dev & Staging**:

  * Fastlane builds the app and distributes it via **Firebase App Distribution**
* For **Production**:

  * Fastlane builds and uploads the app to **App Store Connect** and **Google Play Console**

This guarantees consistency across all deployments.

---

## 4. Development & Staging Deployment

(**Fastlane + Firebase App Distribution**)

### Purpose

* Rapid distribution to testers
* No dependency on app store approval
* Easy feedback and iteration

### High-level Process

1. Development team triggers a **Dev or Staging build**
2. Fastlane:

   * Builds the app for the selected environment
   * Uploads the build to **Firebase App Distribution**
3. Testers receive an email invitation
4. Testers install and test the application
5. New builds can be distributed at any time with release notes

---

## 5. Production Deployment

(**Fastlane + App Stores**)

### Purpose

* Official public release
* Store review and version control
* Secure signing and upload

### High-level Process

1. Production build is generated
2. Fastlane:

   * Handles code signing
   * Uploads the build to the stores
3. App is reviewed by Apple / Google
4. After approval, the app is released to users

---

## 6. Client Responsibilities

To enable this deployment flow, the client provides:

* Firebase access for Dev / Stg / Prod
* Apple Developer account access
* Google Play Console access

---

## 7. Client Benefits

* Faster testing and feedback cycles
* Clear separation between environments
* Lower release risk
* Scalable deployment strategy for future growth

---
