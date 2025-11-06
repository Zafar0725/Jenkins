Polling test at: <current date/time>
# Jenkins CI/CD Pipeline – GitHub Integration (Polling Method)

## 📘 Overview
This project demonstrates how to integrate **Jenkins** with a **GitHub** repository to automatically trigger a CI/CD pipeline whenever new code changes are detected.  
The pipeline uses the **Polling** method, where Jenkins checks the repository for updates every 5 minutes.

---

## ⚙️ Pipeline Stages
The Jenkinsfile defines a complete CI/CD flow with four stages:

1. **Checkout** – Clones the GitHub repository for each build.
2. **Build** – Simulates a build process using echo commands.
3. **Test** – Runs a simple test simulation (echo “Running tests…”).
4. **Notification** – Sends success or failure messages through Jenkins console and email (using the Email Extension Plugin).

---

## 🔁 Trigger Configuration (Polling)
- **Trigger type:** Poll SCM  
- **Schedule:** `H/5 * * * *`  
  → Jenkins checks the repository every 5 minutes for any new commits.

When a commit is detected, Jenkins automatically starts a new build.

---

## 📨 Email Notification Setup
Email alerts are configured through the **Email Extension Plugin** in Jenkins.

### SMTP Configuration:
| Setting | Value |
|----------|--------|
| SMTP Server | `smtp.gmail.com` |
| Port | `465` |
| SSL | Enabled |
| Authentication | Gmail address + App Password |
| Plugin Used | Email Extension Plugin |

### Email Trigger:
- On success → Subject: “SUCCESS: Jenkins CI Pipeline”  
- On failure → Subject: “FAILURE: Jenkins CI Pipeline”

---

## 🧩 How to Test
1. Make a small code change (e.g., edit `README.md`).
2. Commit and push to GitHub.
3. Within 5 minutes, Jenkins detects the change and triggers the pipeline.
4. Check:
   - Jenkins **Console Output** → shows all 4 stages.
   - Gmail inbox → receives success/failure email.

---

## ✅ Result
The Jenkins pipeline successfully:
- Clones the GitHub repository.
- Executes all build/test stages.
- Automatically triggers via Poll SCM.
- Sends build results via email.

This fulfills the assignment requirement for integrating Jenkins with GitHub using automated CI/CD and notification stages.

---

## 🧑‍💻 Author
**Name:** Sheikh Zafrullah  
**Course:** PROG8850 – Cloud Development & Operations  
**Project:** Jenkins CI/CD Integration using Polling  
**GitHub Repo:** [https://github.com/Zafar0725/Jenkins](https://github.com/Zafar0725/Jenkins)

