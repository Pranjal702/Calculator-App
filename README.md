# 🧮 Calculator App

A serverless calculator web application deployed on AWS with multiple deployment methods — demonstrating modern cloud hosting, CDN distribution, and CI/CD automation.

---

## 🌐 Live Demo

- **CloudFront (CDN):** https://d2m1l2evcnlkc1.cloudfront.net
- **AWS Amplify:** https://main.dcqzc4p5lzyb4.amplifyapp.com/

---

## ☁️ AWS Services Used

### 1. **Amazon S3 (Simple Storage Service)**
- **Purpose:** Stores all static files (HTML, CSS, JavaScript)
- **Configuration:** Static website hosting enabled
- **Why:** S3 is infinitely scalable, reliable, and cost-effective for static content

---

### 2. **Amazon CloudFront (Content Delivery Network)**
- **Purpose:** Distributes content globally from edge locations
- **Benefits:**
  - ⚡ **Low latency** — serves content from servers closest to users worldwide
  - 🔒 **HTTPS enabled** — automatic SSL/TLS with free certificate
  - 📊 **Caching** — reduces load on origin S3 bucket
- **How it works:** User requests → CloudFront edge → S3 origin

---

### 3. **AWS Certificate Manager (ACM)**
- **Purpose:** Provides free SSL/TLS certificate for HTTPS
- **Setup:** DNS validation to prove domain ownership
- **Region requirement:** Must be in **us-east-1** for CloudFront compatibility
- **Renewal:** Automatic (AWS handles it for free)

---

### 4. **GitHub Actions (CI/CD Pipeline)**
- **Purpose:** Automatically deploys to S3 whenever you push code
- **Workflow:** Code push → GitHub Actions → AWS CLI → S3 sync → CloudFront invalidation
- **Files:** `.github/workflows/deploy.yml`
- **Benefits:** No manual uploads, deployment in seconds

---

### 5. **AWS Amplify (Alternative Deployment)**
- **Purpose:** Simplified serverless hosting with built-in CI/CD
- **Connected:** Linked to GitHub repository for automatic deploys
- **Benefits:** 
  - One-click setup (no manual S3 + CloudFront config)
  - Automatic HTTPS
  - Built-in CI/CD (no need for separate GitHub Actions)

---

## 🏗️ Architecture Comparison

### Setup 1: S3 + CloudFront (Manual)
```
GitHub Push
    ↓
GitHub Actions
    ↓
AWS S3 (Upload)
    ↓
CloudFront (Distribute & Cache)
    ↓
User (Fast HTTPS)
```

### Setup 2: AWS Amplify (Automated)
```
GitHub Push
    ↓
Amplify (Auto-detect & build)
    ↓
Amplify Hosting (with CDN)
    ↓
User (Fast HTTPS)
```

---

## 🚀 How to Deploy Your Own

### Option 1: Using S3 + CloudFront (Advanced)
1. Create S3 bucket with static website hosting
2. Upload files → make bucket public
3. Create CloudFront distribution pointing to S3
4. Get free SSL cert from ACM
5. Set up GitHub Actions with AWS credentials
6. Push → auto-deploys! 🎉

### Option 2: Using Amplify (Beginner-Friendly)
1. Go to AWS Amplify console
2. Connect GitHub repository
3. Done! Auto-deploys on every push 🎉

---

## 📁 Repository Structure

```
├── index.html          # Main calculator page
├── .github/
│   └── workflows/
│       └── deploy.yml # GitHub Actions workflow
└── README.md
```
