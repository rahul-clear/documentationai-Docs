# Documentation.AI Migration Setup

## 1. Clone your repo

```bash
git clone https://github.com/rahul-clear/documentationai-Docs.git
cd documentationai-Docs
```

## 2. Create the folder structure

```bash
mkdir -p e-invoicing-ksa/api-reference
mkdir -p e-invoicing-ksa/guides
mkdir -p e-invoicing-oman
mkdir -p e-invoicing-qatar
```

## 3. Create documentation.json (site nav config)

```bash
cat > documentation.json << 'EOF'
{
  "name": "ClearTax Global E-Invoicing",
  "initialRoute": "e-invoicing-ksa/overview",
  "navigation": {
    "tabs": [
      {
        "tab": "Documentation",
        "groups": [
          {
            "group": "E-Invoicing KSA",
            "icon": "file-text",
            "pages": [
              {
                "title": "Overview",
                "path": "e-invoicing-ksa/overview"
              },
              {
                "title": "Code Lists",
                "path": "e-invoicing-ksa/api-reference/code-lists"
              }
            ]
          },
          {
            "group": "E-Invoicing Oman",
            "icon": "file-text",
            "pages": [
              {
                "title": "Overview",
                "path": "e-invoicing-oman/overview"
              }
            ]
          },
          {
            "group": "E-Invoicing Qatar",
            "icon": "file-text",
            "pages": [
              {
                "title": "Overview",
                "path": "e-invoicing-qatar/overview"
              }
            ]
          }
        ]
      }
    ]
  }
}
EOF
```

## 4. Create the KSA overview page

```bash
cat > e-invoicing-ksa/overview.mdx << 'EOF'
---
title: "E-Invoicing KSA"
description: "ClearTax ZATCA Phase 2 e-invoicing integration guide for Saudi Arabia"
---

## Overview

ClearTax provides a complete ZATCA-compliant e-invoicing solution for Saudi Arabia, covering both simplified and standard tax invoices under Phase 2 (Integration Phase).

<Callout kind="info">
This documentation covers the ClearTax API for generating, validating, and reporting e-invoices to ZATCA.
</Callout>

## Getting Started

<Steps>
  <Step title="Get API credentials" icon="key">
    Contact ClearTax support to obtain your sandbox API key and ZATCA integration credentials.
  </Step>

  <Step title="Configure your tax profile" icon="settings">
    Set up your seller details, VAT registration number, and device information in the ClearTax dashboard.
  </Step>

  <Step title="Generate your first invoice" icon="zap">
    Use the invoice generation API to create and report your first e-invoice to ZATCA.
  </Step>
</Steps>

## Key Resources

<Columns cols="2">
  <Card title="API Reference" href="/e-invoicing-ksa/api-reference/code-lists" icon="code">
    Endpoints, parameters, and response formats for the KSA e-invoicing API.
  </Card>

  <Card title="Code Lists" href="/e-invoicing-ksa/api-reference/code-lists" icon="list">
    VAT category codes, UOM codes, payment means, and party identification codes.
  </Card>
</Columns>
EOF
```

## 5. Create the Code Lists page (migrated from GitBook)

```bash
cat > e-invoicing-ksa/api-reference/code-lists.mdx << 'EOF'
---
title: "Code Lists"
description: "VAT category codes, unit of measure codes, payment means, and party identification codes for ZATCA e-invoicing"
---

## Unit of Measure

Codes for Units of Measure used in international trade — Revision 16 (UNECE/CEFACT Trade Facilitation Recommendation No.20).

Please refer to Annexes I, II, and III in the UNECE Recommendation No.20 document.

<Callout kind="info">
The full list of UOMs supported by ClearTax for e-invoice generation is inline with UN/ECE standard codes for Units of Measure used in international trade. Contact support if you need a UOM code not listed in the standard set.
</Callout>

## VAT Categories Code

A subset of values from [UN/CEFACT code list 5305, D.16B](https://www.unece.org/fileadmin/DAM/trade/untdid/d16b/tred/tred5305.htm) shall be used.

The valid values for KSA are listed in the table below:

| Code | Description | Tax Exemption Reason Code | Tax Exemption Reason (EN) | Tax Exemption Reason (AR) |
|------|-------------|--------------------------|---------------------------|---------------------------|
| S | Standard rate | NA | NA | NA |
| E | Exempt from Tax | VATEX-SA-29 | Financial services mentioned in Article 29 of the VAT Regulations. | الخدمات المالية |
| E | Exempt from Tax | VATEX-SA-29-7 | Life insurance services mentioned in Article 29 of the VAT Regulations. | عقد تأمين على الحياة |
| E | Exempt from Tax | VATEX-SA-30 | Real estate transactions mentioned in Article 30 of the VAT Regulations. | التوريدات العقارية المعفاة من الضريبة |
| Z | Zero rated goods | VATEX-SA-32 | Export of goods. | صادرات السلع من المملكة |
| Z | Zero rated goods | VATEX-SA-33 | Export of services. | صادرات الخدمات من المملكة |
| Z | Zero rated goods | VATEX-SA-34-1 | The international transport of Goods. | النقل الدولي للسلع |
| Z | Zero rated goods | VATEX-SA-34-2 | International transport of passengers. | النقل الدولي للركاب |
| Z | Zero rated goods | VATEX-SA-34-3 | Services directly connected and incidental to a Supply of international passenger transport. | الخدمات المرتبطة مباشرة أو عرضياً بتوريد النقل الدولي للركاب |
| Z | Zero rated goods | VATEX-SA-34-4 | Supply of a qualifying means of transport. | توريد وسائل النقل المؤهلة |
| Z | Zero rated goods | VATEX-SA-34-5 | Any services relating to Goods or passenger transportation, as defined in article 25 of these Regulations. | الخدمات ذات الصلة بنقل السلع أو الركاب |
| Z | Zero rated goods | VATEX-SA-35 | Medicines and medical equipment. | الأدوية والمعدات الطبية |
| Z | Zero rated goods | VATEX-SA-36 | Qualifying metals. | المعادن المؤهلة |
| Z | Zero rated goods | VATEX-SA-EDU | Private education to citizen. | الخدمات التعليمية الخاصة للمواطنين |
| Z | Zero rated goods | VATEX-SA-HEA | Private healthcare to citizen. | الخدمات الصحية الخاصة للمواطنين |
| Z | Zero rated goods | VATEX-SA-MLTRY | Supply of qualified military goods. | توريد السلع العسكرية المؤهلة |
| Z | Zero rated goods | VATEX-SA-ROYALDECREE | Supply on which the Government bears the VAT. | العرض الذي تتحمل الحكومة ضريبة القيمة المضافة عليه |
| Z | Zero rated goods | VATEX-SA-32(bis) | Supply under Customs Suspension Arrangement. | التوريد بموجب ترتيب تعليق الجمارك |
| O | Not subject to VAT | VATEX-SA-OOS | Free text reason provided by the taxpayer on a case-by-case basis. | السبب يتم تزويده من قبل المكلف على أساس كل حالة على حدة |

## Payment Means Type Code

A subset of values from [UN/CEFACT code list 4461, D.16B](https://www.unece.org/fileadmin/DAM/trade/untdid/d16b/tred/tred4461.htm) shall be used for the payment means code.

| Code | Description |
|------|-------------|
| 10 | Cash |
| 30 | Credit transfer |
| 42 | Payment to bank account |
| 48 | Bank card |
| 1 | Not defined |

## Reason for Allowances in an Invoice

A subset of values from [UNTDID 5189 Code List](https://unece.org/fileadmin/DAM/trade/untdid/d16b/tred/tred5189.htm) shall be used.

| Code | Description |
|------|-------------|
| 41 | Bonus for works ahead of schedule |
| 42 | Other bonus |
| 60 | Manufacturer's consumer discount |
| 62 | Due to military status |
| 63 | Due to work accident |
| 64 | Special agreement |
| 65 | Production error discount |
| 66 | New outlet discount |
| 67 | Sample discount |
| 68 | End-of-range discount |
| 70 | Incoterm discount |
| 71 | Point of sales threshold allowance |
| 88 | Material surcharge/deduction |
| 95 | Discount |
| 100 | Special rebate |
| 102 | Fixed long term |
| 103 | Temporary |
| 104 | Standard |
| 105 | Yearly turnover |

## Reason for Charges in an Invoice

A subset of values from [UNTDID 7161 Code List](https://unece.org/fileadmin/DAM/trade/untdid/d16b/tred/tred7161.htm) shall be used.

| Code | Description |
|------|-------------|
| AA | Advertising |
| AAA | Telecommunication |
| ABK | Miscellaneous |
| ABL | Additional packaging |
| ADR | Other services |
| ADT | Pick-up |
| FC | Freight service |
| FI | Financing |
| LA | Labelling |
| PC | Packing |

## Seller Party Identification Code

| Code | Description |
|------|-------------|
| CRN | Commercial registration number |
| MOM | Momra license |
| MLS | MLSD license |
| SAG | Sagia license |
| OTH | Other ID |

## Buyer Party Identification Code

| Code | Description |
|------|-------------|
| NAT | National ID |
| TIN | Tax Identification Number |
| IQA | Iqama Number |
| PAS | Passport ID |
| CRN | Commercial registration number |
| MOM | Momra license |
| MLS | MLSD license |
| SAG | Sagia license |
| GCC | GCC ID |
| OTH | Other ID |
EOF
```

## 6. Create placeholder pages for Oman and Qatar

```bash
cat > e-invoicing-oman/overview.mdx << 'EOF'
---
title: "E-Invoicing Oman"
description: "ClearTax Fawtara e-invoicing integration guide for Oman"
---

## Overview

ClearTax provides Fawtara-compliant e-invoicing for the Sultanate of Oman, supporting both B2B and B2C invoice types under the OTA mandate.

<Callout kind="alert">
The OTA onboarding deadline is August 2026. Ensure your integration is ready before the cutoff.
</Callout>

## Coming Soon

Documentation for Oman e-invoicing is being migrated. Check back shortly.
EOF

cat > e-invoicing-qatar/overview.mdx << 'EOF'
---
title: "E-Invoicing Qatar"
description: "ClearTax GTA e-invoicing integration guide for Qatar"
---

## Overview

ClearTax supports Qatar's GTA e-invoicing framework, covering device onboarding, certificate management, and invoice reporting.

## Coming Soon

Documentation for Qatar e-invoicing is being migrated. Check back shortly.
EOF
```

## 7. Commit and push

```bash
git add .
git commit -m "Initial migration: KSA code lists, overview pages for KSA/Oman/Qatar"
git push origin main
```

## 8. Verify

Open your live site at `https://clear.documentationai.com` and check:
- Sidebar navigation shows all three market sections
- KSA Code Lists page renders with all tables and Arabic text
- Overview pages render with Callout and Steps components

## 9. Set up Claude Code for bulk migration (optional)

```bash
# Add Documentation.AI MCP servers
claude mcp add --transport http documentation-ai https://documentation.ai/docs/_mcp
claude mcp add --transport http cleartax-docs https://clear.documentationai.com/_mcp

# Restart Claude Code
# Then use it to batch-convert remaining GitBook pages
```
