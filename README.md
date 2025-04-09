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
  
![image](https://github.com/user-attachments/assets/16dd435c-063b-4807-9299-6614b660cbfa) *Figure 1: GoPhish admin login interface - First access point for campaign setup*

![image](https://github.com/user-attachments/assets/48c99824-46c5-42f3-bff2-e817aed5dcb7) *Figure 2: Mandatory password reset after initial admin login*

![image](https://github.com/user-attachments/assets/9fd59266-d78e-4f46-99c2-670c7b019fd5) *Figure 3: GoPhish admin dashboard - Central control panel for campaigns*

**Key Features Used**:  
- **Sending Profiles**: Configured Mailtrap as the SMTP relay.  
- **Landing Pages**: Hosted a fake bank login page to capture credentials.  
- **Email Templates**: Cloned real bank emails for realism.  

### **2.2 Mailtrap**  
**What It Does**:  
- Acts as a fake SMTP server to "catch" test emails.  
- Prevents accidental spam to real users during development.

![image](https://github.com/user-attachments/assets/337c77d1-bd79-4f34-85e3-3eddfd3b1536) *Figure 4: Creating a new sending profile in GoPhish*

![image](https://github.com/user-attachments/assets/9b064491-0a37-4534-90f7-eca5b5faeb0a) *Figure 5: Configuring Mailtrap SMTP credentials in GoPhish*

![image](https://github.com/user-attachments/assets/5df2d701-e337-4475-b486-b4cc088c21df) *Figure 6: Test email verification before campaign launch*

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

2. **Mailtrap Integration**:  
   - Used Mailtrap’s SMTP host/port to send test emails.  
   - Verified emails arrived in Mailtrap’s inbox (no real recipients).  

### **3.2 Execution**  
- Launched a test campaign to 1 user (self).  
- Monitored GoPhish dashboard for opens/clicks (partial data due to Mailtrap).

![image](https://github.com/user-attachments/assets/e8aebb2f-5027-4e94-b5ec-d5f92812a1e0) *Figure 7: Mailtrap inbox showing intercepted test email*

![image](https://github.com/user-attachments/assets/c29f9199-ba07-4238-a486-80c8d08e8ddf) *Figure 8: GoPhish confirmation of successful email dispatch*

![image](https://github.com/user-attachments/assets/f69a57fb-322f-4574-b20a-3b2cbfa83ee6) *Figure 9: Mailtrap email preview with headers and content*

### **3.3 Results**  
- **Emails Sent**: 1 (via Mailtrap).

![image](https://github.com/user-attachments/assets/2e498e80-a393-4799-b296-b118e39c248d) *Figure 10: Confirms email was sent*

- **Landing Page**: Displayed correctly when accessed.

![image](https://github.com/user-attachments/assets/b3a58690-6fed-460b-ae55-6366699b0005) *Figure 11: The actual email sent and it worked*

| Metric | Timestamp | Technical Data |
|--------|-----------|----------------|
| **Email Sent** | Apr 9 11:59:07 | SMTP successful delivery |
| **Email Opened** | Apr 9 11:59:13 | Tracking pixel triggered |
| **Link Clicked** | Apr 9 11:59:21 | {{.URL}} accessed |
| **Data Submitted** | Apr 9 11:59:25 | Credentials captured |

![image](https://github.com/user-attachments/assets/75b9c256-a2fc-4f40-bda7-02e9d3357a3f) *Figure 12: Gophish admin dashboard showing campaign management*

![image](https://github.com/user-attachments/assets/1ddaff85-0f1a-4d07-aa7c-9f1d9ce91ee9)

## ✅ Confirmed Results
- **Email successfully sent** from `parveemirah@gmail.com`  
- **Delivered** to target mailbox  
- **Tracking worked**: Opens/clicks recorded  
- **Credentials captured** via fake login page  

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

## ⚠️ Errors Encountered
| Issue | Solution |
|-------|----------|
| No opens recorded in Mailtrap | Mailtrap blocks tracking - use real SMTP for production tests |
| Form submissions not logged | Ensure form uses `action="{{.URL}}"` |
| Broken CSS in emails | Use inline styles in HTML templates |

---

## **5. Repository Files**  
- `/templates/bank_login.html`: Fake bank landing page.  
- `/templates/phishing_email.html`: Cloned bank email.  

---

## **6. Ethical & Legal Disclaimer**  
*This test was conducted for **educational purposes only**. Unauthorized phishing is illegal. Always obtain explicit consent before testing on users.*  
