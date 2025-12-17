Lab 1: Environment Access & Verification
=========================================

This lab will focus on verifying access to all required lab components for the "Code. Secure. 
Repeat." workshop. Students will validate connectivity to Visual Studio Code Server, GitLab 
Community Edition, and the F5 Distributed Cloud tenant. Additionally, students will verify 
pre-configured objects including namespaces, Customer Edge sites, Virtual Sites, and Virtual 
Kubernetes (vK8s) clusters. The lab concludes with a walkthrough of the complete DevSecOps 
workflow that will be implemented throughout subsequent lab modules.

For the tasks that follow, you should have received lab credentials from your instructor. 
These credentials include access to your individual **namespace**, **VS Code Server URL**, 
**GitLab instance**, and **F5 Distributed Cloud tenant**.

**Expected Lab Time: 15 minutes**

Task 1: Verify Visual Studio Code Server Access
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The following steps will allow you to access the browser-based Visual Studio Code Server 
environment and verify that Terraform CLI is available for Infrastructure as Code operations.

+---------------------------------------------------------------------------------------------------------------+
| **Access VS Code Server and Verify Environment**                                                             |
+===============================================================================================================+
| 1. Open a web browser and navigate to the **VS Code Server URL** provided by your lab instructor.            |
+---------------------------------------------------------------------------------------------------------------+
| 2. Authenticate using the lab credentials provided by your instructor.                                       |
+---------------------------------------------------------------------------------------------------------------+
| 3. Once logged in, verify that the **Explorer** view is visible on the left sidebar. This displays your      |
|                                                                                                               |
|    workspace directory structure.                                                                             |
+---------------------------------------------------------------------------------------------------------------+
| 4. From the top menu, select **View → Terminal** to open an integrated terminal session.                     |
+---------------------------------------------------------------------------------------------------------------+
| 5. In the terminal window, execute the following command to verify Terraform installation:                   |
|                                                                                                               |
|    .. code-block:: bash                                                                                       |
|                                                                                                               |
|       terraform version                                                                                       |
|                                                                                                               |
| .. note::                                                                                                     |
|    *You should see output indicating Terraform v1.5.x or higher. If the command is not found, contact your*  |
|    *lab instructor before proceeding.*                                                                        |
+---------------------------------------------------------------------------------------------------------------+

Task 2: Verify GitLab Community Edition Access
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The following steps will allow you to access the GitLab CE instance and verify that your 
project repository is available for source code management and CI/CD pipeline operations.

+---------------------------------------------------------------------------------------------------------------+
| **Access GitLab and Verify Repository**                                                                      |
+===============================================================================================================+
| 1. Open a new browser tab and navigate to the **GitLab URL** provided by your lab instructor.                |
+---------------------------------------------------------------------------------------------------------------+
| 2. Sign in using the lab credentials provided by your instructor.                                            |
+---------------------------------------------------------------------------------------------------------------+
| 3. From the GitLab dashboard, verify that your **project repository** is visible in the projects list.       |
+---------------------------------------------------------------------------------------------------------------+
| 4. Click on your project repository to open it. Verify that the repository contains initial application      |
|                                                                                                               |
|    code and configuration files.                                                                              |
|                                                                                                               |
| .. note::                                                                                                     |
|    *The repository should contain application source code, Terraform configuration files, and CI/CD*         |
|    *pipeline definitions. These will be used in subsequent lab modules.*                                     |
+---------------------------------------------------------------------------------------------------------------+

Task 3: Verify F5 Distributed Cloud Tenant Access
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The following steps will allow you to access the F5 Distributed Cloud Console and verify that 
pre-configured objects including namespaces, Customer Edge sites, Virtual Sites, and Virtual 
Kubernetes clusters are ready for use.

+---------------------------------------------------------------------------------------------------------------+
| **Login to F5 Distributed Cloud Console**                                                                    |
+===============================================================================================================+
| 1. Open a new browser tab and navigate to your F5 Distributed Cloud Console tenant URL provided by your      |
|                                                                                                               |
|    lab instructor.                                                                                            |
+---------------------------------------------------------------------------------------------------------------+
| 2. Sign in using the lab credentials provided by your instructor.                                            |
|                                                                                                               |
| .. note::                                                                                                     |
|    *If this is your first login, you may be prompted to set work domain roles and skill levels. Follow the*  |
|    *on-screen instructions to complete your profile setup.*                                                  |
+---------------------------------------------------------------------------------------------------------------+

+---------------------------------------------------------------------------------------------------------------+
| **Verify Namespace Configuration**                                                                           |
+===============================================================================================================+
| 1. From the F5 Distributed Cloud Console home page, click the **User Icon** in the top right corner and      |
|                                                                                                               |
|    select **Account Settings**.                                                                               |
+---------------------------------------------------------------------------------------------------------------+
| 2. In the resulting screen, click **My Namespaces** under the **Personal Management** section on the left.   |
+---------------------------------------------------------------------------------------------------------------+
| 3. Verify that your assigned namespace is listed and accessible. Note your namespace name as it will be      |
|                                                                                                               |
|    used throughout the lab exercises.                                                                         |
|                                                                                                               |
| .. note::                                                                                                     |
|    *Namespace format typically follows: <firstname-lastname> or a lab-specific naming convention. If you*    |
|    *do not see a namespace assigned to you, contact your lab instructor.*                                    |
+---------------------------------------------------------------------------------------------------------------+

+---------------------------------------------------------------------------------------------------------------+
| **Verify Customer Edge Sites and Virtual Sites**                                                             |
+===============================================================================================================+
| 1. From the F5 Distributed Cloud Console home page, use the **Select Service** dropdown and select           |
|                                                                                                               |
|    **Multi-Cloud Network Connect**.                                                                           |
+---------------------------------------------------------------------------------------------------------------+
| 2. From the left navigation sidebar, expand **Manage** and click **Site Management → Sites**.                |
+---------------------------------------------------------------------------------------------------------------+
| 3. Verify that Customer Edge (CE) sites are listed and display **ONLINE** status in the **Site Admin State** |
|                                                                                                               |
|    column.                                                                                                    |
|                                                                                                               |
| .. note::                                                                                                     |
|    *Customer Edge sites extend F5 Distributed Cloud capabilities into your environment. These sites will*    |
|    *host your distributed applications and provide local data plane processing.*                             |
+---------------------------------------------------------------------------------------------------------------+
| 4. From the left navigation sidebar, expand **Manage** and click **Virtual Sites**.                          |
+---------------------------------------------------------------------------------------------------------------+
| 5. Verify that a Virtual Site is configured and contains your assigned Customer Edge sites.                  |
|                                                                                                               |
| .. note::                                                                                                     |
|    *Virtual Sites are logical groupings of physical sites. They enable you to deploy workloads across*       |
|    *multiple locations simultaneously using a single deployment target.*                                     |
+---------------------------------------------------------------------------------------------------------------+

+---------------------------------------------------------------------------------------------------------------+
| **Verify Virtual Kubernetes (vK8s) Configuration**                                                           |
+===============================================================================================================+
| 1. From the F5 Distributed Cloud Console home page, use the **Select Service** dropdown and select           |
|                                                                                                               |
|    **Distributed Apps**.                                                                                      |
+---------------------------------------------------------------------------------------------------------------+
| 2. Ensure your namespace is selected from the namespace dropdown in the top left corner.                     |
+---------------------------------------------------------------------------------------------------------------+
| 3. From the left navigation sidebar, expand **Applications** and click **Virtual K8s**.                      |
+---------------------------------------------------------------------------------------------------------------+
| 4. Verify that a vK8s object exists in your namespace and the **Current State** column shows **Ready**.      |
|                                                                                                               |
| .. note::                                                                                                     |
|    *Initial vK8s provisioning can take 5-10 minutes. If the state shows as provisioning, wait a few*         |
|    *minutes and refresh the page. If the vK8s object is not visible or not in Ready state after 10*          |
|    *minutes, contact your lab instructor.*                                                                   |
+---------------------------------------------------------------------------------------------------------------+
| 5. Click on the **...** (Actions menu) for your vK8s object and select **Kubeconfig** to verify that you     |
|                                                                                                               |
|    can download the kubeconfig file.                                                                          |
|                                                                                                               |
| .. note::                                                                                                     |
|    *You do not need to download the kubeconfig at this time. This step simply verifies that the download*    |
|    *capability is available. The kubeconfig will be used in later lab modules for application deployment.*   |
+---------------------------------------------------------------------------------------------------------------+

Task 4: Lab Workflow Overview
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The following section provides an overview of the end-to-end DevSecOps workflow that will be 
implemented throughout this lab series.

+---------------------------------------------------------------------------------------------------------------+
| **Complete DevSecOps Pipeline Architecture**                                                                 |
+===============================================================================================================+
| **Phase 1: Code**                                                                                             |
|                                                                                                               |
| * Develop application code using AI-assisted coding capabilities in VS Code Server                           |
| * Leverage code suggestions, auto-completion, and intelligent refactoring                                    |
| * Commit code changes to GitLab repository with version control                                              |
| * Trigger automated CI/CD pipelines on code commits                                                          |
+---------------------------------------------------------------------------------------------------------------+
| **Phase 2: Build & Deploy**                                                                                   |
|                                                                                                               |
| * GitLab CI/CD pipeline executes automated builds and tests                                                  |
| * Terraform provisions infrastructure on F5 Distributed Cloud (security policies, load balancers)            |
| * Application containers deploy to vK8s across distributed Customer Edge sites                               |
| * Automatic workload distribution and scaling across geographic locations                                    |
+---------------------------------------------------------------------------------------------------------------+
| **Phase 3: Secure**                                                                                           |
|                                                                                                               |
| * F5 Distributed Cloud Web Application Firewall (WAF) protects against OWASP Top 10 threats                  |
| * API Security enforcement with schema validation and rate limiting                                          |
| * Distributed DDoS mitigation at the edge, close to attack sources                                           |
| * Bot defense and credential stuffing protection                                                             |
| * Continuous security monitoring and threat intelligence                                                     |
+---------------------------------------------------------------------------------------------------------------+
| **Phase 4: Monitor & Iterate**                                                                                |
|                                                                                                               |
| * Real-time application performance monitoring and analytics                                                 |
| * Security event correlation and incident response                                                           |
| * Implement security policy updates via Terraform Infrastructure as Code                                     |
| * Test security controls effectiveness with simulated attacks                                                |
| * Continuous improvement of security posture                                                                 |
+---------------------------------------------------------------------------------------------------------------+
| **Lab Series Objectives**                                                                                     |
|                                                                                                               |
| Throughout this lab series, you will:                                                                         |
|                                                                                                               |
| * Experience AI-accelerated application development workflows                                                 |
| * Implement Infrastructure as Code with Terraform for F5 Distributed Cloud                                   |
| * Deploy applications across distributed edge locations using vK8s                                            |
| * Configure comprehensive application security controls including WAF, API security, and DDoS protection     |
| * Validate end-to-end security posture through testing and monitoring                                        |
| * Master the DevSecOps approach of integrating security throughout the development lifecycle                 |
|                                                                                                               |
| **Total Lab Series Duration: 90-120 minutes**                                                                 |
+---------------------------------------------------------------------------------------------------------------+

+---------------------------------------------------------------------------------------------------------------+
| **End of Lab 1**                                                                                              |
+===============================================================================================================+
| This concludes Lab 1. In this lab, you verified access to all required lab components including VS Code       |
|                                                                                                               |
| Server, GitLab CE, and F5 Distributed Cloud tenant. You confirmed that pre-configured objects including       |
|                                                                                                               |
| namespaces, Customer Edge sites, Virtual Sites, and Virtual Kubernetes clusters are ready for use. You also   |
|                                                                                                               |
| reviewed the complete DevSecOps workflow that will be implemented in subsequent lab modules.                   |
|                                                                                                               |
| A fully accessible environment is required before proceeding to Lab 2. If you encountered any issues during   |
|                                                                                                               |
| verification, please contact your lab instructor for assistance.                                               |
|                                                                                                               |
| **You may now proceed to Lab 2: AI-Assisted Application Development**                                         |
+---------------------------------------------------------------------------------------------------------------+