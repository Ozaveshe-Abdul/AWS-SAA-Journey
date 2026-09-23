# 🚀 AWS S3 Static Website & Automation Tools

A collection of lightweight, robust **Bash scripts** built to automate infrastructure deployments and object operations on Amazon S3 using the low-level **AWS CLI `s3api`** and high-level `s3` tools.

🌐 **Live Demo:** [Visit the Hosted Website] (http://ozey-bucket-2.s3-website.eu-north-1.amazonaws.com)

---

## 🛠️ The Scripts

### 1. `configure-static-website`
Automates the full lifecycle deployment of a local web project to an S3 bucket.
* **What it does:** Configures block-public-access settings, injects dynamic JSON bucket policies, enables static web hosting (`index.html`), and syncs local codebases safely.
* **Usage:**
  ```bash
  ./configure-static-website <bucket-name> </path/to/website-folder>
  ```

### 2. `move-s3-object`
A custom utility that mimics a `mv` command for S3 virtual directory prefixes.
* **What it does:** Executes a two-step `copy-object` and `delete-object` pipeline using a strict transactional execution sequence.
* **Usage:**
  ```bash
  ./move-s3-object <bucket-name> <source-key> <destination-key>
  ```

---

## 🧠 Key Learnings Implemented

* **The Virtual Folder Illusion:** Designed scripts around the architectural reality that S3 is a flat object store mapping object prefixes using `/`.
* **Bash Strict Mode (`set -eo pipefail`):** Built-in safeguards that instantly freeze script execution if any underlying command or piped step fails, preventing accidental data loss during moves.
* **Robust Input Validation:** Implemented strict positional parameter checks and interactive prompts to handle folder spaces and guard against incorrect path scopes.

