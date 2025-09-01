# Lovable AI Prompt: Condominium Collection Management MVP

Build a **Brazilian condominium billing and collection management web application** with the following specifications:

## Core Features (Phase 1 - Email MVP)

### User Roles
- **Residents** (condôminos): View bills, make payments, check history
- **Property Managers** (síndicos): Dashboard, collection monitoring, reports
- **Admins**: System configuration, multi-building management

### Key Functionality

**For Residents:**
- Login with unit number + email
- Dashboard showing current balance, due dates, payment history
- Generate PIX payment codes and boleto downloads
- View detailed fee breakdowns with penalties (2% fine, 10% collection fees after D+1)
- Email notifications for payment reminders and confirmations

**For Property Managers:**
- Collection dashboard with payment status overview (paid/pending/overdue)
- Automated billing generation (D-5 schedule, due on 1st of month)
- Configure penalty rules and collection parameters per building
- Financial reports and monthly summaries
- Send announcements to all residents via email

**For Admins:**
- Multi-building management interface
- User management and permissions
- System configuration and monitoring

### Technical Requirements
- **Frontend:** Modern React/Next.js with responsive design
- **Backend:** Node.js/Express with PostgreSQL database
- **Payment Integration:** PIX payment code generation and boleto creation APIs
- **Email Service:** Automated email sending for notifications and billing
- **Authentication:** JWT-based auth with role-based access control

### Brazilian-Specific Features
- Brazilian CPF/CNPJ validation
- Real currency formatting and calculations
- Portuguese language interface
- IPCA inflation index integration for monetary correction
- Brazilian date formats and holiday calendar

### Automated Collection Flow
- D-5: Generate and email bills automatically
- D-1: Payment reminder emails
- D+2, D+7, D+10: Overdue notice emails with updated penalties
- D+25: Final notice before legal action
- D+30: Flag for extrajudicial agreement

### Database Schema
- Buildings, Units, Residents, Bills, Payments, Notifications
- Financial tracking with penalty calculations
- Audit trails for all transactions

Create a **clean, professional interface** with **dashboard-style layouts**, **Brazilian color scheme**, and **mobile-responsive design**. Include sample data for demonstration.