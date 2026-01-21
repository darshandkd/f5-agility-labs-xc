Module 1: AI-Generated Vulnerable App (Demo Only)
=================================================

This module is a demonstration of **AI-assisted "Vibe Coding"** and how it can introduce
typical flaws and vulnerabilities. You will generate a vulnerable application using pre-canned
prompts and observe both the benefits and security risks of AI-generated code.

The goal of this module is to:

* Generate a simple vulnerable application (demo-only)
* Observe the benefits through the use of VSCode with Cline Extension and see how files and code are generated
* Point out the flaws and vulnerabilities of AI-assisted coding and Vibe Coding

.. warning::
   **Critical: Understanding Vibe Coding Risks**

   "Vibe Coding" refers to AI-assisted development where developers accept AI-generated code without
   immediate security validation. Recent studies show **~45% of AI-generated code samples contain known
   vulnerabilities** including SQL injection, XSS, and hardcoded secrets. This module demonstrates why
   security oversight is essential in AI-assisted workflows.

.. note::
   **Throwaway Demo vs. Production Code**

   The application generated in this module is a **throwaway demonstration** designed solely to highlight
   AI coding flaws. It is NOT used in subsequent labs. In Module 2, you will work with a **pre-vetted**
   (but still intentionally vulnerable) application that has been prepared for the CI/CD pipeline exercises.

**Expected Lab Time: 15-20 minutes**

Task 1: Explore Cline Extension and Generate Vulnerable App
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The following steps will allow you to explore the VSCode environment and the Cline Extension
configuration. You will then use AI to generate a vulnerable application to understand the risks
associated with Vibe Coding.

+---------------------------------------------------------------------------------------------------------------+
| **Access VSCode Server**                                                                                      |
+===============================================================================================================+
| 1. Open your browser and navigate to the VSCode Server URL provided in your lab environment. Verify that      |
|                                                                                                               |
|    VSCode loads successfully in your browser.                                                                 |
|                                                                                                               |
| |module1-vscode_browser|                                                                                      |
+---------------------------------------------------------------------------------------------------------------+
| 2. Familiarize yourself with the VSCode interface. Note the sidebar icons for file explorer, search, source   |
|                                                                                                               |
|    control, and extensions.                                                                                   |
|                                                                                                               |
| |module1-vscode_interface|                                                                                    |
+---------------------------------------------------------------------------------------------------------------+

+---------------------------------------------------------------------------------------------------------------+
| **Explore Cline Extension Configuration**                                                                     |
+===============================================================================================================+
| 1. In VSCode, locate the **Cline Extension** in the sidebar. Click on the Cline icon to open the extension    |
|                                                                                                               |
|    panel.                                                                                                     |
|                                                                                                               |
| |module1-cline_sidebar|                                                                                       |
+---------------------------------------------------------------------------------------------------------------+
| 2. Review the Cline Extension configuration settings. Verify the following settings are configured:           |
|                                                                                                               |
|    * **API Provider:** *GCP Vertex AI*                                                                        |
|    * **Google Cloud Project ID:** *f5-gcs-4261-sales-appworld2026*                                            |
|    * **Model:** *gemini-2.5-flash*                                                                            |
|                                                                                                               |
| |module1-cline_config|                                                                                        |
|                                                                                                               |
| .. note::                                                                                                     |
|    *The Cline Extension has been pre-configured with access to Gemini 2.5 flash using a GCP service account.* |
|    *Your instructor will provide the Project ID if needed.*                                                   |
+---------------------------------------------------------------------------------------------------------------+
| 3. Explore the Cline Extension capabilities by reviewing the available options and commands in the panel.     |
|                                                                                                               |
| |module1-cline_capabilities|                                                                                  |
+---------------------------------------------------------------------------------------------------------------+

+---------------------------------------------------------------------------------------------------------------+
| **Understand Cline Plan vs Act Mode**                                                                         |
+===============================================================================================================+
| 1. Before generating code, understand the difference between Cline's **Plan** and **Act** modes:              |
|                                                                                                               |
|    * **Plan Mode:** The AI analyzes the request and proposes a plan of action without executing changes.      |
|      This allows you to review the AI's decision-making process before any code is written.                   |
|    * **Act Mode:** The AI executes the plan, creating files and writing code directly.                        |
|                                                                                                               |
| |module1-cline-start-new-task|                                                                                |
|                                                                                                               |
| .. note::                                                                                                     |
|    *Understanding Plan vs Act is critical for safe Vibe Coding. Plan mode gives you visibility into what*     |
|    *the AI intends to do, while Act mode executes those intentions. Security-conscious developers should*     |
|    *always review the Plan before allowing the AI to Act.*                                                    |
+---------------------------------------------------------------------------------------------------------------+
| 2. Notice the **Plan** and **Act** toggle in the bottom-right corner of the Cline panel. When **Plan** is     |
|                                                                                                               |
|    selected (highlighted), the AI will only propose a plan without making changes.                            |
|                                                                                                               |
| |client-demo-app-plan|                                                                                        |
+---------------------------------------------------------------------------------------------------------------+
| 3. After submitting a prompt in **Plan** mode, the AI will respond with its proposed plan and ask if you      |
|                                                                                                               |
|    want to proceed to **Act Mode** to execute the changes.                                                    |
|                                                                                                               |
| |client-demo-app-plan-response|                                                                               |
+---------------------------------------------------------------------------------------------------------------+
| 4. Click **Start New Task** in the Cline panel to begin a new AI interaction.                                 |
|                                                                                                               |
| |module1-cline_prompt_input|                                                                                  |
+---------------------------------------------------------------------------------------------------------------+

+---------------------------------------------------------------------------------------------------------------+
| **Generate Vulnerable Application Using AI**                                                                  |
+===============================================================================================================+
| 1. In the Cline Extension panel, enter the following **pre-canned prompt** to generate a vulnerable           |
|                                                                                                               |
|    application. Make sure the Cline toggle is set to **Plan**:                                                |
|                                                                                                               |
| .. code-block:: text                                                                                          |
|                                                                                                               |
|    ==============================================                                                              |
|    Create a simple Flask web application for demo purposes (Module 1 - AppWorld 2026 vibe-coding demo).       |
|                                                                                                               |
|    High-level goal:                                                                                           |
|    - A small, polished "conference-style" site inspired by AppWorld 2026 themes (apps, APIs, AI,              |
|      hands-on learning).                                                                                      |
|    - IMPORTANT: Do NOT copy text verbatim from any website. Paraphrase into original wording.                 |
|                                                                                                               |
|    Requirements:                                                                                               |
|    - Use Python Flask.                                                                                        |
|    - No authentication, no database, no external APIs.                                                        |
|    - Single Flask app file named app.py.                                                                      |
|    - Use Jinja2 templates.                                                                                    |
|    - Create a modern, clean UI using Tailwind CSS via CDN (do NOT install Tailwind locally).                  |
|    - App should be visually appealing but simple.                                                             |
|    - Do not use the echo or open commands.                                                                    |
|                                                                                                               |
|    Pages / behavior:                                                                                          |
|    1) Home page (/)                                                                                           |
|    - A top navigation bar with links: Home, Agenda, About.                                                    |
|    - A centered hero section:                                                                                 |
|      - Title: "AppWorld 2026 - Code. Secure. Repeat."                                                         |
|      - Subtitle: A short, original (paraphrased) blurb about learning to build, deliver, and protect          |
|        apps/APIs/AI with hands-on labs.                                                                       |
|    - A primary CTA button linking to /agenda.                                                                 |
|    - 3 feature cards in a responsive grid (each with title + 2-3 bullet points):                              |
|      - "Build Faster" (AI-assisted dev + CI/CD vibe, phrased generically)                                     |
|      - "Secure by Design" (WAAP, API security, bot defense themes, phrased generically)                       |
|      - "Repeatable Workflow" ("Code. Secure. Repeat." loop, phrased generically)                              |
|    - A small "Highlights" strip below the cards with 3 quick stats (static placeholders):                     |
|      - "3 Modules", "Hands-on Demos", "WAAP + API Security"                                                   |
|                                                                                                               |
|    2) Agenda page (/agenda)                                                                                   |
|    - Show a simple agenda with 3 time blocks (static, fake times are OK):                                     |
|      - "Module 0 - Orientation"                                                                               |
|      - "Module 1 - Vibe Coding Demo"                                                                          |
|      - "Module 2/3 - Deploy + API Discovery"                                                                  |
|    - Each agenda item should have: Title, 1-2 line description, A "Track" badge                               |
|      (e.g., DevSecOps, App Delivery, API Security)                                                            |
|    - Add a tiny bit of interactivity:                                                                         |
|      - Support a query string filter like /agenda?track=API                                                   |
|      - If track is provided, filter agenda items server-side and show "Filtered by: ..."                      |
|      - Provide 3 filter links/buttons at top: All, DevSecOps, API, Delivery.                                  |
|                                                                                                               |
|    3) About page (/about)                                                                                     |
|    - A short paragraph explaining:                                                                            |
|      - This is a demo-only app for a lab.                                                                     |
|      - It intentionally stays simple (no auth/db).                                                            |
|      - It exists to demonstrate AI-generated code + UI scaffolding.                                           |
|    - Add a small callout panel: "Lab note: This demo is not the production app used in later modules."        |
|                                                                                                               |
|    UI / layout:                                                                                               |
|    - Use templates/base.html for layout (nav + footer).                                                       |
|    - Use templates/index.html, templates/agenda.html, templates/about.html extending base.                    |
|    - Add a footer with small text: "Demo app for AppWorld 2026 lab - Code. Secure. Repeat."                   |
|                                                                                                               |
|    Technical requirements:                                                                                    |
|    - Flask app must bind to 0.0.0.0.                                                                          |
|    - App must be runnable with: flask run --host=0.0.0.0 --port=5000                                          |
|    - Keep the code readable and well-commented.                                                               |
|    - Do not include Docker, Kubernetes, CI/CD, or security features.                                          |
|                                                                                                               |
|    Deliverables:                                                                                              |
|    - app.py                                                                                                   |
|    - templates/base.html                                                                                      |
|    - templates/index.html                                                                                     |
|    - templates/agenda.html                                                                                    |
|    - templates/about.html                                                                                     |
|                                                                                                               |
|    After generating the files, explain how to run the app using flask run.                                    |
|    ==============================================                                                              |
|                                                                                                               |
| |module1-cline-demo-app-plan|                                                                                 |
+---------------------------------------------------------------------------------------------------------------+
| 2. Observe the **Plan** that Cline generates. Review the AI's proposed approach to building the application.  |
|                                                                                                               |
|    Notice how the AI plans to implement features - this is where security vulnerabilities often originate.    |
|                                                                                                               |
| |module1-cline-demo-app-plan-response|                                                                        |
|                                                                                                               |
| .. warning::                                                                                                  |
|    *Pay attention to how the AI plans to handle user inputs, database queries, and credential storage.*       |
|    *These are common areas where Vibe Coding introduces vulnerabilities.*                                     |
+---------------------------------------------------------------------------------------------------------------+
| 3. Allow Cline to **Act** and execute the plan. Watch as the AI creates files and writes code.                |
|                                                                                                               |
|    After Cline finishes coding each file, it will ask you to save the file before continuing to the           |
|    next file.                                                                                                 |
|                                                                                                               |
| |module1-cline-demo-app-act|                                                                                  |
|                                                                                                               |
| |module1-cline-demo-app-act-2|                                                                                |
+---------------------------------------------------------------------------------------------------------------+
| 4. Observe the file explorer updating as new files are created. The AI will generate multiple files           |
|                                                                                                               |
|    including:                                                                                                 |
|                                                                                                               |
|    * ``app.py`` - Flask application with routes for ``/``, ``/agenda``, and ``/about``                        |
|    * ``templates/base.html`` - Base layout template with navigation and footer                                |
|    * ``templates/index.html`` - Home page template                                                            |
|    * ``templates/agenda.html`` - Agenda page template with filter functionality                               |
|    * ``templates/about.html`` - About page template                                                           |
|                                                                                                               |
| |module1-cline-demo-app-act-3-task-completed|                                                                  |
|                                                                                                               |
| .. note::                                                                                                     |
|    *The AI may take a few minutes to generate all files. Do not interrupt the process until it completes.*    |
|    *Some student-generated applications might fail - this is expected with Vibe Coding due to the*            |
|    *non-deterministic nature of generative AI.*                                                               |
+---------------------------------------------------------------------------------------------------------------+

+---------------------------------------------------------------------------------------------------------------+
| **Run and Test the Generated Application**                                                                    |
+===============================================================================================================+
| 1. Once Cline completes code generation, open the integrated terminal in VSCode by selecting                  |
|                                                                                                               |
|    **Terminal > New Terminal**.                                                                               |
|                                                                                                               |
| |module1-cline-demo-app-terminal|                                                                             |
+---------------------------------------------------------------------------------------------------------------+
| 2. Navigate to the generated application directory (if needed) and start the Flask application:               |
|                                                                                                               |
| .. code-block:: bash                                                                                          |
|                                                                                                               |
|    flask run --host=0.0.0.0 --port=5000                                                                       |
|                                                                                                               |
| |module1-cline-demo-app-act-3-flask-command|                                                                   |
+---------------------------------------------------------------------------------------------------------------+
| 3. Verify the Flask application is running by checking for the startup message in the terminal.               |
|                                                                                                               |
| |module1-cline-demo-app-terminal-4-flask-running|                                                              |
+---------------------------------------------------------------------------------------------------------------+
| 4. Access the application using one of the following options:                                                 |
|                                                                                                               |
|    **Option 1:** Access via VSCode popup. After running the flask command, you should see a popup             |
|    from VSCode. Click **Open** and the app will open in your browser.                                         |
|                                                                                                               |
| |module1-cline-demo-app-terminal-4-vscode-access|                                                              |
|                                                                                                               |
|    **Option 2:** Access the app using the Firefox container running on the Jumphost.                          |
|                                                                                                               |
| |module1-cline-demo-app-terminal-4-firefox|                                                                    |
|                                                                                                               |
| .. note::                                                                                                     |
|    *If you see a Chrome pop-up, select Firefox as your browser for this lab.*                                 |
|                                                                                                               |
| |module1-cline-demo-app-terminal-4-chrome-popup|                                                               |
+---------------------------------------------------------------------------------------------------------------+
| 5. Enter the application URL in Firefox's address bar.                                                        |
|                                                                                                               |
| |module1-cline-demo-app-terminal-4-firefox-address|                                                            |
+---------------------------------------------------------------------------------------------------------------+

+---------------------------------------------------------------------------------------------------------------+
| **Review Generated Code and Identify Vulnerabilities**                                                        |
+===============================================================================================================+
| 1. Return to VSCode and open the generated files to review the code structure. Click on each file in the      |
|                                                                                                               |
|    explorer to view its contents.                                                                             |
|                                                                                                               |
| |module1-review_code|                                                                                         |
+---------------------------------------------------------------------------------------------------------------+
| 2. Identify potential security vulnerabilities in the generated code. Common vulnerabilities in AI-generated  |
|                                                                                                               |
|    code include:                                                                                              |
|                                                                                                               |
|    * **SQL Injection (SQLi):** Unsanitized user inputs in database queries                                    |
|    * **Cross-Site Scripting (XSS):** Improper output encoding in templates                                    |
|    * **Log Injection:** Unsanitized data written to logs                                                      |
|    * **Hardcoded Secrets:** API keys or credentials embedded directly in code                                 |
|                                                                                                               |
|                                                                                                               |
|                                                                                                               |
| .. warning::                                                                                                  |
|    *This is the core danger of Vibe Coding: the AI creates functional code that appears correct but*          |
|    *contains serious security flaws. Without proper review, these vulnerabilities would reach production.*    |
+---------------------------------------------------------------------------------------------------------------+
| 3. Your instructor will demonstrate a pre-scanned application using F5XC WAS to show the types of             |
|                                                                                                               |
|    vulnerabilities detected in AI-generated code.                                                             |
|                                                                                                               |
|                                                                                                               |
+---------------------------------------------------------------------------------------------------------------+

+---------------------------------------------------------------------------------------------------------------+
| **Clean Up Demo Application**                                                                                 |
+===============================================================================================================+
| 1. Stop the running Flask application by pressing **Ctrl+C** in the terminal.                                 |
|                                                                                                               |
| |module1-cline-demo-app-terminal-ctrlc-close|                                                                  |
+---------------------------------------------------------------------------------------------------------------+
| 2. This demo application will not be used in subsequent modules. In Module 2, you will work with a            |
|                                                                                                               |
|    **pre-vetted vulnerable application** that has been prepared for the CI/CD pipeline exercises.             |
|                                                                                                               |
| |module1-cline-demo-app-cleanup|                                                                               |
+---------------------------------------------------------------------------------------------------------------+

+---------------------------------------------------------------------------------------------------------------+
| **Objective Check: Code. Secure. Repeat.**                                                                    |
+===============================================================================================================+
| In this task, you completed the **CODE** phase of the DevSecOps loop:                                         |
|                                                                                                               |
|    ✓ **CODE (AI-assisted):** You used Cline Extension to generate application code                            |
|    ✓ **Observed Vibe Coding risks:** You saw how AI introduces vulnerabilities                                |
|    ✓ **Understood Plan vs Act:** You learned to review AI decisions before execution                          |
|                                                                                                               |
| **Next Steps:** In Module 2, you will **COMMIT** code to GitLab, trigger **SCAN** (SAST), and **PROTECT**     |
| the application with F5XC WAAP - completing the security loop.                                                |
|                                                                                                               |
|    **Code → Commit → Scan → Protect → Improve → Repeat**                                                      |
+---------------------------------------------------------------------------------------------------------------+

+---------------------------------------------------------------------------------------------------------------+
| **End of Module 1**                                                                                           |
+===============================================================================================================+
| This concludes Module 1. In this module, you learned about AI-assisted coding using the Cline Extension and   |
|                                                                                                               |
| observed how AI can introduce security vulnerabilities into generated code. Key takeaways:                    |
|                                                                                                               |
|    * AI coding assistants boost productivity but require security oversight                                   |
|    * Vibe Coding (accepting AI suggestions without review) introduces significant security risks              |
|    * Understanding Plan vs Act modes helps you review AI decisions before execution                           |
|    * DevSecOps practices are essential to catch vulnerabilities introduced by AI-assisted development         |
|                                                                                                               |
| Proceed to **Module 2** to deploy and secure the vulnerable application using F5 Distributed Cloud.           |
|                                                                                                               |
|                                                                                                               |
+---------------------------------------------------------------------------------------------------------------+

.. |module1-vscode_browser| image:: ../_static/module1-vscode_browser.png
   :width: 800px
.. |module1-vscode_interface| image:: ../_static/module1-vscode_interface.png
   :width: 800px
.. |module1-cline_sidebar| image:: ../_static/module1-cline_sidebar.png
   :width: 800px
.. |module1-cline_config| image:: ../_static/module1-cline_config.png
   :width: 800px
.. |module1-cline_capabilities| image:: ../_static/module1-cline_capabilities.png
   :width: 800px
.. |module1-cline-start-new-task| image:: ../_static/module1-cline-start-new-task.png
   :width: 800px
.. |client-demo-app-plan| image:: ../_static/client-demo-app-plan.png
   :width: 800px
.. |client-demo-app-plan-response| image:: ../_static/client-demo-app-plan-response.png
   :width: 800px
.. |module1-cline_prompt_input| image:: ../_static/module1-cline_prompt_input.png
   :width: 800px
.. |module1-cline-demo-app-plan| image:: ../_static/module1-cline-demo-app-plan.png
   :width: 800px
.. |module1-cline-demo-app-plan-response| image:: ../_static/module1-cline-demo-app-plan-response.png
   :width: 800px
.. |module1-cline-demo-app-act| image:: ../_static/module1-cline-demo-app-act.png
   :width: 800px
.. |module1-cline-demo-app-act-2| image:: ../_static/module1-cline-demo-app-act-2.png
   :width: 800px
.. |module1-cline-demo-app-act-3-task-completed| image:: ../_static/module1-cline-demo-app-act-3-task-completed.png
   :width: 800px
.. |module1-cline-demo-app-terminal| image:: ../_static/module1-cline-demo-app-terminal.png
   :width: 800px
.. |module1-cline-demo-app-act-3-flask-command| image:: ../_static/module1-cline-demo-app-act-3-flask-command.png
   :width: 800px
.. |module1-cline-demo-app-terminal-4-flask-running| image:: ../_static/module1-cline-demo-app-terminal-4-flask-running.png
   :width: 800px
.. |module1-cline-demo-app-terminal-4-vscode-access| image:: ../_static/module1-cline-demo-app-terminal-4-vscode-access.png
   :width: 800px
.. |module1-cline-demo-app-terminal-4-firefox| image:: ../_static/module1-cline-demo-app-terminal-4-firefox.png
   :width: 800px
.. |module1-cline-demo-app-terminal-4-chrome-popup| image:: ../_static/module1-cline-demo-app-terminal-4-chrome-popup.png
   :width: 800px
.. |module1-cline-demo-app-terminal-4-firefox-address| image:: ../_static/module1-cline-demo-app-terminal-4-firefox-address.png
   :width: 800px
.. |module1-review_code| image:: ../_static/module1-review_code.png
   :width: 800px
.. |module1-vulnerabilities| image:: ../_static/module1-vulnerabilities.png
   :width: 800px
.. |module1-was_scan_results| image:: ../_static/module1-was_scan_results.png
   :width: 800px
.. |module1-cline-demo-app-terminal-ctrlc-close| image:: ../_static/module1-cline-demo-app-terminal-ctrlc-close.png
   :width: 800px
.. |module1-cline-demo-app-cleanup| image:: ../_static/module1-cline-demo-app-cleanup.png
   :width: 800px
.. |labend| image:: ../_static/labend.png
   :width: 800px