# Risk Assessment Summary: Banki

A fictional Saudi digital-only bank used as the subject of this GRC portfolio project.

## 1. Scope and method

- **Scope:** 20 assets of Banki (applications, data, infrastructure, people, and vendors). Details are in `01-organization-profile.md` and `02-asset-inventory.xlsx`.
- **Method:** Each asset was linked to one main threat scenario and vulnerability (`03`). Risk was scored as **Likelihood (1-5) x Impact (1-5)** and classified using the scale in the `Risk Scale` sheet of `04-risk-assessment-register.xlsx`.
- **Controls:** Each asset was mapped to the NCA Essential Cybersecurity Controls (ECC-2:2024) with a proposed mitigation (`05`).
- **Note:** Scores are **inherent risk** (before the proposed controls are applied).

## 2. Results at a glance

| Risk level | Score range | Number of risks | Assets |
|---|---|---|---|
| Critical | 20-25 | 4 | A-01, A-02, A-06, A-08 |
| High | 15-19 | 5 | A-03, A-07, A-11, A-13, A-14 |
| Medium | 8-14 | 11 | A-04, A-05, A-09, A-10, A-12, A-15, A-16, A-17, A-18, A-19, A-20 |
| Low | 1-7 | 0 | None |

## 3. Top 5 risks

| Rank | Asset | Threat | L | I | Score | Level | Key mitigation | ECC reference |
|---|---|---|---|---|---|---|---|---|
| 1 | A-02 Mobile Banking App | Account takeover, phishing, and API exploitation | 5 | 5 | 25 | Critical | Mandatory MFA, API rate limiting, certificate pinning | 2-15 |
| 2 | A-01 Customer Database | Data exfiltration and SQL injection | 4 | 5 | 20 | Critical | AES-256 encryption at rest, strict access control, database activity monitoring | 2-7 |
| 3 | A-06 Cloud Hosting Environment | Cloud misconfiguration and resource hijacking | 4 | 5 | 20 | Critical | Cloud security posture management, configuration drift checks, IAM role isolation | 4-2 |
| 4 | A-08 Card Data | Card fraud and skimming through APIs | 4 | 5 | 20 | Critical | Hardware security modules for key management, PCI DSS tokenization | 2-8, 2-7 |
| 5 | A-14 Cybersecurity Team | Social engineering and spear phishing of administrators | 4 | 4 | 16 | High | Specialized training, quarterly phishing simulations | 1-10-4-1 |

## 4. Key observations

1. **Customer-facing and cloud assets carry the highest risk.** Three of the four Critical risks (A-01, A-02, A-06) sit on the app, the database, and the cloud environment that every customer service depends on.
2. **Ransomware affects both production and recovery.** A-11 (Core Banking) and A-13 (Backup and Recovery) both include ransomware scenarios, so a single attack could stop services and block restoration at the same time.
3. **Insider risk is concentrated on data and log assets.** A-05, A-09, A-16, and A-17 involve malicious insiders, and their scenarios rely on weak segregation of duties, privileged access, or unprotected logs.
4. **Third-party dependence is significant.** A-04, A-06, and A-20 show reliance on external providers, and the bank has no branches as a fallback.

## 5. Recommendations

| Priority | Recommendation | Addresses |
|---|---|---|
| 1 | Enforce MFA and API protection on the mobile app, and test the app and APIs before each release | A-02 |
| 2 | Encrypt customer and card data, and manage cryptographic keys in hardware security modules | A-01, A-07, A-08 |
| 3 | Monitor cloud configuration continuously and restrict public access to administrative ports | A-06, A-20 |
| 4 | Keep offline, immutable backups and test ransomware recovery regularly | A-11, A-13 |
| 5 | Apply least privilege and privileged access management, and store logs in write-once storage | A-05, A-09, A-16, A-17 |
| 6 | Run regular security training and phishing simulations for administrators and the cybersecurity team | A-14, A-18 |

## 6. Limitations

- The bank, its systems, and all ratings are **fictional** and based on the author's judgment, not on real incident data.
- Each asset has **one** main threat scenario. A full assessment would include several per asset.
- Residual risk (after controls) and a formal risk treatment plan are **not yet included**.

## 7. Next steps

1. Add a risk treatment plan: owner, action, target date, and residual risk for each Critical and High risk.
2. Add more threat scenarios for the Critical assets.
3. Review the likelihood ratings with a short justification for each score.
