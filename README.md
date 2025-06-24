# 🚀 Static Website Deployment to AWS S3 + CloudFront (CI/CD + SNS Enabled)

This project demonstrates a production-grade deployment pipeline for a static website using **AWS S3, CloudFront, GitHub Actions, Terraform**, and **SNS for notifications**.

---

## 📦 Project Structure

```
cicd-deployment_s3/
├── .github/workflows/
│   └── deploy.yml              # GitHub Actions pipeline
├── terraform/
│   ├── main.tf                 # Core AWS resources
│   ├── provider.tf             # AWS provider setup
│   ├── variable.tf             # Input variables
│   ├── versioning.tf           # Versioning, encryption, lifecycle
│   ├── output.tf               # CloudFront output
├── website/
│   ├── index.html              # Home page (static content)
│   └── error.html              # Error fallback
```

---

## ⚙️ Key Features

| Feature                     | Description                                                     |
| --------------------------- | --------------------------------------------------------------- |
| **S3 Static Hosting**       | Bucket serves `index.html` and `error.html`                     |
| **CloudFront CDN**          | Distributes content globally with low latency                   |
| **Terraform IAC**           | Infrastructure is declared as code and reproducible             |
| **GitHub Actions CI/CD**    | Automatic deployment on `main` branch push                      |
| **AWS SNS**                 | Email notifications on deployment success/failure               |
| **Versioning + Encryption** | Enables object versioning and server-side encryption (SSE-S3)   |
| **Lifecycle Rules**         | Automatically expires non-current object versions after 90 days |

---

## 🧱 Architecture Diagram

![image](https://github.com/user-attachments/assets/46a25e0c-1cee-4046-bf1c-c16d0a89a4f8)

---

## 🔐 AWS Resources

### S3 Bucket Configuration:

* Versioning: Enabled
* Encryption: SSE-S3 (AES256)
* Lifecycle: Deletes non-current versions after 90 days
* Static Hosting: Enabled

### CloudFront:

* Serves content from S3
* Caching and invalidation supported

### SNS:

* Sends deployment success/failure emails

---

## ✅ How to Deploy

1. Clone the repo
2. Configure AWS secrets in GitHub (`AWS_ACCESS_KEY_ID`, `AWS_SECRET_ACCESS_KEY`)
3. Push to `main` branch — CI/CD will auto-deploy via GitHub Actions
4. View your site at the generated CloudFront URL

---

## 📩 Output Example

```
cloudfront_url = "https://d285k8rrfguok3.cloudfront.net/"
```

---

