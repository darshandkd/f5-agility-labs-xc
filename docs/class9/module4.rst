Module 4: Create WAS Application Scan and Review Scan Results
=============================================================

This module introduces F5 Distributed Cloud Web App Scanning (WAS) for automated DAST (Dynamic
Application Security Testing) and external attack surface discovery. You will learn how to access
the WAS interface, interpret scan results, and understand how WAS integrates into the DevSecOps
pipeline.

F5XC Web App Scanning (WAS) provides:

* Automated DAST and penetration testing capabilities
* External attack surface discovery
* Comprehensive vulnerability reports
* Integration with DevSecOps pipelines for continuous security assessment

.. note::
   *This module is primarily instructor-led. Follow along as your instructor demonstrates the WAS*
   *capabilities and facilitates discussion on the findings.*

**Expected Lab Time: 10-15 minutes**

Task 1: Access Web App Scanning in F5XC Console
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The following steps will allow you to access and explore the Web App Scanning interface in the F5XC
Console.

+---------------------------------------------------------------------------------------------------------------+
| **Access F5XC Console and Navigate to Web App Scanning**                                                      |
+===============================================================================================================+
| 1. Log in to the F5XC Console at https://f5-xc-lab-app.console.ves.volterra.io using your provided            |
|                                                                                                               |
|    credentials.                                                                                               |
|                                                                                                               |
| |module4-f5xc_login|                                                                                          |
+---------------------------------------------------------------------------------------------------------------+
| 2. From the home dashboard, click on **Web App & API Protection** tile to access the WAAP workspace.          |
|                                                                                                               |
| |module4-waap_navigation|                                                                                     |
+---------------------------------------------------------------------------------------------------------------+
| 3. In the left navigation sidebar, click on **CDN & Origin** and then select **Web App Scanning** to access   |
|                                                                                                               |
|    the WAS interface.                                                                                         |
|                                                                                                               |
| |module4-was_interface|                                                                                       |
+---------------------------------------------------------------------------------------------------------------+

+---------------------------------------------------------------------------------------------------------------+
| **Explore Web App Scanning Features**                                                                         |
+===============================================================================================================+
| 1. Review the WAS dashboard and explore the available scanning options:                                       |
|                                                                                                               |
|    * **Application Scans** - DAST scanning of web applications                                                |
|    * **Attack Surface Discovery** - External attack surface mapping                                           |
|    * **Scan Templates** - Pre-configured scan profiles                                                        |
|    * **Scheduled Scans** - Automated recurring scans                                                          |
|    * **Reports** - Comprehensive vulnerability reports                                                        |
|                                                                                                               |
| |module4-was_features|                                                                                        |
+---------------------------------------------------------------------------------------------------------------+
| 2. Explore the scan configuration options by clicking on **Add Scan** (for demonstration purposes only):      |
|                                                                                                               |
|    * Target URL specification                                                                                 |
|    * Authentication settings                                                                                  |
|    * Scan depth and coverage                                                                                  |
|    * Exclusion rules                                                                                          |
|                                                                                                               |
| |module4-scan_config|                                                                                         |
|                                                                                                               |
| .. note::                                                                                                     |
|    *Do not execute a new scan. Your instructor will use pre-scanned reports for this demonstration.*          |
+---------------------------------------------------------------------------------------------------------------+

Task 2: Review Pre-Scanned Application Reports
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Your instructor will present two pre-scanned reports for comparison, demonstrating the security
posture of the AI-generated application with and without F5XC WAAP protection.

+---------------------------------------------------------------------------------------------------------------+
| **Report 1: AI-Generated Application WITHOUT F5XC WAAP**                                                      |
+===============================================================================================================+
| 1. Your instructor will open the pre-scanned report for the vulnerable application without WAAP protection.   |
|                                                                                                               |
|    Observe the scan summary and overall risk score.                                                           |
|                                                                                                               |
| |module4-report_without_waap|                                                                                 |
+---------------------------------------------------------------------------------------------------------------+
| 2. Review the vulnerability summary showing discovered issues categorized by severity:                        |
|                                                                                                               |
|    * **Critical** - Vulnerabilities requiring immediate attention                                             |
|    * **High** - Significant security risks                                                                    |
|    * **Medium** - Moderate security concerns                                                                  |
|    * **Low** - Minor issues and informational findings                                                        |
|                                                                                                               |
| |module4-vuln_summary_no_waap|                                                                                |
+---------------------------------------------------------------------------------------------------------------+
| 3. Examine specific vulnerabilities discovered in the unprotected application:                                |
|                                                                                                               |
|    * **SQL Injection (Critical)** - Unsanitized input in database queries                                     |
|    * **Cross-Site Scripting - XSS (High)** - Reflected XSS in user input fields                               |
|    * **Sensitive Data Exposure (High)** - Exposed API keys and credentials                                    |
|    * **Security Misconfiguration (Medium)** - Missing security headers                                        |
|    * **Information Disclosure (Low)** - Verbose error messages                                                |
|                                                                                                               |
| |module4-vuln_details_no_waap|                                                                                |
+---------------------------------------------------------------------------------------------------------------+

+---------------------------------------------------------------------------------------------------------------+
| **Report 2: AI-Generated Application WITH F5XC WAAP**                                                         |
+===============================================================================================================+
| 1. Your instructor will open the pre-scanned report for the same application with WAAP protection enabled.    |
|                                                                                                               |
|    Compare the scan summary and overall risk score with the unprotected scan.                                 |
|                                                                                                               |
| |module4-report_with_waap|                                                                                    |
+---------------------------------------------------------------------------------------------------------------+
| 2. Compare the vulnerability summary. Note how WAAP provides defense-in-depth:                                |
|                                                                                                               |
|    * Many attack vectors are now **blocked** by WAF                                                           |
|    * Exploitation attempts are **mitigated**                                                                  |
|    * Some vulnerabilities remain but are **protected** at runtime                                             |
|                                                                                                               |
| |module4-vuln_summary_waap|                                                                                   |
+---------------------------------------------------------------------------------------------------------------+
| 3. Review the comparison showing how F5XC WAAP protects against discovered vulnerabilities:                   |
|                                                                                                               |
|    * **SQL Injection** - Without WAAP: Exploitable | With WAAP: Blocked by WAF signatures                    |
|    * **XSS** - Without WAAP: Exploitable | With WAAP: Blocked by WAF signatures                              |
|    * **API Abuse** - Without WAAP: Unrestricted | With WAAP: Rate limited, schema enforced                   |
|    * **Bot Attacks** - Without WAAP: Undetected | With WAAP: Detected and mitigated                          |
|                                                                                                               |
| |module4-comparison_table|                                                                                    |
+---------------------------------------------------------------------------------------------------------------+

Task 3: Analyze Security Findings
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Your instructor will facilitate analysis and discussion of the WAF detections, API security
discoveries, and bot defense signals.

+---------------------------------------------------------------------------------------------------------------+
| **Analyze WAF Detections and Blocked Attacks**                                                                |
+===============================================================================================================+
| 1. Navigate to the WAF detections section of the report to review attack signatures that were triggered.      |
|                                                                                                               |
| |module4-waf_detections|                                                                                      |
+---------------------------------------------------------------------------------------------------------------+
| 2. Review the types of attack patterns detected:                                                              |
|                                                                                                               |
|    * OWASP Top 10 attack patterns                                                                             |
|    * Custom signature matches                                                                                 |
|    * Anomaly-based detections                                                                                 |
|                                                                                                               |
| |module4-attack_signatures|                                                                                   |
+---------------------------------------------------------------------------------------------------------------+
| 3. Understand the WAF actions taken on detected attacks:                                                      |
|                                                                                                               |
|    * **Block** - Request rejected with error response                                                         |
|    * **Flag** - Request logged for review but allowed                                                         |
|    * **Challenge** - JavaScript challenge presented to client                                                 |
|                                                                                                               |
| |module4-waf_actions|                                                                                         |
+---------------------------------------------------------------------------------------------------------------+

+---------------------------------------------------------------------------------------------------------------+
| **Review API Security Discoveries**                                                                           |
+===============================================================================================================+
| 1. Navigate to the **API Security** section of the report to review discovered API endpoints.                 |
|                                                                                                               |
| |module4-api_security|                                                                                        |
+---------------------------------------------------------------------------------------------------------------+
| 2. Review discovered API endpoints and their characteristics:                                                 |
|                                                                                                               |
|    * Documented vs. undocumented (shadow) APIs                                                                |
|    * Authentication requirements                                                                              |
|    * Data sensitivity classification                                                                          |
|                                                                                                               |
| |module4-api_endpoints|                                                                                       |
+---------------------------------------------------------------------------------------------------------------+
| 3. Examine schema violations and anomalies detected:                                                          |
|                                                                                                               |
|    * **Invalid Parameter** - Request parameters not matching schema                                           |
|    * **Missing Auth** - Endpoints accessed without authentication                                             |
|    * **Rate Exceeded** - API rate limits exceeded                                                             |
|    * **Schema Mismatch** - Response format deviating from OpenAPI spec                                        |
|                                                                                                               |
| |module4-schema_violations|                                                                                   |
+---------------------------------------------------------------------------------------------------------------+

+---------------------------------------------------------------------------------------------------------------+
| **Analyze Bot Defense Signals**                                                                               |
+===============================================================================================================+
| 1. Navigate to the **Bot Defense** section of the report to review bot traffic classification.                |
|                                                                                                               |
| |module4-bot_defense|                                                                                         |
+---------------------------------------------------------------------------------------------------------------+
| 2. Review bot traffic categories identified:                                                                  |
|                                                                                                               |
|    * **Good Bots** - Search engines, monitoring services                                                      |
|    * **Malicious Bots** - Scrapers, credential stuffers, attackers                                            |
|    * **Unknown** - Unclassified automated traffic                                                             |
|                                                                                                               |
| |module4-bot_classification|                                                                                  |
+---------------------------------------------------------------------------------------------------------------+
| 3. Examine bot mitigation effectiveness metrics:                                                              |
|                                                                                                               |
|    * Challenge success/failure rates                                                                          |
|    * Bot signature matches                                                                                    |
|    * Behavioral analysis results                                                                              |
|                                                                                                               |
| |module4-bot_mitigation|                                                                                      |
+---------------------------------------------------------------------------------------------------------------+

+---------------------------------------------------------------------------------------------------------------+
| **Facilitated Discussion**                                                                                    |
+===============================================================================================================+
| Your instructor will facilitate a discussion covering the following topics:                                   |
|                                                                                                               |
| **WAF Effectiveness**                                                                                         |
|                                                                                                               |
|    * How WAF signatures blocked common attack vectors                                                         |
|    * Importance of keeping signatures updated                                                                 |
|    * Custom rule creation for application-specific protection                                                 |
|                                                                                                               |
| **API Security Insights**                                                                                     |
|                                                                                                               |
|    * Value of API discovery and documentation                                                                 |
|    * Schema enforcement benefits                                                                              |
|    * Handling shadow APIs                                                                                     |
|                                                                                                               |
| **Bot Defense Value**                                                                                         |
|                                                                                                               |
|    * Impact of bot traffic on applications                                                                    |
|    * Behavioral vs. signature-based detection                                                                 |
|    * Balancing security and user experience                                                                   |
|                                                                                                               |
| **DevSecOps Integration**                                                                                     |
|                                                                                                               |
|    * Feeding WAS results back into development                                                                |
|    * Prioritizing vulnerability remediation                                                                   |
|    * Continuous scanning in CI/CD pipelines                                                                   |
|                                                                                                               |
| |module4-discussion|                                                                                          |
+---------------------------------------------------------------------------------------------------------------+

+---------------------------------------------------------------------------------------------------------------+
| **The Repeatable Workflow: Code. Secure. Repeat.**                                                            |
+===============================================================================================================+
| This lab reinforces the continuous security improvement loop that forms the foundation of modern DevSecOps:   |
|                                                                                                               |
|    **Code (AI-assisted) → Commit → Scan (SAST/WAS/API) → Protect (WAAP/API Sec/Bot) → Improve → Repeat**      |
|                                                                                                               |
| |module4-workflow_diagram|                                                                                    |
+---------------------------------------------------------------------------------------------------------------+

+---------------------------------------------------------------------------------------------------------------+
| **End of Module 4**                                                                                           |
+===============================================================================================================+
| This concludes Module 4. In this module, you learned about F5XC Web App Scanning capabilities and how WAS     |
|                                                                                                               |
| provides automated DAST scanning for vulnerability discovery. Key takeaways:                                  |
|                                                                                                               |
|    * WAS provides automated DAST scanning and external attack surface mapping                                 |
|    * WAAP provides defense-in-depth with WAF, API Protection, and Bot Defense                                 |
|    * Comprehensive reporting enables actionable insights for security and development teams                   |
|    * WAS reports integrate with DevSecOps pipelines for continuous security improvement                       |
|                                                                                                               |
| Proceed to the **Closing** section for lab summary and additional resources.                                  |
|                                                                                                               |
| |labend|                                                                                                      |
+---------------------------------------------------------------------------------------------------------------+

.. |module4-f5xc_login| image:: _static/module4-f5xc_login.png
   :width: 800px
.. |module4-waap_navigation| image:: _static/module4-waap_navigation.png
   :width: 800px
.. |module4-was_interface| image:: _static/module4-was_interface.png
   :width: 800px
.. |module4-was_features| image:: _static/module4-was_features.png
   :width: 800px
.. |module4-scan_config| image:: _static/module4-scan_config.png
   :width: 800px
.. |module4-report_without_waap| image:: _static/module4-report_without_waap.png
   :width: 800px
.. |module4-vuln_summary_no_waap| image:: _static/module4-vuln_summary_no_waap.png
   :width: 800px
.. |module4-vuln_details_no_waap| image:: _static/module4-vuln_details_no_waap.png
   :width: 800px
.. |module4-report_with_waap| image:: _static/module4-report_with_waap.png
   :width: 800px
.. |module4-vuln_summary_waap| image:: _static/module4-vuln_summary_waap.png
   :width: 800px
.. |module4-comparison_table| image:: _static/module4-comparison_table.png
   :width: 800px
.. |module4-waf_detections| image:: _static/module4-waf_detections.png
   :width: 800px
.. |module4-attack_signatures| image:: _static/module4-attack_signatures.png
   :width: 800px
.. |module4-waf_actions| image:: _static/module4-waf_actions.png
   :width: 800px
.. |module4-api_security| image:: _static/module4-api_security.png
   :width: 800px
.. |module4-api_endpoints| image:: _static/module4-api_endpoints.png
   :width: 800px
.. |module4-schema_violations| image:: _static/module4-schema_violations.png
   :width: 800px
.. |module4-bot_defense| image:: _static/module4-bot_defense.png
   :width: 800px
.. |module4-bot_classification| image:: _static/module4-bot_classification.png
   :width: 800px
.. |module4-bot_mitigation| image:: _static/module4-bot_mitigation.png
   :width: 800px
.. |module4-discussion| image:: _static/module4-discussion.png
   :width: 800px
.. |module4-workflow_diagram| image:: _static/module4-workflow_diagram.png
   :width: 800px
.. |labend| image:: _static/labend.png
   :width: 800px
