# EU AI Act Posture Scanner - Project Documentation

**Project Status:** MVP Complete
**Last Updated:** January 2026
**Live URL:** https://posture-scanner.quantivecyber.com

---

## Executive Summary

The EU AI Act Posture Scanner is a web-based SaaS tool that enables organizations to automatically assess their Microsoft 365 environment's compliance posture against the EU AI Act. The tool connects to customer tenants via Microsoft Graph API and provides instant compliance scoring, risk classification, and actionable recommendations.

---

## What Has Been Built

### 1. Landing Page (index.html)
- Professional marketing page explaining the tool's value proposition
- Feature highlights and "How It Works" section
- EU AI Act risk category explanations
- Call-to-action buttons linking to the scanner
- Responsive design for mobile/desktop

**URL:** https://posture-scanner.quantivecyber.com

### 2. Posture Scanner Application (posture-scanner.html)
- Full single-page application (SPA)
- Microsoft authentication via MSAL.js
- Real-time scanning of Microsoft 365 environments
- Demo mode for client presentations

**Key Features:**
| Feature | Description |
|---------|-------------|
| Microsoft SSO | OAuth 2.0 authentication with PKCE flow |
| AI Systems Discovery | Detects OAuth apps, Copilot, third-party AI tools |
| Risk Classification | Categorizes AI systems as Prohibited/High-Risk/Limited/Minimal |
| Compliance Scoring | Overall posture score with category breakdowns |
| Gap Analysis | Identifies compliance gaps with remediation guidance |
| Data Governance Check | Assesses sensitivity labels, DLP policies |
| Company Logos | Visual identification of discovered AI vendors |
| Demo Mode | Sample data for sales demonstrations |

### 3. Azure App Registration
- **App Name:** Quantive
- **Client ID:** 132d94bd-3524-4213-8bb8-9ece8a640998
- **Authentication:** Multi-tenant (any Azure AD organization)
- **Redirect URI:** https://posture-scanner.quantivecyber.com/posture-scanner.html

**API Permissions (Delegated):**
- User.Read
- Directory.Read.All
- Application.Read.All
- Policy.Read.All
- AuditLog.Read.All
- Reports.Read.All
- Sites.Read.All

### 4. Customer Tracking System
- Webhook integration with Make.com
- Google Sheets logging for customer connections
- Tracks: Tenant name, User email, Timestamp, Scan results

**Tracked Events:**
| Event | Data Captured |
|-------|---------------|
| customer_connected | Tenant name, Tenant ID, User email, Display name |
| scan_completed | Overall score, AI systems found, High-risk count, Gaps identified |

### 5. GitHub Pages Hosting
- **Repository:** Quantive-App-Reg
- **Custom Domain:** posture-scanner.quantivecyber.com
- **CNAME:** Configured
- **HTTPS:** Enabled

---

## Technical Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                     USER BROWSER                             │
│  ┌─────────────────┐    ┌─────────────────────────────────┐ │
│  │  Landing Page   │───▶│     Posture Scanner App         │ │
│  │  (index.html)   │    │   (posture-scanner.html)        │ │
│  └─────────────────┘    └───────────────┬─────────────────┘ │
└─────────────────────────────────────────┼───────────────────┘
                                          │
                    ┌─────────────────────┼─────────────────────┐
                    │                     │                     │
                    ▼                     ▼                     ▼
          ┌─────────────────┐   ┌─────────────────┐   ┌─────────────────┐
          │   Microsoft     │   │    Make.com     │   │   GitHub        │
          │   Graph API     │   │    Webhook      │   │   Pages         │
          │                 │   │                 │   │                 │
          │ • User info     │   │ • Track events  │   │ • Static        │
          │ • Applications  │   │ • Log to Sheets │   │   hosting       │
          │ • Policies      │   │                 │   │                 │
          │ • OAuth grants  │   │                 │   │                 │
          └─────────────────┘   └────────┬────────┘   └─────────────────┘
                                         │
                                         ▼
                                ┌─────────────────┐
                                │  Google Sheets  │
                                │  (Customer Log) │
                                └─────────────────┘
```

---

## Current Limitations

1. **Client-Side Only** - All processing happens in browser; no backend server
2. **No User Accounts** - No persistent customer accounts or login
3. **No Historical Data** - Scans are point-in-time; no trend tracking
4. **No Payment Integration** - No billing or subscription management
5. **Manual Onboarding** - Customers self-serve; no guided setup
6. **Single Scan** - No scheduled or recurring scans

---

## Future Enhancements

### Phase 1: Monetization (Priority: High)
| Enhancement | Description | Effort |
|-------------|-------------|--------|
| Stripe Integration | Add payment processing for Pro tier | Medium |
| Pricing Page | Add pricing section to landing page | Low |
| Feature Gating | Lock advanced features behind paywall | Medium |
| PDF Report Export | Downloadable compliance report | Medium |

### Phase 2: Backend Infrastructure (Priority: High)
| Enhancement | Description | Effort |
|-------------|-------------|--------|
| Backend API | Node.js/Python API server | High |
| Database | PostgreSQL for customer data | High |
| User Authentication | Auth0/Clerk for customer accounts | Medium |
| Secure Token Storage | Server-side token management | High |

### Phase 3: Enhanced Features (Priority: Medium)
| Enhancement | Description | Effort |
|-------------|-------------|--------|
| Scheduled Scans | Daily/weekly automated scans | Medium |
| Email Alerts | Notifications when posture changes | Low |
| Historical Tracking | Trend analysis over time | Medium |
| Remediation Tracking | Mark gaps as resolved | Low |
| Multi-Tenant Dashboard | Manage multiple customer tenants | High |

### Phase 4: Integrations (Priority: Low)
| Enhancement | Description | Effort |
|-------------|-------------|--------|
| Jira/ServiceNow | Create tickets for gaps | Medium |
| Slack/Teams | Real-time notifications | Low |
| API Access | Programmatic access for enterprise | High |
| SSO (SAML) | Enterprise single sign-on | Medium |

### Phase 5: Compliance Expansion (Priority: Low)
| Enhancement | Description | Effort |
|-------------|-------------|--------|
| GDPR Module | Add GDPR compliance checks | High |
| ISO 27001 | Add ISO compliance mapping | High |
| SOC 2 | Add SOC 2 compliance checks | High |
| Custom Frameworks | User-defined compliance frameworks | High |

---

## File Structure

```
c:\Projects\Quantive-App-Reg\
├── index.html              # Landing/marketing page
├── posture-scanner.html    # Main scanner application
├── CNAME                   # Custom domain configuration
├── README.md               # Repository readme
└── CONFLUENCE-DOC.md       # This documentation
```

---

## Configuration Reference

### MSAL Configuration (posture-scanner.html)
```javascript
const msalConfig = {
    auth: {
        clientId: "132d94bd-3524-4213-8bb8-9ece8a640998",
        authority: "https://login.microsoftonline.com/common",
        redirectUri: window.location.origin + window.location.pathname
    }
};
```

### Tracking Webhook (posture-scanner.html)
```javascript
const trackingConfig = {
    webhookUrl: "https://hook.eu1.make.com/wdpxaxousk7xqwrh1qast536jbjhu5y4",
    enabled: true
};
```

### Make.com Scenario
- **Trigger:** Custom Webhook
- **Action:** Google Sheets - Add a Row
- **Sheet:** Data (in EU AI ACT Posture spreadsheet)

---

## Related Resources

| Resource | URL |
|----------|-----|
| Live Scanner | https://posture-scanner.quantivecyber.com |
| EU AI Act Assessment | https://eu-ai-act.quantivecyber.com |
| AI Readiness Check | https://ai-readiness.quantivecyber.com |
| Customer Tracking Sheet | https://docs.google.com/spreadsheets/d/1mjYudF4hS8RA-JuVT18XW_4ae8ewwA6V_DThTRDYm9g |
| Azure App Registration | Azure Portal > App Registrations > Quantive |

---

## Contact

**Project Owner:** QuantiveCyber
**Support:** support@quantivecyber.com
**Website:** https://quantivecyber.com
