# Standards & API Reference

> Project: Performance Management Platform · Generated: 2026-05-06

## Industry Standards & Specifications

### ISO Standards

**ISO 30414:2025 — Human Resource Management: Requirements and Recommendations for Human Capital Reporting and Disclosure**
- URL: https://www.iso.org/standard/30414
- Second edition published August 2025; supersedes ISO 30414:2018. Defines 58 standardised metrics across 11 core human capital domains including compliance and ethics, costs, diversity, leadership, organisational culture, health and safety, productivity, recruitment and turnover, skills development, succession planning, and workforce availability. Unlike the 2018 guidelines, the 2025 edition establishes mandatory requirements alongside recommendations. A performance management platform producing structured performance data (review ratings, OKR completion rates, calibration distributions) should align its reporting schema and exports to ISO 30414 metrics, particularly turnover, productivity, succession planning, and skills development categories. Relevant for EU Corporate Sustainability Reporting Directive compliance and US SEC human capital disclosure requirements.

**ISO/TC 260 — Human Resource Management Standards Programme**
- URL: https://www.iso.org/committee/628737/x/catalogue/
- ISO Technical Committee 260 oversees all ISO HR standards. Key standards under TC 260 include ISO 30408 (human governance guidelines), ISO 30405 (recruitment guidelines), and the forthcoming ISO/FDIS 30201 (human resources management systems requirements). A performance management platform should monitor TC 260 publications for emerging data model standards that could affect API schema design.

**ISO/IEC 27001:2022 — Information Security Management Systems**
- URL: https://www.iso.org/standard/27001
- The international standard for information security management. Required by enterprise procurement requirements in many regulated industries. Employee performance data (review narratives, ratings, calibration outcomes, compensation linkages) constitutes sensitive personal data requiring ISO 27001-grade controls over storage, access, transmission, and incident response.

**ISO/IEC 27018:2019 — Code of Practice for Personally Identifiable Information in Public Clouds**
- URL: https://www.iso.org/standard/76559.html
- Directly relevant to cloud-hosted performance management platforms. Defines controls for processors of PII in public cloud environments, including employee performance records, 360 feedback data, and compensation information.

---

### W3C & IETF Standards

**WCAG 2.1 Level AA — Web Content Accessibility Guidelines**
- URL: https://www.w3.org/TR/WCAG21/
- The W3C accessibility standard required by employment law in most major markets. Level AA is mandated by the European Accessibility Act, UK Public Sector Bodies Accessibility Regulations, US Section 508, and the Accessible Canada Act. All employee-facing screens in a performance management platform (review forms, OKR dashboards, feedback interfaces) must conform. Level AA requires 50 success criteria across perceivable, operable, understandable, and robust dimensions. WCAG 2.2 (October 2023) adds nine additional criteria; implementing 2.2 Level AA is recommended for new builds to remain compliant through the platform's lifecycle.

**WCAG 2.2 — Web Content Accessibility Guidelines (current)**
- URL: https://www.w3.org/TR/WCAG22/
- Current published W3C recommendation as of October 2023; builds on 2.1 and adds nine new success criteria. Recommended baseline for new performance management platform development.

**RFC 6749 — OAuth 2.0 Authorization Framework**
- URL: https://datatracker.ietf.org/doc/html/rfc6749
- The IETF standard for delegated authorisation. All performance management platform API endpoints should implement OAuth 2.0. Required by BambooHR, Workday, Culture Amp, and SAP SuccessFactors for their own API access. Enterprise buyers require OAuth 2.0 for any SaaS integration approved through their IT governance process.

**RFC 7519 — JSON Web Token (JWT)**
- URL: https://datatracker.ietf.org/doc/html/rfc7519
- Defines the compact, URL-safe claims format used in OAuth 2.0 and OpenID Connect access tokens. JWT is the standard bearer token format for performance management platform API authentication; the platform's API gateway and microservices should validate JWTs for all protected endpoints.

**RFC 7643 / RFC 7644 — SCIM 2.0 (System for Cross-domain Identity Management)**
- URL: https://datatracker.ietf.org/doc/html/rfc7643 (schema) / https://datatracker.ietf.org/doc/html/rfc7644 (protocol)
- IETF standards for automated user provisioning and lifecycle management. SCIM 2.0 is the de facto standard for HRIS-to-SaaS employee roster sync, used by Okta, Azure Entra ID, OneLogin, Leapsome, and most enterprise HRIS platforms. A performance management platform must expose a SCIM 2.0 server endpoint to support automated employee creation, deactivation, and group assignment triggered by HRIS events (new hire, termination, department transfer). This is a hard requirement for enterprise procurement approval.

**OpenID Connect Core 1.0**
- URL: https://openid.net/specs/openid-connect-core-1_0.html
- Identity layer on top of OAuth 2.0. Required for Single Sign-On (SSO) integration with enterprise identity providers (Okta, Azure Entra ID, Google Workspace). Enterprise performance management buyers expect OIDC-based SSO as table stakes. GDPR compliance is strengthened by OIDC scope-based data minimisation (sharing only required claims with the platform).

---

### Data Model & API Specifications

**OpenAPI Specification 3.1**
- URL: https://spec.openapis.org/oas/v3.2.0.html
- The industry-standard machine-readable API description format. The performance management platform's public REST API should be described as an OpenAPI 3.1 document, enabling auto-generated SDKs, interactive documentation (Swagger UI / Redoc), and integration with API gateways and testing tools. OpenAPI 3.1 is fully compatible with JSON Schema 2020-12, enabling reuse of JSON Schema definitions for request and response validation.

**JSON Schema 2020-12**
- URL: https://json-schema.org/specification
- The standard schema language for validating JSON data structures. Use JSON Schema to define and validate the data models for the platform's core entities: Employee, ReviewCycle, ReviewForm, Rating, Feedback, Objective, KeyResult, CalibrationSession, and CompensationInput. Aligning internal schemas to HR Open Standards JSON conventions where published will ease third-party integration.

**HR Open Standards — HR-JSON Specifications**
- URL: https://www.hropenstandards.org/standards
- Published by the HR Open Standards Consortium (founded 1999; the only independent non-profit dedicated to HR data exchange specifications). HR-JSON covers assessments, recruiting, and employee data exchange schemas. The 4.1 HR-JSON Assessments standard is relevant to structuring performance review and 360-degree feedback data in a standards-compatible format. Implementing HR Open Standards schemas for core entities reduces integration friction with third-party HRIS and ATS platforms.

**OData Protocol v4.0**
- URL: https://www.odata.org/documentation/
- Used by SAP SuccessFactors (OData V2 and V4) and Microsoft Dynamics for HR data access. If the platform targets enterprise customers with SAP environments, implementing or supporting OData query patterns ($filter, $select, $orderby, $expand) in the integration layer will simplify connector development for SAP SuccessFactors interoperability.

---

### Security & Authentication Standards

**SOC 2 Type II (AICPA Trust Services Criteria)**
- URL: https://www.aicpa-cima.com/resources/landing/system-and-organization-controls-soc-suite-of-services
- Not a technical standard but an audit framework required by enterprise procurement. SOC 2 Type II evaluates the operational effectiveness of security, availability, processing integrity, confidentiality, and privacy controls over a minimum 6-month period. All enterprise performance management platform buyers will require a current SOC 2 Type II report before signing contracts. Planning and auditing for SOC 2 Type II should begin at least 12 months before the first enterprise sales motion.

**NIST Cybersecurity Framework 2.0**
- URL: https://www.nist.gov/cyberframework
- The US federal cybersecurity guidance framework, widely adopted by SaaS vendors as an operational security baseline. CSF 2.0 (published February 2024) structures controls across Govern, Identify, Protect, Detect, Respond, and Recover functions. Aligning the platform's security controls to NIST CSF 2.0 accelerates enterprise procurement reviews and provides a structured baseline for SOC 2 audit readiness.

**NIST Privacy Framework 1.0**
- URL: https://www.nist.gov/privacy-framework
- Complements the Cybersecurity Framework with a focus on personal data management. Directly applicable to a performance management platform holding employee evaluation data, ratings, compensation linkages, and 360 feedback. Guides data minimisation, purpose limitation, consent management, and subject rights fulfilment (GDPR right-of-access, right-to-erasure).

**GDPR (EU Regulation 2016/679) — Articles 5, 17, 22, 25**
- URL: https://gdpr-info.eu/
- Key provisions for a performance management platform: Article 5 (data minimisation and purpose limitation), Article 17 (right to erasure — performance records must be deletable on request), Article 22 (prohibition on solely automated decisions affecting employees — AI-generated performance scores require human review step), Article 25 (data protection by design and default). 360-degree feedback data constitutes personal data under GDPR; anonymity thresholds must be technically enforced. Any EU deployment requires a Data Processing Agreement (DPA).

**EU AI Act — Annex III, Employment High-Risk Systems**
- URL: https://artificialintelligenceact.eu/article/6/
- AI systems used for performance evaluation, task allocation, monitoring, promotion, or termination of workers are classified as "high-risk" under Annex III. High-risk obligations include: data governance for training datasets, technical documentation demonstrating compliance, human oversight mechanisms with meaningful override capability, accuracy and robustness testing, and conformity assessment. Mandatory compliance date is 2 August 2026 (potential deferral to December 2027 under the proposed Digital AI Omnibus, pending final adoption). Non-compliance penalties are up to €40M or 7% of global annual turnover. Any AI feature in the performance management platform (review narrative generation, bias detection, calibration pre-fill) that influences employment decisions in EU deployments must be documented as a high-risk AI system with a conformity assessment.

---

### MCP Server Specifications

The Model Context Protocol (MCP) is relevant to this platform for AI-native integrations. If the platform exposes an MCP server, AI assistants and agents (Claude, Copilot, Gemini) can access employee performance data, OKR status, and feedback history to support review writing, coaching conversation preparation, and goal alignment analysis.

- **MCP Specification**: https://modelcontextprotocol.io/specification
- Recommended MCP resources to expose: `employee_performance_summary`, `okr_progress`, `360_feedback_aggregate`, `calibration_distribution`. These allow AI assistants to draft performance reviews, generate manager talking points for 1-on-1 conversations, and identify at-risk employees — without requiring the AI to have direct database access.

---

## Similar Products — Developer Documentation & APIs

### Lattice

- **Description:** Comprehensive people management platform covering OKRs, performance reviews, 360 feedback, calibration, engagement surveys, and compensation.
- **API Documentation:** https://lattice.com/api
- **Help Center / Developer Guide:** https://help.lattice.com/hc/en-us/articles/360059449534-Lattice-s-Public-API
- **SDKs/Libraries:** No official SDK published; third-party unified HR API adapters available via Merge, Unified.to.
- **Standards:** REST/JSON; OAuth 2.0 for authentication; SCIM 2.0 for user provisioning.
- **Authentication:** OAuth 2.0.

### 15Five

- **Description:** Continuous performance platform with weekly check-ins, OKRs, 360 peer reviews, and manager effectiveness scoring.
- **API Documentation:** https://my.15five.com/api/public/
- **Help Center:** https://success.15five.com/hc/en-us/articles/360002699631-API
- **SDKs/Libraries:** No official SDK; REST/JSON API with API key authentication; integrations available via Zapier and Merge.
- **Standards:** REST/JSON; API key authentication (Basic Auth header).
- **Authentication:** API key via HTTP Basic Auth.

### Betterworks

- **Description:** Enterprise OKR and continuous performance management platform targeting organisations with 500+ employees.
- **API Documentation:** https://developers.betterworks.com/documentation/
- **Developer Portal:** https://developers.betterworks.com/
- **GitHub Docs:** https://betterworks.github.io/documentation/
- **SDKs/Libraries:** No official SDK; REST API with GET and POST support; Postman collection available.
- **Standards:** REST/JSON; API supports retrieval and update of goals, conversations, feedback, recognition, and calibration data.
- **Authentication:** API key with recommended X-Request-Id header per request for traceability.

### Culture Amp

- **Description:** Employee experience platform with world-class engagement surveys, performance reviews, OKRs, and DEI analytics.
- **API Documentation:** https://docs.api.cultureamp.com/docs/resources-getting-started
- **API Overview:** https://www.cultureamp.com/company/api
- **SDKs/Libraries:** No official SDK; OpenAPI Specification published; third-party adapters via Unified.to.
- **Standards:** REST/JSON; OpenAPI Specification available; OAuth 2.0 Client Credentials Flow; webhooks management API.
- **Authentication:** OAuth 2.0 Client Credentials Flow. Note: API currently supports outbound data retrieval only; data ingestion not supported as of 2026.

### Leapsome

- **Description:** Integrated European performance, engagement, and learning platform with strong GDPR compliance posture.
- **API Documentation (Swagger):** https://api.leapsome.com/v1/api-docs/
- **SCIM API (Swagger):** https://api.leapsome.com/scim/v1/api-docs/
- **Help Center:** https://help.leapsome.com/hc/en-us/articles/9251417820061-Content-API-Access-Reviews-Goals
- **SDKs/Libraries:** No official SDK; REST/JSON; SCIM 2.0 for user provisioning; Zapier integration for key result updates.
- **Standards:** REST/JSON; OpenAPI 3 (OAS3) specification published; SCIM 2.0 for user provisioning; supports GraphQL in some integrations.
- **Authentication:** API key; SCIM key separate from content API key.

### Profit.co

- **Description:** OKR-focused platform with deep OKR methodology support, task management, and performance reviews at mid-market price point.
- **API Documentation:** https://www.profit.dev/
- **Postman Collection:** https://www.postman.com/profitokrs
- **SDKs/Libraries:** No official SDK; Bubble.io plugin available; REST API with API key and access key pair.
- **Standards:** REST/JSON.
- **Authentication:** API key + Access key pair (obtained from Settings > Security > API Access).

### Workday HCM

- **Description:** Enterprise HCM suite with integrated performance management, goal management, and succession planning.
- **API Documentation:** https://community.workday.com/sites/default/files/file-hosting/productionapi/index.html
- **Integration Guide:** https://www.apideck.com/blog/create-a-workday-rest-api-integration
- **SDKs/Libraries:** No official SDK; third-party SDKs for Java, Python, and C# from the community; Workday Web Services (WWS) uses SOAP/WSDL for legacy integrations; REST API for newer endpoints.
- **Standards:** REST/JSON for modern endpoints; SOAP/WSDL (WWS) for legacy; OData patterns in some modules.
- **Authentication:** OAuth 2.0 required for REST API; API integration system user required for service account access.

### SAP SuccessFactors

- **Description:** Enterprise HCM suite with performance and goals module, widely used in global enterprises alongside SAP ERP.
- **API Documentation (OData V2):** https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/d599f15995d348a1b45ba5603e2aba9b/03e1fc3791684367a6a76a614a2916de.html
- **API Reference PDF (V2):** https://help.sap.com/doc/a7c08a422cc14e1eaaffee83610a981d/2511/en-US/SF_HCM_OData_API_DEV.pdf
- **OData V4 Guide:** https://help.sap.com/docs/SAP_SUCCESSFACTORS_PLATFORM/9f5f060351034d98990213d077dab38a/b96a4731870e48d090bfbe47b045d259.html
- **SDKs/Libraries:** SAP Business Technology Platform (BTP) SDKs; community-maintained Java and Python clients.
- **Standards:** OData V2 (primary) and OData V4 (newer endpoints); REST/JSON; published on SAP API Business Hub.
- **Authentication:** OAuth 2.0; SAML 2.0 for SSO; HTTP Basic Auth deprecated.

### BambooHR

- **Description:** HRIS platform widely used by SMBs and mid-market; primary employee roster data source for many performance management integrations.
- **API Documentation:** https://documentation.bamboohr.com/docs
- **API Reference:** https://documentation.bamboohr.com/reference
- **Official SDKs:** https://documentation.bamboohr.com/docs/sdks
- **Developer Guide:** https://www.getknit.dev/blog/how-to-get-employee-data-from-bamboohr-api
- **Standards:** REST/JSON; API key via HTTP Basic Auth; OAuth 2.0 for marketplace integrations (OIDC deprecated April 2025).
- **Authentication:** API key (HTTP Basic Auth for direct integrations); OAuth 2.0 authorization code flow for marketplace integrations.

### Unified HRIS APIs (Merge, Unified.to, Truto)

For a performance management platform, implementing direct integrations with each HRIS (BambooHR, Workday, Rippling, Gusto, Personio) is costly. Unified HRIS API providers abstract multiple HRIS platforms behind a single API:

- **Merge:** https://merge.dev/integrations/leapsome — provides unified REST API for HRIS, ATS, and performance data; supports Lattice, Leapsome, BambooHR, Workday, and 50+ others.
- **Unified.to:** https://unified.to/integrations — real-time unified API for HRIS; supports BambooHR, Culture Amp, Leapsome, Workday.
- **Truto:** https://truto.one — unified HRIS API platform; covers Workday, Gusto, Rippling with normalised schema.

Adopting a unified HRIS API layer early significantly reduces integration maintenance costs and accelerates enterprise deals where HRIS compatibility is a procurement criterion.

---

## Notes

**Emerging Standards to Watch**

- **ISO/FDIS 30201** (Human Resources Management Systems — Requirements): Currently in final draft stage under ISO/TC 260. Expected publication 2026–2027. May introduce formal requirements for performance management system data structures that affect API schema design.
- **EU Corporate Sustainability Reporting Directive (CSRD)**: Mandates human capital reporting (including workforce performance metrics) with third-party assurance for ~50,000 European companies. Performance management platforms serving EU enterprise customers should design exports aligned to CSRD disclosure requirements, which reference ISO 30414:2025 metrics.
- **EU Digital AI Omnibus**: Proposed amendment would defer EU AI Act high-risk employment AI obligations from August 2026 to December 2027. Status pending; platform should plan for August 2026 compliance as the safe baseline.
- **OpenID Connect for Identity Assurance 1.0**: Extends OIDC with verified claims (e.g., verified legal name, verified employment status). Relevant if the platform eventually supports employment verification workflows tied to performance history.
