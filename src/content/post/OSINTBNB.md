---
title: "OSINT BNB"
description: "This post is on OSINT BNB"
publishDate: "2025-4-15"
tags: [ "Assignment", "BNB", "Osint"]
---
## 1. Introduction

Open Source Intelligence (OSINT) is the process of collecting, analyzing and utilizing information from publicly availble sources to gain insights into a subject of interest. These sources include websites, social media platforms, public records, news articles, and more. The primary purpose of OSINT is to gather actionable intelligence without engaging in intrusive or illegal activities, making it a valuable tool in cybersecurity, competitive analysis, and investigative research.

Bhutan National Bank (BNB) is a  financial institution in Bhutan, established in 1997 and headquartered in Thimphu, the capital city with an initial funding of Nu. 2.5 million by the Royal Insurance Corporation of Bhutan. Over the years, BNB has played a pivotal role in the economic development of Bhutan by providing essential financial services and fostering financial inclusion.

 

The objective of this OSINT investigation is to systematically collect and analyze publicly available information about Bhutan National Bank to assess its digital footprint and identify potential security vulnerabilities.  This assessment aims to provide actionable insights and recommendations to enhance BNB's cybersecurity measures .

## 2. Methodology

This OSINT investigation on Bhutan National Bank (BNB) follows a structured approach to gathering, analyzing, and interpreting publicly available data. The methodology includes various sources, tools, and ethical considerations to ensure responsible information collection.

**Sources of Data Collection**

To gather relevant information, multiple publicly accessible sources were utilized, including:

- Search Engines – Google were used with Google Dorks to refine searches and extract hidden or indexed information.
- WHOIS Lookup – Conducted via nic.bt to obtain domain registration details, including ownership and hosting information.
- Shodan – Used to identify exposed services, open ports, and potential security misconfigurations in BNB’s online infrastructure.
- Have I Been Pwned – Checked for any leaked credentials associated with BNB or its employees in past data breaches.
- APK Decompiler – Used to analyze the security posture of the bank's mobile application, if available.
- Company Website & Job Listings – Reviewed for technical stack exposure, internal software usage, and security-related insights.
- Social Media & Public Documents – Investigated LinkedIn, Facebook, and financial reports for information on employees, stakeholders, and policies.

**Tools Used**

Various OSINT tools were employed to extract and analyze data, including:

- Shodan – To map the bank’s publicly exposed assets and open ports.
- Have I Been Pwned – To check for breached credentials related to BNB.
- Decompilers  – To inspect the bank’s mobile application for potential security weaknesses.
- nic.bt WHOIS Lookup – To retrieve domain information and hosting details.
- Google Dorks – To uncover hidden web pages and indexed sensitive information.
- nslookup – Used for DNS analysis and identifying IP addresses ..

### **Company Overview: Bhutan National Bank**

**General Details**:

- Company Name: Bhutan National Bank Limited (BNB)
- Registration: Established on July 25, 1980, as the Unit Trust of Bhutan (UTB); became an independent financial institution in 1992 and evolved into a commercial bank in 1997.
- Location: Headquartered in Thimphu, Bhutan.
- Business Model: Provides a comprehensive range of financial services, including personal and corporate banking, international banking, and digital banking solutions

**Official Website and Domain Information:**

- Official Website: https://bnb.bt/
- Domain Information: The domain `bnb.bt` is registered under the `.bt` country code top-level domain (ccTLD) for Bhutan. Specific WHOIS details are not available due to the lack of a public WHOIS server for `.bt` domains.
- SSL Certificate Details: The website employs HTTPS, indicating the use of an SSL certificate to secure data transmission.

### 4. Digital Footprint Analysis

### Website Analysis

- Subdomains: Checked for subdomains using nslookup but significant subdomains were found.

**Technology Stack:**

- CMS & Blog: WordPress
- Database: MySQL
- Programming Language: PHP
- JavaScript Library: jQuery
- Analytics & SEO: Google Analytics, Site Kit, Yoast SEO


### Network Infrastructure

**IP Address & Hosting Provider:**

- Found BNB’s IP using nslookup [bnb.bt](http://bnb.bt/), which resolved to 103.119.126.89.


- Hosting provider details were not publicly available through WHOIS and used [nic.bt](http://nic.bt/)

**Open Ports & Services:**

- Using Shodan, found open ports 433 and 8010, indicating exposed services that could be further examined for vulnerabilities.


The server is running:

- Apache HTTPD 2.4.41
- Ubuntu Linux
- TLS 1.3 with CHACHA20_POLY1305_SHA256 cipher suite



### Social Media & Employee Information

- Employee Data Collection and credential exposure :
    - Found an email linked to an IT department employee, Nima Gyeltshen, from nic.bt records .
    
 
    
    - Checked his email on HaveIBeenPwned, and it appeared in the following breaches:
        - Gravatar (2020)
        - 000webhost (2015)
        
    
        
    - Customer Service Email ([contact@bnb.bt](mailto:contact@bnb.bt)) was also checked but had no known breaches.
    

    

**Reverse Engineering Attempt:**

- Downloaded BNB’s APK file and attempted to decompile it using an online APK decompiler.





- No immediate security flaws or exposed API keys were found, but further static and dynamic analysis could reveal more insights.

**Security Headers Analysis:**

A security headers scan was performed to assess protection mechanisms against web-based attacks. 

The scan revealed missing essential security headers, including:



### Finacial statement

[Financials.pdf](attachment:9c6e0295-fe7c-41db-8d4c-133c4e5fbd9b:Financials.pdf)

site:bnb.bt filetype:pdf

• Highlights the financial health and operational performance of BAS Bank for 2022.

### Conclusion

This OSINT investigation of Bhutan National Bank (BNB) has revealed significant insights into its digital footprint and security posture. Through systematic analysis of public information, I identified several areas of concern: exposed services, potential data breaches, and vulnerabilities in the bank's technology stack. While BNB maintains  security measures—including HTTPS and SSL certification—several security gaps remain that could be exploited. Most notably, the presence of open ports and reliance on common technologies like WordPress and MySQL creates potential entry points for cyber threats. 

### **Recommendations**

1. Enhance Security Measures: BNB should perform a comprehensive security audit of its online systems, with particular attention to the exposed ports (433 and 8010). 
2. Regular Vulnerability Assessments: Establish a routine for conducting vulnerability assessments and penetration testing to identify and address potential weaknesses in the bank's digital assets. 
3. Employee Training and Awareness: Implement cybersecurity training sessions for employees, focusing on phishing detection and secure information handling. This  approach will minimize security breaches caused by human error(employers).
4. Monitor for Data Breaches: Continuously monitor platforms like "Have I Been Pwned" for any leaked credentials associated with BNB or its employees.
5. Review and Update Technology Stack: Evaluate current software components for outdated or unsupported elements. Upgrade to more secure alternatives and add protection measures against known vulnerabilities.