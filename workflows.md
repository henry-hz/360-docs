## Workflows and Stages

### Extrajudicial Stages
- **Notification:** D-1/D+2-20 WhatsApp reminders
- **Suggest Agreement:** D+21, maximum installments
- **Negative Listing:** D+30, incisive warning

### Judicial Stages
- **Escalate:** D+60, mass actions per condominium, notify property manager/legal team for procurações

### Input for Credit Analysis
- Internal regulations
- CPF/CNPJ of debtors
- 24-month delinquency history

### Payment FSM
- `[*] --> Pending`
- `Pending --> Due` (D-1 Reminder)
- `Due --> Overdue` (D+2 Reminder, 3 Messages until D+20)
- `Overdue --> In_Agreement` (D+21 Agreement Suggested)
- `In_Agreement --> Defaulted` (Missed Installment, Reverts to Collection, D+30 Negative)
- `Defaulted --> Paid` (All Installments Paid or Full Payment with Penalties D+5-10: 2%+10%+1%p.m.+IPCA)
- `Paid --> [*]`
- `Defaulted --> Judicial` (D+60 Escalation)

### Collection FSM
- `[*] --> Notification` (D-1/D+2-20 WhatsApp, Penalties D+5-10)
- `Notification --> Negative` (D+30 Negative Listing, Incisive Warning)
- `Negative --> Negotiation` (D+21 Agreement Suggested)
- `Negotiation --> Judicial` (Failure by D+60, Mass Actions, Notify Legal/Property Manager)
- `Judicial --> Resolved` (Agreement Completed or Judicial Payment)
- `Resolved --> [*]`

### Agreement FSM
- `[*] --> Requested` (Resident Request)
- `Requested --> Negotiating` (1-to-1 Review, Discount Override by Manager Only)
- `Negotiating --> Signed` (Approved, ClickSign)
- `Signed --> Active` (First Installment)
- `Active --> Defaulted` (Missed Payment, Reverts to Collection D+30)
- `Active --> Completed` (All Paid)
- `Completed --> [*]`
