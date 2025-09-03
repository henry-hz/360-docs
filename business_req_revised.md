# Business Requirements (Revised)

> From now we are managing stories on the [airtable](https://airtable.com/appOIkgC41gZJX24F/tblD1sYYboWCNvDUv/viwnhpGu1c8tXkTYj)

## Passwords:
- cellcoin
- whatsapp business
- blip
- airtable
- clicksign
- make (if needed to integrate)

## Formas de pagamento:
- PIX
- boleto
- cartao de credito (somente nos acordos)

## Niveis de acesso de usuario (tela do sindico, com password proprio)

---

### Foco Exclusivo em Processos Financeiros:
Remoção de qualquer feature não relacionada a billing, cobrança, acordos ou relatórios financeiros (ex.: anúncios gerais, diretório comunitário, emergências, manutenção, reserva fund).

### Personas Atualizadas:
Inclusão do Time Jurídico (acesso na fase final para judicial/procurações); refinamento de papéis para 360 Capital (visão global de prédios como garantidora/credora), Administradoras (API para dados de consumo/bloqueio de acesso), Síndico (assinaturas/dashboard/notificações judiciais) e Moradores (boletos/QR Code/acordos/renegociações, com questionamentos direcionados).

### Esteira de Cobrança Detalhada:
Timings específicos: Reminder D-1 (antes vencimento); D+2 a D+20 (3 recados via WhatsApp para cobrar ativamente, focando atrasos 5-10 dias para maximizar multas: 2% multa + 10% honorários + 1% a.m. juros + IPCA correção); D+21 sugestão de acordos extrajudiciais (para evitar negativação); D+30 negativação (mais incisivo, explicando risco judicial); D+60 escalada para cobrança judicial (preferencialmente ações em massa por condomínio para maior força). Sem protesto nos primeiros 30 dias; inadimplência em acordos volta à esteira original.

### Acordos Extrajudiciais/Judiciais:
Máximo parcelamentos (sem descontos padrão); campo override para descontos apenas com autorização explícita do gestor da 360 Capital. Rewards alternativos (ex.: Vale-Bonus da CRMBonus ou equivalente) para pagamentos programados. Integração com ClickSign para assinatura eletrônica a partir de minutas padronizadas (preenchidas automaticamente com termos negociados). Se houver desconto vira diretamente da 360, sindicos e administradores nao podem dar descontos.

### Máquinas de Estado (FSMs):
Definidas para workflows de pagamento, cobranca e acordos, com transições baseadas em timings e lógica de inadimplência.

### Integrações:
WhatsApp Business API desde Phase 1 (prioridade sobre email, pois residentes preferem); Celcoin para automação de billing, geração de boletos, contas bancárias separadas (patrimônios separados por condomínio) e collection. ClickSign na Phase 2. API com administradoras para valores de consumo/bloqueio de acesso por inadimplência.

### Relatórios e Separações:
Todos os reports financeiros devem separar explicitamente despesa ordinária, juros, correção monetária (IPCA) e multas.

### Success Metrics:
Marcados como TBD (definir em D-1, sem valores fixos agora para flexibilidade).

### Não Funcionais:
Verificação de segurança/LGPD (consentimento explícito para dados via WhatsApp); cores da plataforma como TBD (a definir, mas sugerir palette azul/verde para vibe fintech confiável).

### Phases de Implementação:
Phase 1 como MVP minimalista (billing básico, reminders WhatsApp, sem judicial/acordos avançados); Phase 2 para features completas (acordos, judicial, acesso jurídico).

---

## Alterações Específicas por Seção da Versão 1.0

**Seção 1: Executive Summary:** Expandido para incluir papel da 360 Capital como garantidora, esteira timings e rewards. Justificativa: Alinha ao nosso modelo de negócio, evitando menções vagas a "modern channels".

**Seção 2: Scope/Objectives:** Adicionadas API administradoras, contas separadas, ações judiciais em massa, integrações Celcoin/ClickSign. Removidas referências a non-financeiro (ex.: resident satisfaction via community). Métricas TBD. Justificativa: Foco em escalabilidade e compliance; remoções evitam diluição.

**Seção 3: Personas:** Adicionado Time Jurídico (acesso fase 2 para judicial); refinados papéis existentes (ex.: Administradoras com API/bloqueio). Removidos Porteiro/Zelador/Contador (non-core). Justificativa: Reflete responsabilidades reais; jurídico essencial para judicial.

**Seção 4: User Stories:** Removidas US-008/009/012/016 (anúncios/info/overides – non-financeiro ou risco compliance). Adicionadas novas US para rewards/renegociações/API. Expandida US-030 com esteira timings/multas. Acceptance criteria mais detalhados (ex.: separação itens em reports). Justificativa: Evita overrides manuais; adiciona valor financeiro.

**Nova Seção 5: System Requirements (Workflows e FSMs):** Adicionada para estágios judiciais/extrajudiciais, input docs (regulamento, CPF/CNPJ, histórico inadimplência)

**Seção 6: Additional Features:** Removida inteira (non-financeiro: emergency, reserve, community, maintenance). Adicionadas rewards, ClickSign. Justificativa: Mantém escopo lean.

**Seção 7: Technical Requirements:** Adicionada LGPD, cores TBD. Justificativa: Compliance crítico.

**Seção 8: Implementation Phases:** Phase 1: WhatsApp/Celcoin MVP (billing/reminders básicos); Phase 2: Acordos/judicial, jurídico acesso. Removidas phases avançadas. Justificativa: Acelera MVP.

**Seção 9: Success Measurement:** TBD com placeholders. Justificativa: Flexibilidade.

---

## 1. Executive Summary

**Original Content (Version 1.0):**
> This document outlines the comprehensive business requirements for a condominium collection management system that automates billing, payment collection, and communication processes. The system will primarily interface with residents (condôminos) through WhatsApp chatbot integration, with email as the initial communication channel during Phase 1. The solution addresses the critical need for automated condominium fee collection in Brazil, reducing manual administrative work while improving payment compliance and resident satisfaction through modern communication channels.

**Remove:**
- The phrase "while improving payment compliance and resident satisfaction through modern communication channels" (too vague and non-specific to financial focus).

**Alter:**
- Replace "comprehensive business requirements" with "finalized business requirements tailored to financial processes".
- Change "with email as the initial communication channel during Phase 1" to "with WhatsApp Business API and email as the primary channel from Phase 1".
- Update the last sentence to "The solution addresses the critical need for automated condominium fee collection in Brazil, reducing manual administrative work and enhancing compliance as a credit guarantor."

**Include:**
- Add: "The system operates exclusively on financial processes, featuring a structured pipeline: D-1 reminders, D+2 to D+20 (three WhatsApp reminders targeting 5-10 day delays for maximum penalties: 2% fine + 10% fees + 1% p.m. interest + IPCA adjustment), D+21 extrajudicial agreement suggestions, D+30 negative listing (with judicial warning), and D+60 judicial escalation (mass actions per condominium). No standard discounts are offered (maximum installment plans; discount overrides require 360 Capital manager approval)."

**Revised Content (Version 2.0):**
> This document outlines the finalized business requirements tailored to financial processes for a condominium collection management system that automates billing, payment collection, and communication processes. The system will primarily interface with residents (condôminos) through WhatsApp chatbot integration, with WhatsApp Business API and email as the primary channel from Phase 1. The solution addresses the critical need for automated condominium fee collection in Brazil, reducing manual administrative work and enhancing compliance as a credit guarantor. The system operates exclusively on financial processes, featuring a structured pipeline: D-1 reminders, D+2 to D+20 (three WhatsApp reminders targeting 5-10 day delays for maximum penalties: 2% fine + 10% fees + 1% p.m. interest + IPCA adjustment), D+21 extrajudicial agreement suggestions, D+30 negative listing (with judicial warning), and D+60 judicial escalation (mass actions per condominium). No standard discounts are offered (maximum installment plans; discount overrides require 360 Capital manager approval).

---

## 2. Project Scope and Objectives

**Original Content (Version 1.0):**
> 2.1 Primary Objectives
> Automate billing and collection processes for condominium fees
> Reduce payment delinquency through proactive communication
> Streamline administration tasks for property managers
> Improve resident experience through modern communication channels
> Ensure regulatory compliance with Brazilian condominium laws
> Provide comprehensive financial reporting and analytics
> 2.2 Success Metrics
> Reduction in payment delinquency by 40%
> Decrease in administrative time by 60%
> Increase in first-attempt payment success by 35%
> Resident satisfaction score above 8.5/10

**Remove:**
- "Streamline administration tasks for property managers" (too broad, non-specific to financial automation).
- "Improve resident experience through modern communication channels" (vague, covered by pipeline).
- All success metrics (placeholders to be redefined as TBD).

**Alter:**
- In "Automate billing and collection processes for condominium fees", add "applying penalties/jurisdictional interest automatically".
- Change "Reduce payment delinquency through proactive communication" to "Reduce payment delinquency through a structured WhatsApp pipeline (D-1, D+2-20, D+21 agreements)".
- Update "Ensure regulatory compliance with Brazilian condominium laws" to "Ensure compliance with Brazilian condominium laws (e.g., Civil Code, Law 4.591/64) and LGPD (explicit data consent)".

**Include:**
- Add new objectives:
    - "Provide 360 Capital with global oversight as guarantor/creditor across multiple buildings."
    - "Integrate API with property management companies for consumption data and access blocking due to delinquency."
    - "Support mass judicial actions per condominium for leverage."
    - "Maintain separate bank accounts per condominium for financial security."
    - "Integrate with WhatsApp Business API (Phase 1), Celcoin (billing/boletos, Phase 1), and ClickSign (agreements, Phase 2)."
- Replace success metrics with: "TBD (to be defined with baseline data); placeholders: Delinquency reduction: 40%, Extrajudicial agreement success rate: 70%, Administrative time reduction: 60%, Payment rate for 5-10 day delays (with penalties): 60% of cases."

**Revised Content (Version 2.0):**
> 2.1 Primary Objectives
> - Automate billing and collection processes for condominium fees, applying penalties/jurisdictional interest automatically
> - Reduce payment delinquency through a structured WhatsApp pipeline (D-1, D+2-20, D+21 agreements)
> - Provide 360 Capital with global oversight as guarantor/creditor across multiple buildings
> - Integrate API with property management companies for consumption data and access blocking due to delinquency
> - Ensure compliance with Brazilian condominium laws (e.g., Civil Code, Law 4.591/64) and LGPD (explicit data consent)
> - Support mass judicial actions per condominium for leverage
> - Maintain separate bank accounts per condominium for financial security
> - Integrate with WhatsApp Business API (Phase 1), Celcoin (billing/boletos, Phase 1), and ClickSign (agreements, Phase 2)
>
> 2.2 Success Metrics
> TBD (to be defined with baseline data); placeholders: Delinquency reduction: 40%, Extrajudicial agreement success rate: 70%, Administrative time reduction: 60%, Payment rate for 5-10 day delays (with penalties): 60% of cases

---

## 3. User Personas and Roles

**Original Content (Version 1.0):**
> 3.1 Primary Users
> Condômino (Resident)
> Description: Property owner or tenant responsible for condominium fee payments
> Demographics: Adults aged 25-70, varying tech-savviness, smartphone users
> Pain Points: Forgotten payment dates, difficulty accessing payment methods, unclear fee breakdowns
> Goals: Easy payment process, clear communication, payment history access
> Síndico (Property Manager)
> Description: Elected or appointed individual responsible for condominium administration
> Demographics: Adults aged 35-65, moderate to high tech skills, time-constrained
> Pain Points: Manual collection tracking, difficult resident communication, complex reporting
> Goals: Automated processes, clear financial oversight, efficient problem resolution
> Administradora (Property Management Company)
> Description: Professional company managing multiple condominiums
> Demographics: Business professionals, high tech skills, efficiency-focused
> Pain Points: Managing multiple properties, standardization across buildings, scalability
> Goals: Centralized management, automated workflows, comprehensive reporting
> Porteiro/Zelador (Concierge/Caretaker)
> Description: On-site staff handling day-to-day operations
> Demographics: Adults aged 25-60, basic to moderate tech skills
> Pain Points: Resident inquiries about payments, lack of information access
> Goals: Quick access to resident payment status, simple interface
> Contador (Accountant)
> Description: Financial professional handling condominium accounting
> Demographics: Finance professionals, high attention to detail
> Pain Points: Manual reconciliation, complex reporting requirements
> Goals: Automated financial reports, easy reconciliation, audit trails
> 3.2 System Users
> 360Capital Operations Team
> Description: Internal team managing system operations and client support
> Goals: System monitoring, client success, issue resolution
> System Administrator
> Description: Technical team managing system configuration and maintenance
> Goals: System reliability, security, performance optimization

**Remove:**
- Entire "Porteiro/Zelador (Concierge/Caretaker)" persona (non-core to financial focus).
- Entire "Contador (Accountant)" persona (handled internally by 360 Capital).

**Alter:**
- For "Condômino (Resident)", update Goals to: "Easy payment process, access to boleto/QR Code Pix, request installments/renegotiations (1-to-1 review), view signed agreements, direct queries to property manager/company; if agreement defaults, revert to original pipeline."
- For "Síndico (Property Manager)", update Description to "Elected or appointed individual responsible for signing agreements/procurações and monitoring dashboard"; update Goals to: "Automated collection oversight, validate active procurações, receive D+60 judicial notifications, assist in collections."
- For "Administradora (Property Management Company)", update Description to "Professional company managing multiple condominiums, providing consumption data and access blocking via API"; update Goals to: "Centralized management, automated workflows, access agreement updates for ongoing collection."
- For "360Capital Operations Team", update Description to "Internal team managing system operations, credit analysis, and support as guarantor/creditor."

**Include:**
- Add new persona under 3.1 Primary Users: Legal Team Description: Attorneys/team handling judicial phase and procuration validation Demographics: Legal professionals, high attention to detail Pain Points: Manual document handling for judicial actions Goals: Access to procurações, 24-month delinquency history, CPF/CNPJ, support mass judicial actions per condominium (Phase 2 access)

**Revised Content (Version 2.0):**
> 3.1 Primary Users
> **Condômino (Resident)**
> - Description: Property owner or tenant responsible for condominium fee payments
> - Demographics: Adults aged 25-70, varying tech-savviness, smartphone users
> - Pain Points: Forgotten payment dates, difficulty accessing payment methods, unclear fee breakdowns
> - Goals: Easy payment process, access to boleto/QR Code Pix, request installments/renegotiations (1-to-1 review), view signed agreements, direct queries to property manager/company; if agreement defaults, revert to original pipeline
>
> **Síndico (Property Manager)**
> - Description: Elected or appointed individual responsible for signing agreements/procurações and monitoring dashboard
> - Demographics: Adults aged 35-65, moderate to high tech skills, time-constrained
> - Pain Points: Manual collection tracking, difficult resident communication, complex reporting
> - Goals: Automated collection oversight, validate active procurações, receive D+60 judicial notifications, assist in collections
>
> **Administradora (Property Management Company)**
> - Description: Professional company managing multiple condominiums, providing consumption data and access blocking via API
> - Demographics: Business professionals, high tech skills, efficiency-focused
> - Pain Points: Managing multiple properties, standardization across buildings, scalability
> - Goals: Centralized management, automated workflows, access agreement updates for ongoing collection
>
> **Legal Team**
> - Description: Attorneys/team handling judicial phase and procuration validation
> - Demographics: Legal professionals, high attention to detail
> - Pain Points: Manual document handling for judicial actions
> - Goals: Access to procurações, 24-month delinquency history, CPF/CNPJ, support mass judicial actions per condominium (Phase 2 access)
>
> 3.2 System Users
> **360Capital Operations Team**
> - Description: Internal team managing system operations, credit analysis, and support as guarantor/creditor
> - Goals: System monitoring, client success, issue resolution
>
> **System Administrator**
> - Description: Technical team managing system configuration and maintenance
> - Goals: System reliability, security, performance optimization

---

## 4. Detailed User Stories

**Original Content (Version 1.0):**
> 4.1 Resident (Condômino) Stories
> Payment Management
> US-001: View Current Balance
> As a resident
> I want to check my current balance and payment status
> So that I can understand what I owe and when payments are due
> Acceptance Criteria:
> Display current month balance
> Show overdue amounts with penalties
> Present payment due date
> Include detailed fee breakdown
> Show payment history for last 12 months

**Remove:**
- Entire "View Building Announcements" (US-008) and "Access Building Financial Information" (US-009) under Resident Stories (non-financial).
- Any mention of manual overrides or non-financial features from other stories (e.g., US-012 "Initiate Manual Collection Actions" under Property Manager Stories).

**Alter:**
- For US-001: View Current Balance, update Acceptance Criteria to: "Display current month balance; show overdue amounts; present due date; include detailed breakdown (ordinary/extraordinary/agreements); show 12-month history; accessible via WhatsApp link."
- For US-004: Request Payment Installments (assumed from v1.0 context), alter to: "As a resident, I want to request installments or renegotiations, so that I manage debts. Acceptance Criteria: Suggest agreements via WhatsApp at D+21 (maximum installments, no discounts by default); override discounts only with 360 Capital manager approval; 1-to-1 review; if defaulted, revert to original collection pipeline; sign via ClickSign (Phase 2)."

**Include:**
- Add new story under 4.1 Resident (Condômino) Stories: US-NOVA-001: Renegotiate Agreement As a resident I want to request extensions or renegotiations So that I can adjust payment terms Acceptance Criteria: Submit request via WhatsApp (D+21+); 1-to-1 review; if approved, update boletos automatically; if defaulted, apply penalties and escalate (D+30 negative, D+60 judicial) (Phase 2)
- Under 4.2 Property Manager (Síndico) Stories (assumed from v1.0 context), alter existing and add:
    - US-010: Monitor Dashboard As a property manager I want a dashboard for oversight So that I can track collection status Acceptance Criteria: Display per-resident stage tracking; D+60 judicial notifications; validate active procurações; generate reports with separated items (ordinary/interest/IPCA/fines) (Phase 1 basic; Phase 2 full)
- Remove US-011: Configure Collection Rules and US-012: Initiate Manual Collection Actions (avoid overrides, compliance risk).
- Add US-NOVA-002: Sign Legal Documents As a property manager I want to sign agreements and procurações So that collection can proceed Acceptance Criteria: Electronic signing via ClickSign; notify on judicial escalation; ensure procurações are valid (Phase 2)
- Under 4.3 360 Capital/Property Management Company Stories (new grouping for clarity), add:
    - US-NOVA-003: Integrate with Property Management Companies As a property management company I want API access So that I can share consumption data Acceptance Criteria: Send consumption values and blocking signals via API; receive agreement updates for ongoing collection (Phase 2)
    - US-NOVA-004: Access Judicial Features As a legal team I want access to legal documents So that I can handle judicial actions Acceptance Criteria: View/upload procurações, 24-month delinquency history, CPF/CNPJ; support mass actions per condominium (Phase 2)
- Under 4.4 System Automation Stories (new grouping), alter and add:
    - US-028: Automated Billing As the system I want to generate bills automatically So that processes are efficient Acceptance Criteria: Include ordinary, extraordinary, agreements, and separated penalties; send via WhatsApp; apply IPCA/interest post-30 days (Phase 1)
    - US-030: Collection Workflow Automation As the system I want automated collection So that delinquency is minimized Acceptance Criteria: Pipeline: D-1 reminder; D+2-20 (three WhatsApp reminders, focus penalties D+5-10); D+21 suggest agreement; D+30 negative listing (incisive, warn judicial); D+60 escalate judicial (mass actions); integrate ClickSign for agreements; if agreement defaults, revert to pipeline (Phase 1 basic; Phase 2 full)
    - US-033: Banking System Integration As the system I want banking integration So that payments are processed Acceptance Criteria: Use Celcoin for boletos, Pix, separate accounts per condominium; confirm payments in real-time (Phase 1)

**Revised Content (Version 2.0):**
> 4.1 Resident (Condômino) Stories
> **Payment Management**
>
> **US-001: View Current Balance**
> - As a resident
> - I want to check my current balance and payment status
> - So that I can understand what I owe and when payments are due
> - Acceptance Criteria:
>     - Display current month balance
>     - Show overdue amounts
>     - Present payment due date
>     - Include detailed breakdown (ordinary/extraordinary/agreements)
>     - Show payment history for last 12 months
>     - Accessible via WhatsApp link
>
> **US-004: Request Payment Installments**
> - As a resident
> - I want to request installments or renegotiations
> - So that I manage debts
> - Acceptance Criteria:
>     - Suggest agreements via WhatsApp at D+21 (maximum installments, no discounts by default)
>     - Override discounts only with 360 Capital manager approval
>     - 1-to-1 review
>     - If defaulted, revert to original collection pipeline
>     - Sign via ClickSign (Phase 2)
>
> **US-NOVA-001: Renegotiate Agreement**
> - As a resident
> - I want to request extensions or renegotiations
> - So that I can adjust payment terms
> - Acceptance Criteria:
>     - Submit request via WhatsApp (D+21+)
>     - 1-to-1 review
>     - If approved, update boletos automatically
>     - If defaulted, apply penalties and escalate (D+30 negative, D+60 judicial) (Phase 2)
>
> 4.2 Property Manager (Síndico) Stories
>
> **US-010: Monitor Dashboard**
> - As a property manager
> - I want a dashboard for oversight
> - So that I can track collection status
> - Acceptance Criteria:
>     - Display per-resident stage tracking
>     - D+60 judicial notifications
>     - Validate active procurações
>     - Generate reports with separated items (ordinary/interest/IPCA/fines) (Phase 1 basic; Phase 2 full)
>
> **US-NOVA-002: Sign Legal Documents**
> - As a property manager
> - I want to sign agreements and procurações
> - So that collection can proceed
> - Acceptance Criteria:
>     - Electronic signing via ClickSign
>     - Notify on judicial escalation
>     - Ensure procurações are valid (Phase 2)
>
> 4.3 360 Capital/Property Management Company Stories
>
> **US-NOVA-003: Integrate with Property Management Companies**
> - As a property management company
> - I want API access
> - So that I can share consumption data
> - Acceptance Criteria:
>     - Send consumption values and blocking signals via API
>     - Receive agreement updates for ongoing collection (Phase 2)
>
> **US-NOVA-004: Access Judicial Features**
> - As a legal team
> - I want access to legal documents
> - So that I can handle judicial actions
> - Acceptance Criteria:
>     - View/upload procurações, 24-month delinquency history, CPF/CNPJ
>     - Support mass actions per condominium (Phase 2)
>
> 4.4 System Automation Stories
>
> **US-028: Automated Billing**
> - As the system
> - I want to generate bills automatically
> - So that processes are efficient
> - Acceptance Criteria:
>     - Include ordinary, extraordinary, agreements, and separated penalties
>     - Send via WhatsApp
>     - Apply IPCA/interest post-30 days (Phase 1)
>
> **US-030: Collection Workflow Automation**
> - As the system
> - I want automated collection
> - So that delinquency is minimized
> - Acceptance Criteria:
>     - Pipeline: D-1 reminder
>     - D+2-20 (three WhatsApp reminders, focus penalties D+5-10)
>     - D+21 suggest agreement
>     - D+30 negative listing (incisive, warn judicial)
>     - D+60 escalate judicial (mass actions)
>     - Integrate ClickSign for agreements
>     - If agreement defaults, revert to pipeline (Phase 1 basic; Phase 2 full)
>
> **US-033: Banking System Integration**
> - As the system
> - I want banking integration
> - So that payments are processed
> - Acceptance Criteria:
>     - Use Celcoin for boletos, Pix, separate accounts per condominium
>     - Confirm payments in real-time (Phase 1)

---

## 5. System Requirements

**Original Content (Version 1.0):**
> [No specific content provided in truncated document]

**Remove:**
- Any implied non-financial requirements (e.g., community features, emergency systems).

**Alter:**
- [No alteration needed as section was empty; to be fully defined below.]

**Include:**
- Add new section: 5.1 Workflows and Stages
    - Extrajudicial Stages: Notification (D-1/D+2-20 WhatsApp reminders); Suggest Agreement (D+21, maximum installments); Negative Listing (D+30, incisive warning).
    - Judicial Stages: Escalate (D+60, mass actions per condominium, notify property manager/legal team for procurações).
    - Input for Credit Analysis: Internal regulations, CPF/CNPJ of debtors, 24-month delinquency history.
- State Machines (FSMs):
    - Payment FSM: [*] --> Pending --> Due (D-1 Reminder) --> Overdue (D+2 Reminder, 3 Messages until D+20) --> In_Agreement (D+21 Agreement Suggested) --> Defaulted (Missed Installment, Reverts to Collection, D+30 Negative) --> Paid (All Installments Paid or Full Payment with Penalties D+5-10: 2%+10%+1%p.m.+IPCA) --> Judicial (D+60 Escalation).
    - Collection FSM: [*] --> Notification (D-1/D+2-20 WhatsApp, Penalties D+5-10) --> Negative (D+30 Negative Listing, Incisive Warning) --> Negotiation (D+21 Agreement Suggested) --> Judicial (Failure by D+60, Mass Actions, Notify Legal/Property Manager) --> Resolved (Agreement Completed or Judicial Payment).
    - Agreement FSM: [*] --> Requested (Resident Request) --> Negotiating (1-to-1 Review, Discount Override by Manager Only) --> Signed (Approved, ClickSign) --> Active (First Installment) --> Defaulted (Missed Payment, Reverts to Collection D+30) --> Completed (All Paid).

**Revised Content (Version 2.0):**
> 5. System Requirements
> 5.1 Workflows and Stages
> - **Extrajudicial Stages:** Notification (D-1/D+2-20 WhatsApp reminders); Suggest Agreement (D+21, maximum installments); Negative Listing (D+30, incisive warning).
> - **Judicial Stages:** Escalate (D+60, mass actions per condominium, notify property manager/legal team for procurações).
> - **Input for Credit Analysis:** Internal regulations, CPF/CNPJ of debtors, 24-month delinquency history.
>
> 5.2 State Machines (FSMs):
> - **Payment FSM:** [*] --> Pending --> Due (D-1 Reminder) --> Overdue (D+2 Reminder, 3 Messages until D+20) --> In_Agreement (D+21 Agreement Suggested) --> Defaulted (Missed Installment, Reverts to Collection, D+30 Negative) --> Paid (All Installments Paid or Full Payment with Penalties D+5-10: 2%+10%+1%p.m.+IPCA) --> Judicial (D+60 Escalation).
> - **Collection FSM:** [*] --> Notification (D-1/D+2-20 WhatsApp, Penalties D+5-10) --> Negative (D+30 Negative Listing, Incisive Warning) --> Negotiation (D+21 Agreement Suggested) --> Judicial (Failure by D+60, Mass Actions, Notify Legal/Property Manager) --> Resolved (Agreement Completed or Judicial Payment).
> - **Agreement FSM:** [*] --> Requested (Resident Request) --> Negotiating (1-to-1 Review, Discount Override by Manager Only) --> Signed (Approved, ClickSign) --> Active (First Installment) --> Defaulted (Missed Payment, Reverts to Collection D+30) --> Completed (All Paid).

---

## 6. Additional Features

**Original Content (Version 1.0):**
> [No specific content provided in truncated document, but assumed from context: Emergency Communication System, Reserve Fund Management, Resident Community Features]

**Remove:**
- Entire "Emergency Communication System" (urgent notifications, security alerts, weather advisories).
- Entire "Reserve Fund Management" (automatic contributions, maintenance budgeting).
- Entire "Resident Community Features" (digital directory, maintenance requests).

**Alter:**
- [No alteration needed as section to be redefined below.]

**Include:**
- Add new content:
    - Agreements: Maximum installment plans; no standard discounts (discount override only with 360 Capital manager approval); standardized minutes via ClickSign (auto-filled with negotiated terms, e.g., payment schedule, installments).
    - Security and Compliance: LGPD compliance (explicit consent via WhatsApp, data anonymization, audit trails); platform colors TBD (suggest blue/green for fintech trust).

**Revised Content (Version 2.0):**
> 6. Additional Features
> - **Agreements:** Maximum installment plans; no standard discounts (discount override only with 360 Capital manager approval); standardized minutes via ClickSign (auto-filled with negotiated terms, e.g., payment schedule, installments).
> - **Security and Compliance:** LGPD compliance (explicit consent via WhatsApp, data anonymization, audit trails); platform colors TBD (suggest blue/green for fintech trust).

---

## 7. Non-Functional Requirements

**Original Content (Version 1.0):**
> [No specific content provided in truncated document]

**Remove:**
- Any implied non-financial performance metrics (e.g., community-related scalability).

**Alter:**
- [No alteration needed as section was empty; to be fully defined below.]

**Include:**
- Add new section:
    - Performance: System must handle 10,000+ users with <2s response time.
    - Security: LGPD-compliant (data encryption, consent logs).
    - Usability: Mobile-first, WhatsApp-centric UI.
    - Colors: TBD (suggest blue/green palette).

**Revised Content (Version 2.0):**
> 7. Non-Functional Requirements
> - **Performance:** System must handle 10,000+ users with <2s response time.
> - **Security:** LGPD-compliant (data encryption, consent logs).
> - **Usability:** Mobile-first, WhatsApp-centric UI.
> - **Colors:** TBD (suggest blue/green palette).

---

## 8. Implementation Phases

**Original Content (Version 1.0):**
> Phase 1: Email-Based MVP (Months 1-3)
> Core billing and collection functionality
> Email communication system
> Basic web dashboard for administrators
> Payment processing via PIX and boleto
> Phase 2: WhatsApp Integration (Months 4-6)
> WhatsApp Business API implementation
> Chatbot conversation flows
> Rich media support
> Migration from email to WhatsApp primary channel

**Remove:**
- Any mention of "Rich media support" (non-essential for MVP).

**Alter:**
- For Phase 1: Email-Based MVP, change to: "Core billing and collection functionality with WhatsApp Business API as primary channel, email secondary; basic web dashboard for administrators; payment processing via Pix and boleto using Celcoin."
- For Phase 2: WhatsApp Integration, update to: "Enhanced WhatsApp chatbot flows, agreement signing via ClickSign, judicial escalation (D+30/60), API with property managers, full dashboard, legal team access; complete migration to WhatsApp."

**Include:**
- Add: "Phase 1 excludes agreements and judicial features; Phase 2 includes mass judicial actions."

**Revised Content (Version 2.0):**
> 8. Implementation Phases
> **Phase 1: Email-Based MVP (Months 1-3)**
> - Core billing and collection functionality with WhatsApp Business API as primary channel, email secondary
> - Basic web dashboard for administrators
> - Payment processing via Pix and boleto using Celcoin
> - Phase 1 excludes agreements and judicial features
>
> **Phase 2: WhatsApp Integration (Months 4-6)**
> - Enhanced WhatsApp chatbot flows
> - Agreement signing via ClickSign
> - Judicial escalation (D+30/60)
> - API with property managers
> - Full dashboard
> - Legal team access
> - Complete migration to WhatsApp primary channel
> - Phase 2 includes mass judicial actions

---

## 9. Success Measurement

**Original Content (Version 1.0):**
> [No specific content provided in truncated document, assumed from context]

**Remove:**
- Any specific metric values (e.g., 40% reduction).

**Alter:**
- [No alteration needed as section to be redefined below.]

**Include:**
- Add new section: "TBD (to be defined with baseline data); track via KPIs such as penalty capture rate for 5-10 day delays, extrajudicial agreement success."

**Revised Content (Version 2.0):**
> 9. Success Measurement
> TBD (to be defined with baseline data); track via KPIs such as penalty capture rate for 5-10 day delays, extrajudicial agreement success
