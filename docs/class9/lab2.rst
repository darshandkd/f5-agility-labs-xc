Module 2: Deploy and Secure Vulnerable App
==========================================

This module guides you through deploying a pre-established vulnerable application using GitLab CI/CD
pipelines and securing it with F5 Distributed Cloud (F5 XC) services. You will experience the complete
DevSecOps workflow from code commit to production deployment with integrated security controls.

In this module, you will:

* Commit a pre-established vulnerable application to GitLab
* Experience automated SAST and Secret Detection in CI/CD pipelines
* Deploy the application to F5XC vK8s using Terraform
* Configure WAF, Bot Defense, and API Protection
* Trigger attack scripts to test security controls

**Expected Lab Time: 45-50 minutes**

Task 1: Commit Pre-Established Vulnerable Application Code
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The following steps will allow you to commit the pre-created vulnerable application to GitLab CE,
triggering the automated CI/CD pipeline that builds, scans, and deploys the application.

+---------------------------------------------------------------------------------------------------------------+
| **Open Pre-Created Vulnerable Application**                                                                   |
+===============================================================================================================+
| 1. In VSCode Server, navigate to the project directory containing the pre-created vulnerable application.     |
|                                                                                                               |
|    Use the File Explorer in the sidebar to browse to the project folder.                                      |
|                                                                                                               |
| |module2-project_directory|                                                                                   |
+---------------------------------------------------------------------------------------------------------------+
| 2. Explore the application structure and review the key files. The application should contain the following   |
|                                                                                                               |
|    structure:                                                                                                 |
|                                                                                                               |
|    * **src/** - Application source code                                                                       |
|    * **Dockerfile** - Container build configuration                                                           |
|    * **requirements.txt** - Python dependencies                                                               |
|    * **.gitlab-ci.yml** - CI/CD pipeline configuration                                                        |
|    * **terraform/** - Infrastructure as Code for F5XC deployment                                              |
|                                                                                                               |
| |module2-file_structure|                                                                                      |
+---------------------------------------------------------------------------------------------------------------+
| 3. Open and review the main application files to understand the code structure. Click on **app.py** or the    |
|                                                                                                               |
|    main application file to view its contents.                                                                |
|                                                                                                               |
| |module2-review_code|                                                                                         |
+---------------------------------------------------------------------------------------------------------------+

+---------------------------------------------------------------------------------------------------------------+
| **Commit and Push to GitLab**                                                                                 |
+===============================================================================================================+
| 1. Open the **Source Control** panel in VSCode by clicking the branch icon in the sidebar, or use the         |
|                                                                                                               |
|    integrated terminal.                                                                                       |
|                                                                                                               |
| |module2-source_control|                                                                                      |
+---------------------------------------------------------------------------------------------------------------+
| 2. Stage all changes by clicking the **+** icon next to **Changes** or by running the following command in    |
|                                                                                                               |
|    the terminal:                                                                                              |
|                                                                                                               |
| .. code-block:: bash                                                                                          |
|                                                                                                               |
|    git add .                                                                                                  |
|                                                                                                               |
| |module2-git_add|                                                                                             |
+---------------------------------------------------------------------------------------------------------------+
| 3. Enter a commit message describing your changes in the **Message** field:                                   |
|                                                                                                               |
|    *Initial commit: Pre-established vulnerable application for lab*                                           |
|                                                                                                               |
| |module2-commit_message|                                                                                      |
+---------------------------------------------------------------------------------------------------------------+
| 4. Commit the changes by clicking the **Commit** button or running:                                           |
|                                                                                                               |
| .. code-block:: bash                                                                                          |
|                                                                                                               |
|    git commit -m "Initial commit: Pre-established vulnerable application for lab"                             |
|                                                                                                               |
| |module2-git_commit|                                                                                          |
+---------------------------------------------------------------------------------------------------------------+
| 5. Push the changes to GitLab CE by clicking **Sync Changes** or running:                                     |
|                                                                                                               |
| .. code-block:: bash                                                                                          |
|                                                                                                               |
|    git push origin main                                                                                       |
|                                                                                                               |
| |module2-git_push|                                                                                            |
+---------------------------------------------------------------------------------------------------------------+

+---------------------------------------------------------------------------------------------------------------+
| **Observe CI/CD Pipeline Execution**                                                                          |
+===============================================================================================================+
| 1. Open GitLab CE in your browser and navigate to your project. Use the URL provided in your lab environment. |
|                                                                                                               |
| |module2-gitlab_project|                                                                                      |
+---------------------------------------------------------------------------------------------------------------+
| 2. Navigate to **CI/CD > Pipelines** in the left sidebar to view the triggered pipeline.                      |
|                                                                                                               |
| |module2-pipeline_view|                                                                                       |
+---------------------------------------------------------------------------------------------------------------+
| 3. Observe the pipeline stages executing. The pipeline includes the following stages:                         |
|                                                                                                               |
|    * **SAST** - Static Application Security Testing                                                           |
|    * **Secret Detection** - Scan for exposed secrets and credentials                                          |
|    * **Build** - Source-to-container build (Image v1.0)                                                       |
|    * **Push** - Push container image to registry                                                              |
|    * **Deploy** - Terraform deployment to F5XC vK8s                                                           |
|                                                                                                               |
| |module2-pipeline_stages|                                                                                     |
|                                                                                                               |
| .. note::                                                                                                     |
|    *The pipeline may take several minutes to complete all stages. Wait for all stages to finish before*       |
|    *proceeding to the next step.*                                                                             |
+---------------------------------------------------------------------------------------------------------------+
| 4. **Alternative Flow - Secret Detection Failure:** If the pipeline fails due to exposed secrets in the       |
|                                                                                                               |
|    application code, you will need to correct the issue.                                                      |
|                                                                                                               |
|    a. Review the pipeline error in GitLab by clicking on the failed job                                       |
|    b. Return to VSCode and correct the exposed secret in the code                                             |
|    c. Commit and push the fix using the same steps above                                                      |
|    d. The pipeline will re-trigger automatically                                                              |
|                                                                                                               |
| |module2-secret_failure|                                                                                      |
+---------------------------------------------------------------------------------------------------------------+

+---------------------------------------------------------------------------------------------------------------+
| **Verify Automated Deployment**                                                                               |
+===============================================================================================================+
| 1. Once the pipeline succeeds, verify that the **Container Image v1.0** has been pushed to the container      |
|                                                                                                               |
|    registry. Navigate to **Packages & Registries > Container Registry** in GitLab.                            |
|                                                                                                               |
| |module2-container_registry|                                                                                  |
+---------------------------------------------------------------------------------------------------------------+
| 2. Log in to the F5XC Console and navigate to **Distributed Apps > Virtual K8s** to verify the **vK8s         |
|                                                                                                               |
|    Workload** has been deployed.                                                                              |
|                                                                                                               |
| |module2-vk8s_workload|                                                                                       |
+---------------------------------------------------------------------------------------------------------------+
| 3. Navigate to **Multi-Cloud App Connect > Manage > Load Balancers > Origin Pools** to verify the **Origin    |
|                                                                                                               |
|    Pool** has been created and is pointing to the vK8s workload.                                              |
|                                                                                                               |
| |module2-origin_pool|                                                                                         |
+---------------------------------------------------------------------------------------------------------------+
| 4. Navigate to **Multi-Cloud App Connect > Manage > Load Balancers > HTTP Load Balancers** to verify the      |
|                                                                                                               |
|    **HTTP Load Balancer** has been configured with the following security controls:                           |
|                                                                                                               |
|    * WAF policy attached                                                                                      |
|    * Bot Defense enabled                                                                                      |
|    * API Protection enabled                                                                                   |
|                                                                                                               |
| |module2-http_lb|                                                                                             |
+---------------------------------------------------------------------------------------------------------------+
| 5. Note the public URL of your deployed application from the HTTP Load Balancer configuration. You will need  |
|                                                                                                               |
|    this URL for the next task.                                                                                |
|                                                                                                               |
| |module2-f5xc_verification|                                                                                   |
+---------------------------------------------------------------------------------------------------------------+

Task 2: Trigger Simple Attack Script
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The following steps will allow you to execute attack scripts against the deployed vulnerable
application to test the effectiveness of the F5XC security controls.

+---------------------------------------------------------------------------------------------------------------+
| **Identify Application URL and Verify Access**                                                                |
+===============================================================================================================+
| 1. Retrieve the public URL of your deployed application from the HTTP Load Balancer configuration noted in    |
|                                                                                                               |
|    the previous task.                                                                                         |
|                                                                                                               |
| |module2-app_url|                                                                                             |
+---------------------------------------------------------------------------------------------------------------+
| 2. Open the application URL in your browser to verify the application is accessible and functioning.          |
|                                                                                                               |
| |module2-app_accessible|                                                                                      |
+---------------------------------------------------------------------------------------------------------------+

+---------------------------------------------------------------------------------------------------------------+
| **Execute Attack Scripts**                                                                                    |
+===============================================================================================================+
| 1. Open a terminal in VSCode Server by selecting **Terminal > New Terminal** from the menu, or access the     |
|                                                                                                               |
|    client VM terminal.                                                                                        |
|                                                                                                               |
| |module2-terminal|                                                                                            |
+---------------------------------------------------------------------------------------------------------------+
| 2. Navigate to the attack scripts directory provided in your lab environment:                                 |
|                                                                                                               |
| .. code-block:: bash                                                                                          |
|                                                                                                               |
|    cd /path/to/attack-scripts                                                                                 |
|                                                                                                               |
| |module2-attack_scripts_dir|                                                                                  |
+---------------------------------------------------------------------------------------------------------------+
| 3. Review the available attack scripts by listing the directory contents:                                     |
|                                                                                                               |
| .. code-block:: bash                                                                                          |
|                                                                                                               |
|    ls -la                                                                                                     |
|                                                                                                               |
| |module2-attack_scripts|                                                                                      |
+---------------------------------------------------------------------------------------------------------------+
| 4. Execute the **SQL Injection** attack script against your application:                                      |
|                                                                                                               |
| .. code-block:: bash                                                                                          |
|                                                                                                               |
|    ./sqli_attack.sh <YOUR_APP_URL>                                                                            |
|                                                                                                               |
| |module2-sqli_attack|                                                                                         |
|                                                                                                               |
| .. note::                                                                                                     |
|    *Replace <YOUR_APP_URL> with the actual URL of your deployed application.*                                 |
+---------------------------------------------------------------------------------------------------------------+
| 5. Execute the **Cross-Site Scripting (XSS)** attack script:                                                  |
|                                                                                                               |
| .. code-block:: bash                                                                                          |
|                                                                                                               |
|    ./xss_attack.sh <YOUR_APP_URL>                                                                             |
|                                                                                                               |
| |module2-xss_attack|                                                                                          |
+---------------------------------------------------------------------------------------------------------------+
| 6. Execute additional attack scripts as provided by your instructor:                                          |
|                                                                                                               |
| .. code-block:: bash                                                                                          |
|                                                                                                               |
|    ./bot_attack.sh <YOUR_APP_URL>                                                                             |
|    ./api_abuse.sh <YOUR_APP_URL>                                                                              |
|                                                                                                               |
| |module2-additional_attacks|                                                                                  |
+---------------------------------------------------------------------------------------------------------------+

+---------------------------------------------------------------------------------------------------------------+
| **Review Attack Results in F5XC Console**                                                                     |
+===============================================================================================================+
| 1. Log in to the F5XC Console and navigate to **Web App & API Protection** from the home dashboard.           |
|                                                                                                               |
| |module2-waap_dashboard|                                                                                      |
+---------------------------------------------------------------------------------------------------------------+
| 2. Navigate to **Dashboards > Security Dashboard** to view an overview of detected attacks and security       |
|                                                                                                               |
|    events.                                                                                                    |
|                                                                                                               |
| |module2-security_analytics|                                                                                  |
+---------------------------------------------------------------------------------------------------------------+
| 3. Review the **Security Events** log by navigating to **Apps & APIs > Security > Security Analytics**. You   |
|                                                                                                               |
|    should see events corresponding to your attack scripts:                                                    |
|                                                                                                               |
|    * **SQL Injection** - WAF Signature Match - Blocked                                                        |
|    * **XSS** - WAF Signature Match - Blocked                                                                  |
|    * **Bot Traffic** - Bot Defense - Flagged/Blocked                                                          |
|    * **API Abuse** - API Protection - Rate Limited/Blocked                                                    |
|                                                                                                               |
| |module2-security_events|                                                                                     |
+---------------------------------------------------------------------------------------------------------------+
| 4. Click on an individual security event to drill down and view detailed information:                         |
|                                                                                                               |
|    * Attack signature matched                                                                                 |
|    * Request details (headers, payload)                                                                       |
|    * Action taken (blocked, flagged, allowed)                                                                 |
|    * Source IP and geo-location                                                                               |
|                                                                                                               |
| |module2-event_details|                                                                                       |
+---------------------------------------------------------------------------------------------------------------+
| 5. Navigate to **Apps & APIs > Security > WAF** to review the WAF Dashboard showing an overview of blocked    |
|                                                                                                               |
|    attacks.                                                                                                   |
|                                                                                                               |
| |module2-waf_dashboard|                                                                                       |
+---------------------------------------------------------------------------------------------------------------+

+---------------------------------------------------------------------------------------------------------------+
| **Analyze Bot Defense Signals**                                                                               |
+===============================================================================================================+
| 1. Navigate to **Apps & APIs > Security > Bot Defense** in the F5XC Console.                                  |
|                                                                                                               |
| |module2-bot_defense|                                                                                         |
+---------------------------------------------------------------------------------------------------------------+
| 2. Review the bot classification and signals displayed in the dashboard:                                      |
|                                                                                                               |
|    * Automated traffic detection                                                                              |
|    * Bot signatures identified                                                                                |
|    * Mitigation actions applied                                                                               |
|                                                                                                               |
| |module2-bot_signals|                                                                                         |
+---------------------------------------------------------------------------------------------------------------+

+---------------------------------------------------------------------------------------------------------------+
| **End of Module 2**                                                                                           |
+===============================================================================================================+
| This concludes Module 2. In this module, you learned about the complete DevSecOps workflow from code commit   |
|                                                                                                               |
| to production deployment with integrated security controls. Key takeaways:                                    |
|                                                                                                               |
|    * GitLab CI/CD provides automated SAST, Secret Detection, and deployment pipelines                         |
|    * Terraform enables Infrastructure as Code deployment of F5XC resources                                    |
|    * F5XC WAAP provides comprehensive protection with WAF, Bot Defense, and API Protection                    |
|    * Security visibility through real-time attack detection and comprehensive logging                         |
|                                                                                                               |
| Proceed to **Module 3** to add advanced security controls and API functionality.                              |
|                                                                                                               |
| |labend|                                                                                                      |
+---------------------------------------------------------------------------------------------------------------+

.. |module2-project_directory| image:: _static/module2-project_directory.png
   :width: 800px
.. |module2-file_structure| image:: _static/module2-file_structure.png
   :width: 800px
.. |module2-review_code| image:: _static/module2-review_code.png
   :width: 800px
.. |module2-source_control| image:: _static/module2-source_control.png
   :width: 800px
.. |module2-git_add| image:: _static/module2-git_add.png
   :width: 800px
.. |module2-commit_message| image:: _static/module2-commit_message.png
   :width: 800px
.. |module2-git_commit| image:: _static/module2-git_commit.png
   :width: 800px
.. |module2-git_push| image:: _static/module2-git_push.png
   :width: 800px
.. |module2-gitlab_project| image:: _static/module2-gitlab_project.png
   :width: 800px
.. |module2-pipeline_view| image:: _static/module2-pipeline_view.png
   :width: 800px
.. |module2-pipeline_stages| image:: _static/module2-pipeline_stages.png
   :width: 800px
.. |module2-secret_failure| image:: _static/module2-secret_failure.png
   :width: 800px
.. |module2-container_registry| image:: _static/module2-container_registry.png
   :width: 800px
.. |module2-vk8s_workload| image:: _static/module2-vk8s_workload.png
   :width: 800px
.. |module2-origin_pool| image:: _static/module2-origin_pool.png
   :width: 800px
.. |module2-http_lb| image:: _static/module2-http_lb.png
   :width: 800px
.. |module2-f5xc_verification| image:: _static/module2-f5xc_verification.png
   :width: 800px
.. |module2-app_url| image:: _static/module2-app_url.png
   :width: 800px
.. |module2-app_accessible| image:: _static/module2-app_accessible.png
   :width: 800px
.. |module2-terminal| image:: _static/module2-terminal.png
   :width: 800px
.. |module2-attack_scripts_dir| image:: _static/module2-attack_scripts_dir.png
   :width: 800px
.. |module2-attack_scripts| image:: _static/module2-attack_scripts.png
   :width: 800px
.. |module2-sqli_attack| image:: _static/module2-sqli_attack.png
   :width: 800px
.. |module2-xss_attack| image:: _static/module2-xss_attack.png
   :width: 800px
.. |module2-additional_attacks| image:: _static/module2-additional_attacks.png
   :width: 800px
.. |module2-waap_dashboard| image:: _static/module2-waap_dashboard.png
   :width: 800px
.. |module2-security_analytics| image:: _static/module2-security_analytics.png
   :width: 800px
.. |module2-security_events| image:: _static/module2-security_events.png
   :width: 800px
.. |module2-event_details| image:: _static/module2-event_details.png
   :width: 800px
.. |module2-waf_dashboard| image:: _static/module2-waf_dashboard.png
   :width: 800px
.. |module2-bot_defense| image:: _static/module2-bot_defense.png
   :width: 800px
.. |module2-bot_signals| image:: _static/module2-bot_signals.png
   :width: 800px
.. |labend| image:: _static/labend.png
   :width: 800px
