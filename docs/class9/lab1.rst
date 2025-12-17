Lab 01 - Module 01: Environment Verification
============================================

Task 1: Verify Access
=====================

**Objective:** Validate access to all required lab components and understand the end-to-end workflow.

Prerequisites
-------------

* Lab credentials provided by instructor
* Modern web browser (Chrome, Firefox, or Edge)
* Active internet connection

Access Verification Checklist
------------------------------

Visual Studio Code Server
~~~~~~~~~~~~~~~~~~~~~~~~~~

**Purpose:** Browser-based development environment with integrated Terraform CLI.

1. Navigate to the provided VS Code Server URL
2. Authenticate using lab credentials
3. **Verify:** Terminal access is available (View → Terminal)
4. **Verify:** File explorer displays workspace directory

GitLab Community Edition
~~~~~~~~~~~~~~~~~~~~~~~~~

**Purpose:** Source code repository and CI/CD pipeline management.

1. Access GitLab CE at the provided URL
2. Sign in with lab credentials
3. **Verify:** Project repository is visible
4. **Verify:** Repository contains initial application code

F5 Distributed Cloud Tenant
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Purpose:** SaaS-based control plane for application security and delivery.

Access the F5 Distributed Cloud Console at: ``https://<tenant-name>.console.ves.volterra.io``

**Verify Pre-Created Objects:**

**Namespaces**

1. Navigate to **Administration → Personal Management → My Namespaces**
2. **Verify:** Your assigned namespace is listed and accessible
3. **Note:** Namespace format typically follows: ``<firstname-lastname>`` or lab-specific naming

**Customer Edge (CE) Sites and Virtual Sites**

1. Navigate to **Multi-Cloud Network Connect → Sites → Site List**
2. **Verify:** Customer Edge sites show "ONLINE" status
3. Navigate to **Shared Configuration → Virtual Sites**
4. **Verify:** Virtual site contains your assigned CE sites
5. **Note:** Virtual sites group physical sites for workload deployment

**Virtual Kubernetes (vK8s)**

1. Navigate to **Distributed Apps → Applications → Virtual K8s**
2. **Verify:** vK8s object exists in your namespace
3. **Verify:** Current State shows "Ready"
4. Click **"..." → Kubeconfig** to confirm kubeconfig download capability
5. **Note:** Each vK8s object is associated with a virtual site for distributed application deployment

Terraform CLI Verification
~~~~~~~~~~~~~~~~~~~~~~~~~~~

**Purpose:** Infrastructure as Code (IaC) tool for automating F5 BIG-IP and XC deployments.

Execute in VS Code Server terminal:

.. code-block:: bash

   # Verify Terraform installation
   terraform version
   
   # Expected output: Terraform v1.5.x or higher

**Verify:** Version information displays without errors

Lab Workflow Overview
---------------------

**High-Level Architecture:**

This lab demonstrates a complete DevSecOps pipeline:

1. **Code Phase**
   
   * Develop application code in VS Code Server
   * Leverage AI-assisted coding capabilities
   * Commit code to GitLab repository

2. **Build & Deploy Phase**
   
   * GitLab CI/CD pipeline triggers automated builds
   * Terraform provisions infrastructure on F5 Distributed Cloud
   * Application deploys to vK8s across distributed sites

3. **Secure Phase**
   
   * F5 Distributed Cloud Web Application Firewall (WAF) protection
   * API security enforcement
   * Distributed DDoS mitigation
   * Continuous security monitoring

4. **Iterate Phase**
   
   * Monitor application performance
   * Implement security policy updates via Terraform
   * Test security controls effectiveness

**Lab Objectives:**

* Experience AI-accelerated application development
* Implement Infrastructure as Code with Terraform
* Deploy applications across distributed edge locations
* Configure comprehensive application security controls
* Validate end-to-end security posture

**Expected Duration:** 90-120 minutes across all lab modules

Troubleshooting
---------------

**Cannot Access VS Code Server**

* Verify URL is correct and includes protocol (https://)
* Clear browser cache and cookies
* Try incognito/private browsing mode

**F5 Distributed Cloud Console Login Issues**

* Check spam folder for invitation email
* Verify credentials match case-sensitive format
* Contact lab instructor for password reset

**Terraform Command Not Found**

* Verify PATH environment variable includes Terraform binary
* Restart VS Code Server terminal
* Contact lab support if issue persists

**vK8s Status Not Ready**

* Initial provisioning requires 5-10 minutes
* Refresh console page
* Verify virtual site contains healthy CE sites

Next Steps
----------

Proceed to **Lab 01 - Module 02** to begin application development and deployment.

Additional Resources
--------------------

* `F5 Distributed Cloud Documentation <https://docs.cloud.f5.com/docs-v2>`_
* `Virtual Kubernetes Guide <https://docs.cloud.f5.com/docs-v2/distributed-apps/how-to/app-mgnt/create-vk8s-obj>`_
* `Terraform F5 Provider <https://registry.terraform.io/providers/F5Networks/bigip/latest/docs>`_