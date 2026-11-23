🛡️ PENETRATION TESTING REPORT

Mediroza General Hospital | Week 4 | Batch B084


👤 Author Details

- Name: Relebogile Majatladi
- LinkedIn: https://www.linkedin.com/in/bethuel-ntsetse-majatladi-48a62524a?utm_source=share_via&utm_content=profile&utm_medium=member_android
- Role: Cybersecurity Intern
- Program: Networkwalks Academy
- Task Batch: B084
- Client: Mediroza General Hospital
- Target: https://medirozahospital.com
- Assessment Type: Black-Box Penetration Testing & Vulnerability Assessment
- Purpose: Educational / Controlled Environment

---

📌 1. Executive Summary

This project documents the Week 4 penetration testing assessment conducted against the Mediroza General Hospital web application in an authorized educational environment.

The assessment focused on identifying security weaknesses and understanding how multiple vulnerabilities could be chained together to expose sensitive information.

The reported findings included:

- Username enumeration.
- SQL injection and authentication bypass.
- Access to encrypted patient reports.
- Weak PDF password protection.
- Sensitive document metadata exposure.
- Exposed backup directories.
- Publicly accessible legacy database backups.

The most significant concern was the exposure of a legacy database backup containing employee salary and shareholder records.

Overall Risk Level: CRITICAL

The findings demonstrate the importance of strong authentication, secure document storage, database protection and proper server configuration.

🎯 2. Scope and Methodology

Target and Rules of Engagement

Testing was restricted to:

- Target: "https://medirozahospital.com"
- Assessment: Black-box penetration testing.
- Environment: Authorized educational testing environment.

The assessment excluded:

- Social engineering.
- Denial-of-service attacks.
- Unauthorized access to unrelated systems.
- Activities outside the approved scope.

Methodology and Tools

The following techniques and tools were used during the assessment:

Phase| Tools / Techniques
Reconnaissance| WHOIS, Nmap, Zenmap
Web Inspection| cURL, robots.txt
Authentication Testing| Login and username enumeration testing
Vulnerability Testing| SQL injection testing
Post-Exploitation Analysis| Password dictionary testing
Metadata Inspection| ExifTool
Server Exposure Review| Directory and backup inspection
Remediation| Security recommendations and defensive controls

🔍 3. Findings and Proof of Exploitation

The assessment identified seven reported security findings.

No.| Vulnerability| Risk
1| Username Enumeration| 🟠 Medium
2| SQL Injection and Authentication Bypass| 🔴 Critical
3| Unauthorized Access to Encrypted Patient Reports| 🔴 High
4| Weak PDF Passwords| 🔴 High
5| Sensitive PDF Metadata Exposure| 🟠 Medium
6| Exposed Backup Directory| 🔴 Critical
7| Exposed Database Backup| 🔴 Critical

3.1 Username Enumeration

Location: "patient/login.php"

Risk: Medium

The login page reportedly returned different responses depending on whether a username existed.

This could allow an attacker to identify valid usernames.

Recommendation:

- Use generic login error messages.
- Implement rate limiting.
- Monitor repeated login attempts.

3.2 SQL Injection and Authentication Bypass

Location: "patient/login.php"

Risk: Critical

SQL injection testing reportedly identified weaknesses in the login functionality, including authentication bypass and verbose SQL syntax error disclosure.

Recommendation:

- Implement prepared statements.
- Use parameterized SQL queries.
- Validate user input.
- Disable detailed database error messages in production.

3.3 Access to Encrypted Patient Reports

Location: "patient/portal.php" and "patient/reports/"

Risk: High

Following the reported authentication bypass, three encrypted pathology PDF reports were accessible.

Reports identified:

- S. Dlamini
- P. Reddy
- E. Thompson

This demonstrated weaknesses in document access controls.

Recommendation:

- Enforce server-side authorization.
- Restrict access to sensitive patient documents.
- Store reports outside publicly accessible directories.

3.4 Weak PDF Password Protection

Location: Patient report PDFs

Risk: High

Dictionary-based password testing reportedly recovered weak passwords.

Examples included:

- "123456"
- "password"
- "!@#$%^&"

Weak passwords reduce the protection offered by encrypted documents.

Recommendation:

- Use strong, randomly generated passwords.
- Apply modern encryption.
- Avoid relying on PDF passwords as the only security control.

3.5 Sensitive PDF Metadata Exposure

Location: Decrypted PDF documents

Risk: Medium

ExifTool was used to inspect document metadata.

The reported findings included:

- Author: "j.malik"
- Comments referencing an "/old" backup location.

This information could reveal useful internal details.

Recommendation:

- Remove unnecessary metadata before document distribution.
- Review document-generation processes.
- Avoid exposing internal server paths.

3.6 Exposed Backup Directory

Location: "/old/"

Risk: Critical

The backup directory reportedly allowed directory listing, potentially exposing files that were not intended for public access.

Recommendation:

- Disable directory listing.
- Restrict access to backup directories.
- Move sensitive backups outside the public web directory.

3.7 Exposed Database Backup

Location: "/old/mediroza_db_backup_2019.sql"

Risk: Critical

The reported database backup contained plaintext employee salary and shareholder records.

This created a serious confidentiality risk.

Recommendation:

- Remove publicly accessible database backups.
- Encrypt backup files.
- Restrict access to authorized administrators.
- Rotate exposed credentials where necessary.

---

⚠️ 4. Risk Assessment

Rating| Description
Critical| Could result in unauthorized access or exposure of highly sensitive records.
High| Could expose confidential documents or protected information.
Medium| Could reveal information useful for further attacks.
Low| Limited security impact.

Overall Risk: CRITICAL

The combination of authentication weaknesses, insufficient document protection and exposed backup resources represents a serious security concern.

🛠️ 5. Recommendations and Remediation

Authentication and Database Security

- Implement prepared statements and parameterized queries.
- Use secure password hashing.
- Apply account lockout and rate-limiting controls.
- Return generic authentication error messages.
- Review session-management mechanisms.

File Storage and Encryption

- Store sensitive reports outside public web directories.
- Enforce authorization checks for every document request.
- Use strong encryption.
- Review document-sharing permissions.

Metadata and Backup Security

- Remove unnecessary document metadata using ExifTool.
- Disable directory listing.
- Remove legacy backups from public web locations.
- Encrypt backups and enforce strict access controls.

Monitoring and Incident Response

- Monitor suspicious login attempts.
- Maintain access logs.
- Investigate potential unauthorized access.
- Conduct regular vulnerability assessments.
- Establish an incident response process.


🎓 6. Key Learning Outcomes

Through this assessment, I gained practical experience and improved my understanding of:

- Web application reconnaissance.
- Authentication vulnerabilities.
- SQL injection and authentication bypass.
- Document encryption and password security.
- Metadata inspection using ExifTool.
- Directory listing and server exposure.
- Database backup security.
- Vulnerability reporting and remediation.

📝 7. Conclusion

The Week 4 assessment demonstrated how individual security weaknesses can be chained together to create serious vulnerabilities within a web application.

The findings highlighted the importance of secure authentication, proper access controls, strong encryption and responsible data management.

This project strengthened my practical understanding of penetration testing and the importance of identifying vulnerabilities before they can be exploited.

Prepared by: Relebogile Majatladi
Cybersecurity Internship: Networkwalks Academy
Batch: B084

---

#Cybersecurity #PenetrationTesting #EthicalHacking #NetworkSecurity #CybersecurityInternship
