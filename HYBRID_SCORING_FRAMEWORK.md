# Hybrid AI Readiness & EU AI Act Compliance Framework

**Version:** 1.0 | **Date:** January 2026

---

## Executive Summary

This framework combines:
1. **AI Readiness Assessment (100-Point Scoring)** - Technical security posture checks that are largely auto-detectable
2. **EU AI Act Alignment (Informational)** - Regulatory compliance view showing what's needed for EU AI Act

The scoring drives the ROI Calculator. The EU AI Act section provides compliance context and actionable guidance.

---

## Part 1: AI Readiness Score (100 Points)

### Risk Level Mapping

| Score | Risk Level | AI Readiness | Agent Readiness | Breach Probability |
|-------|------------|--------------|-----------------|-------------------|
| 0-35 | CRITICAL | Not Ready | Not Ready | 30-40% |
| 36-70 | ELEVATED | Conditional | Not Ready | 15-25% |
| 71-100 | MANAGED | Ready | Ready with Controls | 5-10% |

---

### Category 1: Data Visibility & Discovery (10 pts, 5 tests)

| Test | Points | Auto-Detect | Graph API / Method | EU AI Act Article |
|------|--------|-------------|-------------------|-------------------|
| 1.1 Business Data Mapping | 2 | Partial | Cloud Discovery API, SP Sites | Art. 10 - Data Governance |
| 1.2 Classification Coverage | 3 | Yes | Purview Information Protection API | Art. 10 - Data Governance |
| 1.3 Classification Accuracy | 2 | Partial | Content Explorer sampling | Art. 10 - Data Quality |
| 1.4 Audit Logging Enabled | 1 | Yes | Audit API search | Art. 12 - Record Keeping |
| 1.5 Shadow IT Discovery | 2 | Yes | MDCA Cloud Discovery (filter: Generative AI) | Art. 9 - Risk Management |

**Scoring Logic:**
```
1.1: 2 = >90% sources identified | 1 = 70-90% | 0 = <70%
1.2: 3 = >80% content classified | 2 = 40-80% | 1 = 10-40% | 0 = <10%
1.3: 2 = <10% misclassification | 1 = 10-25% | 0 = >25%
1.4: 1 = Audit enabled with data | 0 = Disabled
1.5: 2 = AI apps identified | 1 = Limited visibility | 0 = None
```

---

### Category 2: Identity & Access Governance (20 pts, 9 tests)

| Test | Points | Auto-Detect | Graph API / Method | EU AI Act Article |
|------|--------|-------------|-------------------|-------------------|
| 2.1 MFA for Admins | 2 | Yes | Conditional Access Policies API | Art. 9 - Risk Management |
| 2.2 MFA for All Users | 2 | Yes | Conditional Access Policies API | Art. 9 - Risk Management |
| 2.3 Legacy Auth Blocked | 1 | Yes | Conditional Access Policies API | Art. 9 - Risk Management |
| 2.4 Conditional Access Policies | 3 | Yes | Conditional Access Policies API | Art. 9 - Risk Management |
| 2.5 Privileged Identity Management | 3 | Yes | PIM API (requires P2) | Art. 9, Art. 14 - Oversight |
| 2.6 Access Reviews | 3 | Yes | Access Reviews API (requires P2) | Art. 9, Art. 14 - Oversight |
| 2.7 Role Assignment Quality | 2 | Yes | Directory Roles API | Art. 9 - Risk Management |
| 2.8 Admin Account Count | 2 | Yes | Directory Roles API (Global Admin) | Art. 9 - Risk Management |
| 2.9 Sign-in Risk Policies | 2 | Yes | Identity Protection API (requires P2) | Art. 9 - Risk Management |

**Scoring Logic:**
```
2.1: 2 = MFA all admins | 1 = Some exclusions | 0 = Not enforced
2.2: 2 = MFA all users (<5% exclusions) | 1 = 5-20% exclusions | 0 = Not enforced
2.3: 1 = Legacy blocked | 0 = Not blocked
2.4: 3 = Comprehensive (device, location, app) | 2 = Good with gaps | 1 = MFA only | 0 = None
2.5: 3 = All privileged roles in PIM | 2 = Some roles | 1 = Minimal | 0 = None/No license
2.6: 3 = Regular reviews, >80% completion | 2 = Inconsistent | 1 = Limited | 0 = None
2.7: 2 = Least privilege | 1 = Some over-privileged | 0 = Poor
2.8: 2 = 2-4 Global Admins | 1 = 5-8 | 0 = >8
2.9: 2 = Sign-in + user risk configured | 1 = Basic | 0 = None/No license
```

---

### Category 3: Data Classification & Protection (15 pts, 6 tests)

| Test | Points | Auto-Detect | Graph API / Method | EU AI Act Article |
|------|--------|-------------|-------------------|-------------------|
| 3.1 Label Taxonomy Structure | 3 | Yes | Information Protection Labels API | Art. 10 - Data Governance |
| 3.2 Protection Actions Configured | 3 | Yes | Label policy settings | Art. 10 - Data Protection |
| 3.3 Auto-labeling Policies | 3 | Yes | Auto-labeling policies API | Art. 10 - Data Governance |
| 3.4 Auto-labeling Performance | 2 | Partial | Activity Explorer / simulation | Art. 10 - Data Quality |
| 3.5 DLP Policy Quality | 2 | Yes | DLP Policies API | Art. 10, Art. 15 - Protection |
| 3.6 User Labeling Adoption | 2 | Partial | Activity Explorer (manual label events) | Art. 4 - AI Literacy |

**Scoring Logic:**
```
3.1: 3 = 4-8 labels, clear hierarchy | 2 = Minor gaps | 1 = Basic issues | 0 = None
3.2: 3 = Encryption on sensitive + markings | 2 = Good with gaps | 1 = Markings only | 0 = None
3.3: 3 = Multiple policies, >85% accuracy, active | 2 = 70-85% | 1 = Basic | 0 = None
3.4: 2 = <10% false positives | 1 = 10-20% | 0 = High/poor
3.5: 2 = Well-tuned policies | 1 = Basic, needs tuning | 0 = Poor/None
3.6: 2 = High engagement | 1 = Moderate | 0 = Low
```

---

### Category 4: Device & Endpoint Security (5 pts, 2 tests)

| Test | Points | Auto-Detect | Graph API / Method | EU AI Act Article |
|------|--------|-------------|-------------------|-------------------|
| 4.1 Devices Onboarded to Purview | 3 | Yes | Device onboarding status API | Art. 9 - Risk Management |
| 4.2 Endpoint DLP Policies | 2 | Yes | Endpoint DLP settings | Art. 10 - Data Protection |

**Scoring Logic:**
```
4.1: 3 = >80% onboarded | 2 = 50-80% | 1 = <50% | 0 = None
4.2: 2 = Comprehensive (USB, print, browser) | 1 = Basic | 0 = None
```

---

### Category 5: Collaboration Security (11 pts, 5 tests)

| Test | Points | Auto-Detect | Graph API / Method | EU AI Act Article |
|------|--------|-------------|-------------------|-------------------|
| 5.1 External Sharing Policies | 3 | Yes | SharePoint Settings API | Art. 10 - Data Minimization |
| 5.2 Guest Access Configuration | 2 | Yes | External Identities settings | Art. 9 - Risk Management |
| 5.3 Sensitivity Labels on Sites/Teams | 2 | Yes | Container labels API | Art. 10 - Data Governance |
| 5.4 Oversharing Detection | 2 | Yes | Data Access Governance reports | Art. 9 - Risk Management |
| 5.5 Sharing Link Defaults | 2 | Yes | SharePoint Settings API | Art. 10 - Data Minimization |

**Scoring Logic:**
```
5.1: 3 = Restricted with domain controls | 2 = Moderate | 1 = Basic | 0 = Unrestricted
5.2: 2 = Controlled with expiration | 1 = Basic | 0 = Unrestricted
5.3: 2 = Container labels deployed | 1 = Available, limited use | 0 = None
5.4: 2 = No significant oversharing | 1 = Some identified | 0 = Widespread
5.5: 2 = "Specific people" default | 1 = "People in org" | 0 = "Anyone"
```

---

### Category 6: AI & Agent Governance (39 pts, 14 tests)

| Test | Points | Auto-Detect | Graph API / Method | EU AI Act Article |
|------|--------|-------------|-------------------|-------------------|
| 6.1 AI Tool Discovery | 3 | Yes | MDCA Cloud Discovery (Generative AI filter) | Art. 9 - Risk Management |
| 6.2 AI Interaction Monitoring | 3 | Yes | Activity Explorer + Copilot Reports | Art. 12 - Record Keeping |
| 6.3 AI-Specific DLP | 3 | Yes | DLP policies targeting AI/Copilot | Art. 10, Art. 15 - Protection |
| 6.4 External AI Controls | 3 | Yes | CA policies + MDCA blocking | Art. 5, Art. 9 - Prohibited/Risk |
| 6.5 Copilot Configuration | 2 | Yes | Copilot Admin Settings API | Art. 9 - Risk Management |
| 6.6 Restricted SharePoint Search | 3 | Yes | SharePoint Search settings | Art. 10 - Data Minimization |
| 6.7 Label Inheritance for AI | 2 | Partial | Label policy inheritance check | Art. 10 - Data Governance |
| 6.8 AI Oversharing Audit | 4 | Yes | Data Access Governance + DSPM | Art. 9 - Risk Management |
| 6.9 Insider Risk for AI Users | 1 | Yes | IRM policy check for AI indicators | Art. 9 - Risk Management |
| 6.10 DSPM for AI | 4 | Yes | DSPM for AI status (E5 required) | Art. 9, Art. 10 - Management |
| 6.11 Agent Governance Settings | 2 | Yes | Agent settings API | Art. 14 - Human Oversight |
| 6.12 Insider Risk - Agent Policies | 2 | Yes | IRM Agent policies | Art. 9 - Risk Management |
| 6.13 Conditional Access for Agents | 2 | Yes | CA for Agent IDs (Preview) | Art. 14 - Human Oversight |
| 6.14 Adaptive Protection | 2 | Yes | Adaptive Protection status (E5) | Art. 9 - Risk Management |

**Scoring Logic:**
```
6.1: 3 = Comprehensive AI discovery | 2 = Limited | 1 = Gaps | 0 = None
6.2: 3 = Comprehensive monitoring | 2 = Basic | 1 = Limited | 0 = None
6.3: 3 = Dedicated AI/Copilot DLP | 2 = Some coverage | 1 = Minimal | 0 = None
6.4: 3 = Blocked/controlled via CA/MCAS | 2 = Partial | 1 = Minimal | 0 = None
6.5: 2 = Appropriate restrictions | 1 = Basic | 0 = Defaults only
6.6: 3 = Sensitive sites excluded | 2 = Some restrictions | 1 = Aware, not configured | 0 = None
6.7: 2 = Labels inherited | 1 = Partial/inconsistent | 0 = Not verified/stripped
6.8: 4 = Audit complete, minimal oversharing | 3 = Remediation in progress | 2 = Known, not fixed | 1 = Basic awareness | 0 = None
6.9: 1 = IRM covers AI indicators | 0 = No coverage
6.10: 4 = >50% recommendations actioned | 3 = Some actioned | 2 = Minimal config | 1 = Not configured | 0 = Not enabled/No license
6.11: 2 = Configured with restrictions | 1 = Basic | 0 = Defaults
6.12: 2 = Risky Agents policy tuned | 1 = Default deployed | 0 = None
6.13: 2 = CA policies for agents | 1 = Basic | 0 = None
6.14: 2 = Enabled, IRM-to-DLP active | 1 = Partial | 0 = Not configured/No license
```

---

## Part 2: EU AI Act Alignment (Informational Section)

This section does NOT contribute to the score. It provides compliance context.

### AI Systems Risk Classification

The scanner discovers AI systems and classifies them:

| Risk Level | Examples | EU AI Act Requirement | Action Required |
|------------|----------|----------------------|-----------------|
| **PROHIBITED** | Social scoring, real-time biometric ID (public), emotion recognition (workplace) | Must be removed immediately | Immediate removal |
| **HIGH-RISK** | HR/recruitment AI, credit scoring, biometric categorization | Conformity assessment, human oversight, documentation | Full compliance programme |
| **LIMITED** | Chatbots, AI-generated content | Transparency obligations - disclose AI use | User notifications |
| **MINIMAL** | Spam filters, AI-enhanced search, general productivity AI | Voluntary best practices | No mandatory requirements |

### Key EU AI Act Articles Mapped to Technical Controls

| Article | Requirement | How Scanner Checks Address It |
|---------|-------------|------------------------------|
| **Art. 4** | AI Literacy | 3.6 User labeling adoption, training programmes |
| **Art. 5** | Prohibited AI | 6.4 External AI controls blocking prohibited systems |
| **Art. 9** | Risk Management | Identity controls (Cat 2), AI controls (Cat 6), IRM |
| **Art. 10** | Data Governance | Data classification (Cat 1, 3), DLP, labeling |
| **Art. 11** | Technical Documentation | Manual: AI system cards and documentation |
| **Art. 12** | Record Keeping | 1.4 Audit logging, 6.2 AI interaction monitoring |
| **Art. 14** | Human Oversight | 2.5 PIM, 2.6 Access reviews, 6.11-6.13 Agent governance |
| **Art. 15** | Accuracy & Security | 3.5 DLP quality, 6.3 AI-specific DLP |
| **Art. 52** | Transparency | Manual: AI disclosure notices |

### EU AI Act Compliance Status Display

For each discovered AI system, show:
- System name and type
- Risk classification (with color badge)
- Applicable articles
- Current compliance gaps
- Recommended actions

---

## Part 3: UI Structure

### Dashboard Layout

```
+------------------------------------------------------------------+
|  HEADER: QuantiveCyber | AI Readiness Scanner | Tenant | Actions |
+------------------------------------------------------------------+
|  ALERT BANNER (if score < 36: Critical | 36-70: Elevated)        |
+------------------------------------------------------------------+
|  STATS ROW: AI Systems | Risk Level | Copilot Users | Score      |
+------------------------------------------------------------------+
|                                                                   |
|  +---------------------------+  +-------------------------------+ |
|  | AI READINESS SCORE        |  | EU AI ACT ALIGNMENT           | |
|  | [Ring: 58/100]            |  | Discovered Systems: 12        | |
|  | ELEVATED - Conditional    |  | - 0 Prohibited                | |
|  | Ready for AI              |  | - 3 High-Risk                 | |
|  |                           |  | - 12 Limited                  | |
|  | Categories:               |  | - 3 Minimal                   | |
|  | - Data Visibility    8/10 |  |                               | |
|  | - Identity & Access 15/20 |  | [View Compliance Details]     | |
|  | - Classification    10/15 |  +-------------------------------+ |
|  | - Device Security    3/5  |                                    |
|  | - Collaboration      8/11 |                                    |
|  | - AI Governance     14/39 |                                    |
|  +---------------------------+                                    |
|                                                                   |
+------------------------------------------------------------------+
|  IMPROVE YOUR SCORE                              +42 pts available|
|  +-------------------------------------------------------------+ |
|  | Control | Category | Points | Article | Action               | |
|  | AI Oversharing Audit | AI Gov | +4 | Art.9 | Run DSPM audit  | |
|  | DSPM for AI | AI Gov | +4 | Art.9,10 | Enable DSPM          | |
|  | Access Reviews | Identity | +3 | Art.14 | Configure reviews  | |
|  | ... (sorted by points available)                             | |
|  +-------------------------------------------------------------+ |
+------------------------------------------------------------------+
|  IMPLEMENTED CONTROLS (Collapsible)               58 pts earned  |
+------------------------------------------------------------------+
|  DISCOVERED AI SYSTEMS                                           |
|  [Expandable cards with risk badges and compliance details]      |
+------------------------------------------------------------------+
|  EU AI ACT COMPLIANCE GAPS (if high-risk systems detected)       |
|  [Priority actions for high-risk AI compliance]                  |
+------------------------------------------------------------------+
```

---

## Part 4: Auto-Detection Capability Summary

### Fully Auto-Detectable (32 tests)
These can be checked via Graph API without manual intervention:
- All of Category 2 (Identity - 9 tests)
- All of Category 4 (Device - 2 tests)
- All of Category 5 (Collaboration - 5 tests)
- Most of Category 6 (AI Governance - 12 of 14 tests)
- 1.4, 1.5 from Category 1
- 3.1, 3.2, 3.3, 3.5 from Category 3

### Partially Auto-Detectable (6 tests)
Need some manual verification or sampling:
- 1.1 Business Data Mapping (can detect sources, accuracy needs verification)
- 1.2 Classification Coverage (percentage detectable, quality needs review)
- 1.3 Classification Accuracy (needs sampling review)
- 3.4 Auto-labeling Performance (simulation vs production may differ)
- 3.6 User Labeling Adoption (activity detectable, engagement subjective)
- 6.7 Label Inheritance (can check settings, runtime behavior varies)

### Manual Verification Required (3 tests)
Cannot be auto-detected, require documentation review:
- Art. 11 Technical Documentation (AI system cards)
- Art. 52 Transparency Notices (user-facing AI disclosures)
- Art. 4 AI Literacy Training (training programme existence)

**Note:** Manual items appear in EU AI Act Alignment section as compliance gaps, not in the scored section.

---

## Part 5: Graph API Endpoints Required

### Core APIs (Already in use)
```
GET /organization
GET /users
GET /subscribedSkus
GET /identity/conditionalAccess/policies
GET /servicePrincipals
GET /oauth2PermissionGrants
GET /security/secureScores
```

### Additional APIs for Full 41-Test Coverage
```
# Identity & Access
GET /identity/conditionalAccess/policies
GET /privilegedAccess/aadRoles/roleAssignments
GET /accessReviews
GET /identityProtection/policies/riskPolicies
GET /directoryRoles/members (for Global Admin count)

# Information Protection
GET /informationProtection/sensitivityLabels
GET /informationProtection/policy/labels
GET /dlp/policies (Purview API)

# SharePoint/Collaboration
GET /admin/sharepoint/settings
GET /sites (with sharing settings)
GET /groups (with sensitivity labels)

# Defender for Cloud Apps
GET /security/alerts
Cloud Discovery API (for AI apps)

# Copilot & AI
GET /admin/microsoft365/copilot/settings
GET /reports/getCopilotUsage
Agent settings API
DSPM for AI status
```

---

## Part 6: Licensing Impact on Scoring

| Feature | License Required | Tests Affected | If Missing |
|---------|-----------------|----------------|------------|
| PIM | Entra ID P2 | 2.5 | Score 0, note "License required" |
| Access Reviews | Entra ID P2 | 2.6 | Score 0, note "License required" |
| Sign-in Risk | Entra ID P2 | 2.9 | Score 0, note "License required" |
| DSPM for AI | E5 Compliance | 6.10 | Score 0, note "License required" |
| Agent Governance | E5 + Copilot | 6.11-6.13 | Score 0, note "License required" |
| Adaptive Protection | E5 Compliance | 6.14 | Score 0, note "License required" |

**Scoring Adjustment:** When a feature requires a license the tenant doesn't have, the test scores 0 but is marked as "License Required" rather than "Failed". The maximum possible score adjusts accordingly in the display.

---

## Part 7: Implementation Priority

### Phase 1: Core Scoring (MVP)
1. Implement 6-category scoring structure
2. Auto-detect tests for Categories 2, 4, 5 (16 tests, 36 points)
3. Basic Category 6 AI detection (6.1, 6.4, 6.5 = 8 points)
4. EU AI Act risk classification for discovered AI

### Phase 2: Enhanced Detection
1. Category 1 & 3 data classification checks (11 tests, 25 points)
2. Remaining Category 6 AI governance (11 tests, 31 points)
3. Full EU AI Act article mapping

### Phase 3: Polish
1. Licensing detection and score adjustment
2. Manual verification prompts for partially-detectable items
3. Export/reporting enhancements

---

*Framework designed for QuantiveCyber AI Readiness Scanner - January 2026*
