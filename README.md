# **Advanced Automated System for Domain and Subdomain Security Analysis and Reporting**

![Screenshot 2025-07-23 113826](https://github.com/user-attachments/assets/92ceea46-397a-4694-83e9-a03ff543f198)

## **Abstract**

The exponential growth of cyber threats targeting web infrastructure necessitates robust, scalable, and automated solutions for domain reconnaissance and security assessment. This paper presents the design and implementation of a comprehensive system for domain and subdomain analysis integrating DNS enumeration, SSL/TLS inspection, HTTP header compliance validation, and security intelligence aggregation. Built using Python and supported by a GUI (Tkinter) and executive-level HTML reporting, this tool enables cybersecurity professionals to perform in-depth security assessments and generate visual, shareable reports.

---

## **1. Introduction**

Domain infrastructure is a prime target for cyberattacks, often exploited through weakly configured subdomains, insecure headers, or outdated SSL certificates. While several tools exist for partial assessments, there is a lack of integrated, extensible systems that offer full-stack domain analysis with visualization and automation.

This research introduces a modular system that automates:

* Subdomain discovery via multiple intelligence sources
* DNS and port-level reconnaissance
* SSL and security header grading
* Real-time GUI-based analytics
* Executive-grade HTML reporting

---

## **2. Related Work**

Tools like **Sublist3r**, **Amass**, and **SSL Labs** provide functionalities for subdomain enumeration and certificate scanning. However, these are either CLI-based or lack extensibility in UI and reporting. Our proposed solution draws inspiration from these utilities while augmenting automation, cross-source intelligence, and graphical interaction.

---

## **3. Methodology**

### 3.1 System Architecture

The system is composed of three main modules:

* **`subdomain_scanner`**: Performs multi-source enumeration.
* **`advanced_domain_analizer`**: Conducts SSL, DNS, HTTP header, and port analysis.
* <img width="1682" height="447" alt="image" src="https://github.com/user-attachments/assets/f9026640-9ef8-411f-b266-7a28405961c3" />

* **`main_app`**: GUI controller using `customtkinter` for visualization and triggering execution.

![Domain Security Analyzer - System Architecture_page-0001](https://github.com/user-attachments/assets/486269b2-74d6-4c6d-97b1-a3870aa3acf1)

---

### 3.2 Subdomain Enumeration

This module leverages:

* **DNS zone transfers**
* **CRT.sh** certificate transparency logs
* **ThreatCrowd and VirusTotal APIs**

---

### 3.3 Domain Analysis

Each identified (sub)domain undergoes:

* **DNS resolution & record type classification**
  <img width="1877" height="303" alt="image" src="https://github.com/user-attachments/assets/c8d9058a-49e7-49b4-aff4-07dc12f5dccb" />

* **SSL/TLS certificate inspection**
* **Port probing** for services (21, 22, 80, 443, 8080, etc.)
* **Security header evaluation** (e.g., `Strict-Transport-Security`, `Content-Security-Policy`)

The security header compliance scoring follows a weighted system:

<img width="1501" height="666" alt="image" src="https://github.com/user-attachments/assets/f7a74030-4814-4de8-b06f-bf4545447ca6" />

<img width="1661" height="678" alt="image" src="https://github.com/user-attachments/assets/dd1c0254-a675-4c63-81a9-0fb718cf34e1" />

| Header                      | Weight | Purpose               |
| --------------------------- | ------ | --------------------- |
| `Strict-Transport-Security` | 25     | Enforces HTTPS        |
| `Content-Security-Policy`   | 25     | Mitigates XSS         |
| `X-Frame-Options`           | 20     | Prevents clickjacking |

<img width="423" height="740" alt="image" src="https://github.com/user-attachments/assets/f2f36905-38b8-4570-bf77-7687d46d2f4b" />

<img width="426" height="628" alt="image" src="https://github.com/user-attachments/assets/d448165f-20cc-4826-b63c-5eaad0d643ab" />

<img width="402" height="571" alt="image" src="https://github.com/user-attachments/assets/4a52ae58-3a32-47e5-8f2a-292ba4a5906a" />

Optional and deprecated headers are also tracked, and recommendations are provided.

---

## **4. Implementation**

### 4.1 GUI Dashboard

<img width="1606" height="527" alt="image" src="https://github.com/user-attachments/assets/496f63bd-89ea-4ce5-8200-06f2fb7b0377" />

The GUI is implemented using `customtkinter`, providing:

* Multi-tab interface (Overview, Details, Charts)
* Dynamic progress bars
* Matplotlib-based embedded charts

![Figure 2: GUI with Charts and Statistics](attachment\:gui_overview.png)

### 4.2 HTML Reporting

The HTML report (`advanced_report.html`) is built using Plotly.js, custom CSS, and responsive design principles. It includes:

* Summary metrics
* Progress visualization
* Interactive charts (Pie, Bar, Radar)
* Tabular domain intelligence

![Figure 3: SSL Grade Chart (HTML Report)](attachment\:ssl_grade_chart.png)

---

## **5. Results and Discussion**

Tests were conducted on multiple public and enterprise domains. The system identified:

* An average of **45 subdomains** per target domain
* SSL grades ranging from A to F
* \~28% of domains lacking `Strict-Transport-Security`
* \~40% exposure to deprecated HTTP headers

Example summary:

| Metric                    | Value |
| ------------------------- | ----- |
| Total Domains             | 120   |
| Reachable Domains         | 112   |
| SSL Enabled               | 98    |
| Avg SSL Grade             | B     |
| Cloudflare Bypass Success | 93%   |

---

## **6. Conclusion**

The presented system offers an advanced, extensible, and visually-rich approach to automated domain reconnaissance. By integrating multiple intelligence sources, deep SSL and HTTP header inspections, and real-time GUI and HTML reporting, this tool significantly aids security practitioners in identifying infrastructure weaknesses. Future work includes machine-learning based anomaly detection and integration with SIEMs and CTI platforms.

---

## **7. References**

1. OWASP Secure Headers Project. [https://owasp.org/www-project-secure-headers/](https://owasp.org/www-project-secure-headers/)
2. CRT.sh – Certificate Transparency Logs. [https://crt.sh/](https://crt.sh/)
3. ThreatCrowd API. [https://www.threatcrowd.org/](https://www.threatcrowd.org/)
4. SeleniumHQ. [https://www.selenium.dev/](https://www.selenium.dev/)
5. Plotly.js for interactive charts. [https://plotly.com/javascript/](https://plotly.com/javascript/)

**Contact:**
Please contact me if you require the setup file or further assistance:

* Linkedin: [Chanaka Lasantha Nanayakkara](https://www.linkedin.com/in/chanaka-lasantha-nanayakkara-813357285/)
* ORCID: [0009-0006-3226-7713](https://orcid.org/0009-0006-3226-7713)
