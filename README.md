# GoPhish Email Security Testing Report  
*Simulated phishing campaign to evaluate email security awareness and system vulnerabilities.*  

---

## **1. Introduction**  
### **Purpose**  
This project demonstrates how **GoPhish** (a phishing framework) and **Mailtrap** (an email testing tool) can be used to:  
- Test organizational vulnerability to phishing attacks.  
- Train users to identify malicious emails.  
- Evaluate email security configurations.  

### **Tools Overview**  
| Tool       | Purpose                                                                 | Role in This Test                          |  
|------------|-------------------------------------------------------------------------|--------------------------------------------|  
| **GoPhish** | Open-source phishing toolkit for simulating attacks.                    | Created fake bank emails/login pages.      |  
| **Mailtrap** | Email sandbox for testing SMTP/email delivery (no real emails sent).    | Simulated email sending for safe testing.  |  

---

## **2. Tool Breakdown**  
### **2.1 GoPhish**  
**What It Does**:  
- Designs phishing campaigns (emails + landing pages).  
- Tracks user interactions (email opens, link clicks, form submissions).  
- Generates reports on campaign success rates.
![image](https://github.com/user-attachments/assets/16dd435c-063b-4807-9299-6614b660cbfa)
![image](https://github.com/user-attachments/assets/48c99824-46c5-42f3-bff2-e817aed5dcb7)

**Key Features Used**:  
- **Sending Profiles**: Configured Mailtrap as the SMTP relay.  
- **Landing Pages**: Hosted a fake bank login page to capture credentials.  
- **Email Templates**: Cloned real bank emails for realism.  

### **2.2 Mailtrap**  
**What It Does**:  
- Acts as a fake SMTP server to "catch" test emails.  
- Prevents accidental spam to real users during development.
![image](https://github.com/user-attachments/assets/cb0864d4-0e70-4ff0-b4cb-a3715e8fdec7)

**Limitations in This Test**:  
- **No real email delivery**: Cannot track opens/clicks accurately.  
- **Sandboxed environment**: Blocks GoPhish tracking pixels/form submissions.  

---

## **3. Methodology**  
### **3.1 Setup**  
1. **GoPhish Configuration**:  
   - Created a sending profile with Mailtrap’s SMTP credentials.  
   - Designed a bank-themed email template with `{{.URL}}` for tracking.  
   - Built a landing page with `action="{{.URL}}"` to capture credentials.  

   ![](media/image4.png) *Sending profile setup in GoPhish*  

2. **Mailtrap Integration**:  
   - Used Mailtrap’s SMTP host/port to send test emails.  
   - Verified emails arrived in Mailtrap’s inbox (no real recipients).  

   ![](media/image9.png) *Email preview in Mailtrap*  

### **3.2 Execution**  
- Launched a test campaign to 1 user (self).  
- Monitored GoPhish dashboard for opens/clicks (partial data due to Mailtrap).  

   ![](media/image14.png) *GoPhish dashboard showing sent emails*  

### **3.3 Results**  
- **Emails Sent**: 1 (via Mailtrap).  
- **Landing Page**: Displayed correctly when accessed.  
- **Data Captured**: Credentials submitted to GoPhish (if tested outside Mailtrap).  

---

## **4. Key Takeaways**  
### **GoPhish Strengths**  
✅ Realistic phishing simulations.  
✅ Detailed tracking (with real SMTP).  

### **Mailtrap Limitations**  
❌ **No real tracking**: Cannot replace actual SMTP for phishing tests.  
❌ **Sandbox restrictions**: Blocks GoPhish’s tracking functionality.  

### **Recommendations**  
- **For accurate testing**: Use a real SMTP service (e.g., SendGrid, Gmail).  
- **For training**: Combine GoPhish with user education programs.  

---

## **5. Repository Files**  
- `/templates/bank_login.html`: Fake bank landing page.  
- `/templates/phishing_email.html`: Cloned bank email.  
- `/media/`: Screenshots of setup/results.  

---

## **6. Ethical & Legal Disclaimer**  
*This test was conducted for **educational purposes only**. Unauthorized phishing is illegal. Always obtain explicit consent before testing on users.*  
