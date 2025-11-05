# Nexus ERP Platform

### Author
**Abdul Syed – Lead Cloud & Integration Engineer, Nexus Systems Inc.**

---

## 1. Overview
**Nexus ERP Platform** is a **cloud-native SaaS application** that extends enterprise procurement capabilities by integrating with **SAP S/4HANA** through **SAP Business Technology Platform (BTP)** and **SAP Event Mesh**.  
It enables users to create purchase requisitions (PRs), automatically synchronize them with SAP, and receive real-time order status updates and analytics on vendor spend and cycle times.

---

## 2. Objectives
- Simplify purchase-requisition submission and tracking  
- Enable **event-driven, near-real-time** synchronization with SAP  
- Demonstrate **SAP-on-Azure** integration and automation patterns  
- Validate cloud-native scalability, observability, and security design

---

## 3. System Architecture Summary
| Layer | Technologies / Responsibilities |
|-------|--------------------------------|
| **Frontend** | React / Flask web form for PR creation and status view |
| **Microservices** | `PR Service`, `SAP Sync Service` (BTP iFlow), `Event Handler`, `Analytics Service` |
| **Cloud Infrastructure** | Azure App Service or AKS, Azure SQL or Cosmos DB, Storage, Application Insights |
| **Integration Layer** | SAP BTP Integration Suite (iFlow) + SAP Event Mesh |
| **Security** | Azure AD (OIDC OAuth 2.0), HTTPS TLS 1.2+, RBAC policy enforcement |

---

## 4. High-Level Flow
1. User submits a PR in Nexus → PR Service stores request + sends to SAP via BTP iFlow  
2. SAP acknowledges PR ID / status → Nexus updates record  
3. SAP emits events (PO created, goods receipt) → Event Mesh → Nexus Event Handler  
4. Event Handler updates DB → Analytics Service aggregates metrics → Dashboard refresh  

---

## 5. User Stories
1. As a buyer, I want to submit a purchase requisition so I can request goods.  
2. As a procurement officer, I want live PR→PO status updates from SAP.  
3. As a finance analyst, I want analytics on vendor spend and cycle time.  
4. As a system admin, I want secure OAuth-based integration for compliance.  
5. As an executive, I want a demo-ready proof of SAP–Azure integration.  

---

## 6. Architecture Diagram
*(See `/docs/architecture.png`)*

---

## 7. 30-Day Engineering Roadmap

### **Week 1 – Foundations & Architecture Design**
| Day | Focus |
|----:|-------|
| 1 | Define business use case (PR portal), write product brief, user stories, and architecture diagram |
| 2 | Set up Azure subscription + SAP BTP trial, verify Event Mesh & Integration Suite availability |
| 3 | Provision Azure App Service, SQL DB, Storage, Application Insights (manually) |
| 4 | Configure Azure AD tenant + app registration for OIDC login |
| 5 | Initialize Node.js or Python project structure; Dockerize base service |
| 6 | Test local API + Docker workflow |
| 7 | Push infra and code scaffold to GitHub (main branch ready) |

### **Week 2 – Core Microservices & SAP Integration (Mock)**
| Day | Focus |
|----:|-------|
| 8 | Build `PR Service` (REST API CRUD) |
| 9 | Build `Order Status Service` (SAP mock integration) |
| 10 | Containerize services → Docker Compose |
| 11 | Implement SAP BTP iFlow (mock SAP endpoint) |
| 12 | Configure SAP Event Mesh (publish dummy events) |
| 13 | Implement event listener endpoint in Nexus |
| 14 | Deploy services to Azure App Service – E2E mock loop operational |

### **Week 3 – Analytics & Cloud-Native Enhancements**
| Day | Focus |
|----:|-------|
| 15 | Design DB schema for PR/PO records |
| 16 | Add analytics API (endpoints for KPIs) |
| 17 | Optional React/Streamlit dashboard |
| 18 | Optional Power BI integration |
| 19 | Introduce Azure Service Bus queue for decoupled writes |
| 20 | Add autoscaling (App Service or AKS) |
| 21 | Integrate Application Insights + Prometheus exporters |

### **Week 4 – DevOps, Security & Hardening**
| Day | Focus |
|----:|-------|
| 22 | CI/CD pipeline (GitHub Actions – build/test/deploy) |
| 23 | Add Terraform/Bicep for infra provisioning |
| 24 | Integrate Azure AD login (OIDC) |
| 25 | Secure BTP connection (HTTPS, certificates or Cloud Connector) |
| 26 | Implement RBAC in API layer |
| 27 | Run OWASP ZAP scan + threat review |
| 28 | Write automated tests + integration validation scripts |

### **Final 2 Days – Packaging & Presentation**
| Day | Focus |
|----:|-------|
| 29 | Complete diagrams, README, and technical documentation |
| 30 | Record demo walk-through and final GitHub push |

## 8. Repository Structure

nexus-erp-platform/
├── src/                 # microservices source
├── docs/                # diagrams & architecture assets
├── .github/workflows/   # CI/CD pipeline
├── README.md
└── user_stories.md

---

## 9. Next Steps
- Build PR Service API and local mock SAP integration.  
- Connect to SAP BTP Integration Suite.  
- Implement Event Mesh listener and analytics pipeline.

---

**Status:** Week 1 in progress  
**Target:** MVP demo by Day 30  