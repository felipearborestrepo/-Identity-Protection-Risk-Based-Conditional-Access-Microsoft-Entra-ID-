# 🛡️ Identity Protection & Risk-Based Conditional Access (Microsoft Entra ID)
**Focus:** Risk detections • User risk remediation • Sign-in risk response • Self-defending identities  
**Platform:** Microsoft Entra ID (Azure AD)  
**Level:** IAM / SOC-aligned / SC-300

<img width="1536" height="1024" alt="ChatGPT Image Feb 1, 2026 at 01_10_13 PM" src="https://github.com/user-attachments/assets/6aaaa949-0b13-4616-afd2-8e2ad7be6c91" />

---

## 📌 Project Summary
This lab demonstrates how Microsoft Entra ID can **automatically detect risky identity behavior** and **enforce Conditional Access responses** in real time.

Instead of applying MFA to everyone all the time, this architecture applies stronger controls **only when Entra detects risk** such as:
- Anonymous IP / VPN / TOR usage
- Suspicious sign-in patterns
- Credential leak indicators
- Impossible travel scenarios

The result is an identity environment that **adapts to risk automatically**.

---

## 🎯 What You’ll Build
✅ User Risk Policy (forces password reset for compromised users)  
✅ Sign-In Risk Conditional Access policy (MFA triggered by risk)  
✅ Identity Protection monitoring dashboard  
✅ Validation using Risk Detections + Sign-in Logs  
✅ Evidence pack showing CA triggered **because of risk**

---

## 🧰 Requirements
- Microsoft Entra ID tenant
- Entra ID P2 (Identity Protection features)
- At least one test user:
  - `Felipe-User` or `Felipe-Admin`
- VPN / hotspot / alternate network (to simulate risk)

---

# 🧱 PHASE 0 — Identity Protection Dashboard (Baseline)
**Path:**  
Entra admin center → **Protection** → **Identity Protection** → **Dashboard**

This page shows:
- Risky users
- Risk detections
- Attacks blocked
- High-risk users

At the start of the lab, this should show **no data**.

📸 Screenshot:

![1](https://github.com/user-attachments/assets/f240d581-0df9-4650-93a3-4b83091f733d)

---

# 🔐 PHASE 1 — Configure User Risk Policy
**Purpose:** Protect accounts Entra believes are compromised.

**Path:**  
Identity Protection → **Risk-based Conditional Access** → **User risk policy**

### Configuration

| Setting | Value |
|---|---|
| Users | All users (exclude break-glass) |
| User risk | High |
| Control | Require password change |
| Enforce | On |

This means:
> If a user is marked **High Risk**, they must reset their password.

📸 Screenshot:

![2](https://github.com/user-attachments/assets/09e94d6c-0856-4845-803a-f9ab104c70a2)

![3](https://github.com/user-attachments/assets/279c68e5-1ba9-420d-bc47-10fa73a0d3e7)

![4](https://github.com/user-attachments/assets/d9ab2a20-7bb9-4877-a683-bba3d10b807f)

![5](https://github.com/user-attachments/assets/d86ec011-e4e4-411d-a15d-72663419a069)

---

# 🧠 PHASE 2 — Create Sign-In Risk Conditional Access Policy
**Purpose:** Trigger MFA only when sign-in behavior is suspicious.

**Path:**  
Entra → **Protection** → **Conditional Access** → **New policy**

**Policy Name:**  
`CA – Sign-In Risk – Require MFA`

### Assignments

| Setting | Value |
|---|---|
| Users | All users (exclude break-glass) |
| Cloud apps | All cloud apps |
| Conditions | Sign-in risk = Medium and High |
| Grant | Require MFA |
| Enable | On |

📸 Screenshots:

![6](https://github.com/user-attachments/assets/47e9efb8-7012-4ff8-950d-b2f3a0d68fa9)

![7](https://github.com/user-attachments/assets/4d6636ab-8bb6-45b1-a0f3-5be1c3b2a388)

![8](https://github.com/user-attachments/assets/d8d24dca-cbcb-4629-9281-f052581e66b0)

---

# 🧪 PHASE 3 — Trigger a Risky Sign-In
**Purpose:** Generate real risk data.

Simulate risk by:
- Using a VPN
- Using a phone hotspot
- Logging in from an unfamiliar network
- Using incognito browser

Sign in as:
- `Felipe-User` or `Felipe-Admin`

<img width="603" height="1311" alt="9" src="https://github.com/user-attachments/assets/b573ccad-5a16-4032-bb08-ed0981695d6d" />

<img width="603" height="1311" alt="10" src="https://github.com/user-attachments/assets/80ace52b-5866-411a-b656-91eb83249507" />

<img width="603" height="1311" alt="11" src="https://github.com/user-attachments/assets/dc24f76f-8f8c-454d-9aea-06460967f7fd" />

![12](https://github.com/user-attachments/assets/78bee970-816e-48e9-930c-49f5b45e04ea)

---

# 🔎 PHASE 4 — Observe Risk Detection
**Path:**  
Identity Protection → **Risk detections**

You should begin seeing:
- Risky sign-ins
- Risk level
- Location anomaly or unfamiliar properties

📸 Screenshot:
- Risk detections page showing the event

![Image 2-1-26 at 12 57](https://github.com/user-attachments/assets/d60b4979-05f4-4b5c-86f3-813dc1cea210)

---

# 📊 IAM Evidence Pack
Capture these screenshots for documentation:

1. Identity Protection dashboard (before)
2. User Risk policy
3. Sign-In Risk CA policy
4. Risk detections page
5. Sign-in log → Conditional Access tab
6. Sign-in log → Authentication details

This proves:
> Entra detected suspicious behavior and automatically enforced stronger authentication.

---

# ✅ Results
This project demonstrates:
- Automatic detection of risky identities
- Conditional Access reacting to risk signals
- Password reset enforcement for compromised users
- Real-time identity protection using Entra

---

# 🧾 Skills Demonstrated
- Microsoft Entra Identity Protection
- Risk-based Conditional Access
- Adaptive authentication
- Identity monitoring & investigation
- Zero Trust IAM principles
