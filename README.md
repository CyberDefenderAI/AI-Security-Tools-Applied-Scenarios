# AI in Cybersecurity

A curated, comprehensive, and deeply detailed list of open-source tools, applications, and practical use cases leveraging Artificial Intelligence (AI), Machine Learning (ML), and Large Language Models (LLMs) to solve complex information security challenges.

As the threat landscape evolves from manual exploitation to automated, AI-driven attacks, defending digital infrastructure requires a paradigm shift. Moving beyond deterministic, signature-based rulesets, modern cybersecurity relies on probabilistic semantic understanding, anomaly detection via deep neural networks, and generative AI for rapid incident response. This repository categorizes the ecosystem into actionable tools, frameworks, and deep methodological use cases.

## 📑 Table of Contents

1. [Tools and Applications](#-tools-and-applications)
   * [IDE Plugins](#ide-plugins)
   * [Browser Plugins](#browser-plugins)
   * [CLI Plugins](#cli-plugins)
   * [Chatbots & Local Models](#chatbots--local-models)
   * [Personal Assistants & Security Agents](#personal-assistants--security-agents)
   * [MCP Servers (Model Context Protocol)](#mcp-servers-model-context-protocol)
2. [Application Scenarios & Use Cases](#-application-scenarios--use-cases)
   * [Signature Analysis](#signature-analysis)
   * [Code Quality and Linting](#code-quality-and-linting)
   * [Vulnerability Analysis & Reverse Engineering](#vulnerability-analysis--reverse-engineering)
   * [Automated Pentesting](#automated-pentesting)
   * [Anomaly Detection](#anomaly-detection)
   * [Pattern Recognition](#pattern-recognition)
   * [Incident Management & SOAR](#incident-management--soar)
   * [Threat Modeling](#threat-modeling)
   * [Fraud Detection](#fraud-detection)
   * [Translation & Localization](#translation--localization)
   * [Summarization & Alert Triage](#summarization--alert-triage)

---

## 🛠️ Tools and Applications

### IDE Plugins
Integrating AI directly into the Integrated Development Environment (IDE) represents the ultimate "Shift-Left" security approach. By identifying vulnerabilities during the coding phase, organizations drastically reduce remediation costs and prevent insecure code from ever reaching the continuous integration pipeline.

* **[Codium-ai/pr-agent](https://github.com/Codium-ai/pr-agent):**
 An open-source, AI-powered tool for automated Pull Request (PR) analysis. Instead of just checking syntax, it uses LLMs to understand the semantic intent of the PR. It automatically generates descriptions, reviews the code for logic bugs, identifies missing security test cases, and specifically hunts for common OWASP vulnerabilities before the code is merged into the main branch.
* **GitHub Copilot / GitHub Advanced Security:**
Beyond functioning as a pair programmer, Copilot can be explicitly prompted to act as a rigorous security auditor. Developers can highlight a block of code and command the AI to "Find potential Cross-Site Scripting (XSS) or SQL Injection vulnerabilities in this function and rewrite it using parameterized queries." It contextually understands the framework being used (e.g., React, Django) and suggests framework-specific secure coding practices.
* **Snyk Code / DeepCode AI:**
Powered by a hybrid approach combining symbolic logic and machine learning, this engine performs real-time Static Application Security Testing (SAST). It was trained on millions of open-source commits and their subsequent vulnerability patches. This allows the AI to recognize insecure architectural patterns (like hardcoded secrets or improper access control configurations) rather than relying on brittle, traditional Regex rules, resulting in dramatically fewer false positives.

* **Bito / Tabnine:** These plugins offer privacy-centric AI assistance. They allow security engineers to quickly highlight obfuscated or suspicious code snippets and query the AI (e.g., "Explain the security implications of this encryption implementation") without the data leaving corporate boundaries, depending on the chosen deployment model.

### Browser Plugins
Extensions designed to protect end-users in real-time, facilitate Open Source Intelligence (OSINT) gathering, and provide on-the-fly threat analysis directly within the web browser using computer vision and natural language processing.

* **[browser-use/browser-use](https://github.com/browser-use/browser-use):**
An open-source framework that makes websites accessible to AI agents. In a security context, this can be utilized to build custom browser extensions or headless agents that autonomously navigate suspicious websites, interact with phishing portals to extract drop-server endpoints, and analyze malicious DOM structures without risking human analyst exposure.
* **SquareX:** A disposable browser extension designed for secure computing. It uses AI to determine if a downloaded file or a visited link is malicious. Instead of just blocking it, it allows users to open suspicious documents or websites in a disposable, cloud-based micro-VM (sandbox), completely isolating the endpoint from potential zero-day exploits.

* **Aura / Guardio:** Moving beyond traditional static blocklists, these extensions utilize active machine learning models and computer vision. They analyze the DOM structure, visual layout, and natural language of a webpage in real-time to detect sophisticated phishing campaigns that use brand-new domains to bypass standard reputation filters.

* **Harpa AI / Web ChatGPT Extensions:** Highly utilized by Threat Intelligence analysts for OSINT. These tools can parse long threat advisories, extract Indicators of Compromise (IoCs) like IP addresses and file hashes directly from web pages, and summarize zero-day vulnerability write-ups without requiring the analyst to manually comb through blocks of text.

### CLI Plugins
Command-Line Interface tools that bring the power of LLMs directly to the terminal, automating bash scripting, complex log parsing, and infrastructure orchestration.

* **[danielmiessler/fabric](https://github.com/danielmiessler/fabric):**
A groundbreaking open-source framework specifically tailored for cybersecurity professionals and hackers. Fabric uses a system of meticulously crafted "patterns" (highly optimized system prompts). You can pipe the raw, messy output of traditional security tools directly into Fabric. For example, piping raw `nmap` XML output or `amass` subdomains into a pattern like `extract_endpoints` or `find_hidden_params` yields instantly structured, actionable markdown reports.
* **[TheR1D/shell_gpt](https://github.com/TheR1D/shell_gpt):**
Allows security engineers to bypass complex syntax memorization. By querying in natural language, users can instantly generate and execute complex CLI commands. A SecOps engineer can type: `sgpt "Write an iptables rule to drop all incoming TCP traffic from subnet 192.168.1.0/24 except port 22, and log the dropped packets"`. The AI generates the exact bash command, drastically speeding up incident response times.

* **GitHub CLI (`gh copilot`):** An extension for the GitHub CLI that helps DevSecOps engineers quickly write workflow automation scripts, formulate complex GitHub Advanced Security API queries, and manage secrets across repositories directly from the terminal.


### Chatbots & Local Models
General-purpose Large Language Models utilized as highly versatile, interactive expert systems for security research, malware analysis, and data processing.

* **[ollama/ollama](https://github.com/ollama/ollama) & [lmstudio-ai](https://github.com/lmstudio-ai):**
For security operations, sending sensitive logs or proprietary source code to a public API (like OpenAI) is often a severe compliance violation. Ollama allows security teams to run powerful, quantized open-source LLMs (like Llama 3, Mistral, or specialized coding models) entirely locally on their own hardware. This enables air-gapped, privacy-preserving AI analysis of highly confidential incident data.
* **Claude 3 (Opus/Sonnet by Anthropic):** Currently a favorite in the infosec community due to its massive context window (200k+ tokens). Analysts can drop entire decompiled codebases, massive raw PCAP (packet capture) files, or extensive JSON system logs into the chat and ask the model to trace the execution path of a malware sample or find the initial point of compromise in the logs.

* **ChatGPT (OpenAI - Advanced Data Analysis):** Exceptional at writing and executing Python code in a sandboxed environment. Security researchers use it to upload encrypted payloads or obfuscated scripts; the model can iteratively write decryption routines, execute them, and provide the deobfuscated output, effectively acting as an automated malware analysis lab.

* **Google Gemini (Advanced):** Deeply integrated with Google's ecosystem and threat intelligence feeds (Mandiant). It excels at synthesizing vast amounts of unstructured threat data, helping analysts quickly connect the dots between emerging threat actor campaigns and specific technical indicators.

### Personal Assistants & Security Agents
Specialized, deeply integrated autonomous AI agents built explicitly for Security Operations Centers (SOCs) and offensive security teams (Red Teams).

* **[GreyDGL/PentestGPT](https://github.com/GreyDGL/PentestGPT):**
An interactive LLM-wrapper designed to act as a senior Red Team orchestrator. It does not blindly fire exploits; instead, it maintains engagement state, tracks the penetration test's progress, ingests stdout from various tools (like `nmap`, `gobuster`, `sqlmap`), builds a structural attack tree in its memory, and suggests the next logical exploitation steps based on the unique environmental context.
* **[aress31/burpgpt](https://github.com/aress31/burpgpt):**
An extension for Burp Suite Professional that integrates OpenAI's API. It passively sends HTTP requests and responses to the LLM to identify complex, logic-based vulnerabilities that traditional dynamic scanners (DAST) miss. It can spot bespoke privilege escalation vectors, IDORs, and insecure API architectures by analyzing the semantic meaning of HTTP parameters.
* **Microsoft Copilot for Security:** An enterprise-grade AI assistant deeply integrated into the Microsoft Security ecosystem (Sentinel, Defender). It can automatically translate natural language questions into complex Kusto Query Language (KQL), orchestrate threat hunting across endpoints, summarize active incidents, and even reverse-engineer malicious PowerShell scripts found on compromised hosts.

* **PentestGPT:** An interactive LLM-wrapper designed to guide penetration testers. It does not blindly attack systems; instead, it maintains state, tracks the engagement's progress, ingests outputs from various tools, builds a structural attack tree, and suggests the next logical exploitation steps, acting as a senior Red Team orchestrator.

### MCP Servers (Model Context Protocol)
MCP is an emerging open standard championed by Anthropic that allows AI models to securely connect to local and remote data sources, giving them real-time access to corporate security infrastructure.

* **[modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers):**
MCP servers act as a secure bridge between an LLM and a company's internal tools. In a security context, developers build MCPs to connect to SIEMs (Splunk, Elastic) or EDRs (CrowdStrike). An analyst can ask their local AI assistant, "Find all anomalous lateral movement attempts originating from the HR subnet in the last 24 hours." The LLM uses the MCP tool to autonomously construct the query, fetch the live data securely, and summarize the findings, all without the raw logs ever leaving the corporate boundary.
* **Local SIEM & EDR MCPs:** Servers that bridge Claude (or other compatible LLMs) directly to internal Splunk, ElasticSearch, or CrowdStrike instances. An analyst can ask the AI, "Find all anomalous lateral movement attempts in the last 24 hours." The MCP translates this, queries the local SIEM, and returns the data to the LLM for summarization, keeping the raw logs securely on-premise.

* **OSINT & Threat Intel MCPs:** Connections to external APIs like Shodan, VirusTotal, or AlienVault OTX. When an analyst asks about a specific IP address in an AI chat, the model autonomously queries these MCP servers to fetch real-time reputation scores, open ports, and historical malware associations to enrich its answer dynamically.

---

## 🎯 Application Scenarios & Use Cases

### Signature Analysis
AI drastically accelerates the creation, optimization, and translation of detection rules used by firewalls, Intrusion Detection Systems (IDS), and enterprise antivirus engines.

* **Automated Rule Generation:** Instead of manually writing complex syntax, analysts can provide an LLM with a technical description of a novel attack or a raw malware memory dump. The AI can instantly generate highly accurate, functionally valid `YARA` rules for file scanning, `Suricata` rules for network traffic, or [Sigma](https://github.com/SigmaHQ/sigma) rules for SIEM event logs.
* **Regex Optimization & ReDoS Prevention:** Security tools heavily rely on Regular Expressions for parsing logs and blocking WAF payloads. AI can analyze and optimize poorly written regex to prevent Regular Expression Denial of Service (ReDoS) vulnerabilities, ensuring high-performance packet inspection that doesn't consume excessive CPU cycles.

### Code Quality and Linting
Moving beyond simple Abstract Syntax Tree (AST) checking, AI provides deep, context-aware semantic analysis of source code architectures.

* **Complex Logic Flaw Detection:** Traditional tools rely on known vulnerable patterns. LLMs can review Pull Requests and identify complex business logic flaws. For example, it can understand that a developer forgot to implement a rate-limiting mechanism on a newly created password reset API endpoint, or spot subtle race conditions in multi-threaded financial transaction code.
* **[trufflesecurity/trufflehog](https://github.com/trufflesecurity/trufflehog) Evolution:** While TruffleHog traditionally uses regex and entropy checks to find secrets, modern ML approaches use Natural Language Processing to understand the context around a string. The AI can distinguish between a high-entropy random string used in a test suite and an actual, hardcoded AWS cryptographic key, massively reducing false-positive rates in CI/CD pipelines.

### Vulnerability Analysis & Reverse Engineering
Enhancing the speed at which security researchers understand software flaws and reverse-engineer compiled malware.

* **[JusticeRage/Gepetto](https://github.com/JusticeRage/Gepetto) (IDA Pro Integration):**
Reverse engineering compiled, stripped binaries (where all function and variable names are removed) is incredibly tedious. Gepetto integrates LLMs directly into IDA Pro. The AI analyzes the raw assembly instructions and the generated pseudocode, heuristically guesses the purpose of the function (e.g., "This looks like a custom AES decryption routine"), and automatically renames variables and writes descriptive comments, saving reverse engineers dozens of hours per binary.
* **CVE Impact & Root Cause Synthesis:** When a critical Zero-Day vulnerability is published, LLMs can digest the highly technical CVE disclosure, the associated proof-of-concept (PoC) code, and the organization's internal architecture maps to assess whether the specific infrastructure is genuinely vulnerable, providing a bespoke risk score.

### Automated Pentesting
Streamlining the offensive security lifecycle by reducing manual overhead and enhancing payload sophistication and evasion techniques.

* **Custom, Context-Aware Payload Generation:** Traditional Web Application Firewalls (WAFs) easily block standard payloads (like `' OR 1=1--`). LLMs can generate highly obfuscated, polyglot payloads—malicious code that is simultaneously valid in multiple languages (e.g., valid in both JavaScript and SQL)—tailored specifically to bypass the semantic filters of a target's WAF.
* **Social Engineering & Phishing Generation:** Red Teams leverage LLMs to craft highly persuasive, context-aware spear-phishing templates. By feeding the AI public LinkedIn data and corporate press releases, it can generate flawless, localized emails that perfectly mimic the tone of a company's CEO or IT department, drastically increasing click-through rates during security awareness assessments.

### Anomaly Detection
Machine Learning architectures (like Autoencoders and Isolation Forests) excel at identifying deviations from the norm in vast, high-dimensional datasets where human analysts would be overwhelmed.

* **UEBA (User and Entity Behavior Analytics):** Unsupervised ML models continuously ingest identity and access logs to build a dynamic baseline of "normal" behavior for every single user and device. They trigger high-fidelity alerts upon detecting anomalies, such as an employee logging in from a new device in an impossible geographic location (impossible travel), or an HR representative suddenly downloading terabytes of data from secure source code repositories at 3 AM.
* **Network Traffic Analytics (NTA):** Deep learning models analyzing NetFlow and packet metadata to detect subtle deviations. They can identify low-and-slow DNS tunneling (data exfiltration hidden within DNS queries), beaconing behavior characteristic of compromised C2 communications, or unusual spikes in encrypted outbound traffic that traditional static firewalls ignore.

### Pattern Recognition
Utilizing advanced neural networks (CNNs, RNNs) to categorize and identify malicious infrastructure, domains, and communications.

* **DGA (Domain Generation Algorithm) Classification:** Botnets often generate thousands of random, disposable domain names daily to avoid static blocklists. Deep learning models analyze character entropy, consonant-to-vowel ratios, and linguistic patterns to instantly classify whether a domain like `xkqzwy123.info` is human-registered or machine-generated, blocking the botnet's communication channel in real-time.
* **Phishing and BEC Clustering:** NLP models analyze the semantics, psychological urgency, and emotional tone of emails to detect Business Email Compromise (BEC). Furthermore, by recognizing linguistic fingerprints and infrastructure reuse, ML clustering algorithms can tie seemingly isolated phishing emails back to a single, coordinated Advanced Persistent Threat (APT) group.

### Incident Management & SOAR
Accelerating the Mean Time to Respond (MTTR) by orchestrating, correlating, and responding to disparate security events autonomously.

* **Alert Triage and Correlation:** A modern SOC receives thousands of alerts daily. AI engines ingest isolated alerts from Endpoint Detection and Response (EDR) agents, firewalls, and Identity Access Management (IAM) systems. The AI correlates these alerts based on timestamps and entity relationships, weaving them into a single, cohesive "Kill Chain" narrative, drastically reducing alert fatigue.
* **Dynamic SOAR Playbook Generation:** During a live, fast-moving incident, static playbooks often fail. LLMs can dynamically generate incident response steps. For example, upon detecting a novel ransomware outbreak, the AI can instantly draft the exact PowerShell scripts needed to isolate the affected subnets via the EDR API and draft a preliminary, legally compliant breach notification for stakeholders.

### Threat Modeling
Integrating security design principles early in the Software Development Life Cycle (SDLC) through architectural analysis.

* **Automated STRIDE/DREAD Analysis:** Security architects can feed plain-text system descriptions, `Terraform` Infrastructure-as-Code files, or even upload whiteboard images of network architectures to multimodal LLMs (like GPT-4o or Claude 3.5 Sonnet). The AI systematically applies threat modeling methodologies like STRIDE to generate comprehensive threat matrices, identify trust boundary violations (e.g., an unauthenticated Lambda function accessing a core database), and recommend specific security controls before a single line of application code is written.

### Fraud Detection
Leveraging predictive ML models to secure financial transactions, digital identities, and prevent synthetic identity theft in real-time.

* **Transaction Scoring & AML (Anti-Money Laundering):** Graph Neural Networks (GNNs) analyze complex webs of financial transactions. By mapping relationships between accounts, IPs, and geographic locations in a high-dimensional graph, the AI can identify circular money flows, mule account networks, and sophisticated AML evasion tactics in milliseconds, blocking fraudulent transactions before they settle.
* **Deepfake and Synthetic Media Detection:** As social engineering evolves into synthetic voice cloning (CEO fraud) and video manipulation, specialized ML models are deployed at the authentication edge. These models analyze biometric artifacts, microscopic audio frequencies, lighting inconsistencies, and pixel-level noise to detect AI-generated media during live video KYC (Know Your Customer) authentication flows.

### Translation & Localization
Overcoming language and abstraction barriers in global threat intelligence and low-level reverse engineering.

* **Decompilation Translation:** Seamlessly translating low-level hardware architectures (x86, ARM, MIPS Assembly) into high-level conceptual workflows. LLMs can take cryptic assembly blocks and explain them as Python or C-like structures, making malware analysis accessible to junior analysts without deep assembly language expertise.
* **Threat Intel Localization:** Advanced Persistent Threat (APT) reports and zero-day discussions frequently originate in the native languages of the targeted regions or the discovering researchers (e.g., Mandarin on specific forums, Russian on Dark Web boards, Farsi). AI provides instant, highly accurate translations that preserve critical, nuanced cybersecurity taxonomy and operational context, allowing global defense teams to ingest and act on foreign threat intelligence immediately.

### Summarization & Alert Triage
Distilling overwhelming, gigabyte-sized amounts of raw telemetry and threat data into concise, actionable intelligence.

* **Alert Fatigue Reduction (The "TL;DR" of InfoSec):** Security analysts face immense cognitive overload. LLMs can condense a highly technical 50-page CISA advisory, an intricate Mandiant threat report, or a massive, chaotic Twitter/X thread from security researchers into a structured, 3-bullet executive summary: "1. What is the threat?", "2. Is our specific tech stack affected?", and "3. What are the immediate mitigation and patching steps?".
* **Log Aggregation Synthesis:** Instead of forcing a human analyst to scroll through 10,000 lines of raw Windows Event Logs (Sysmon) or AWS CloudTrail JSON files to find the anomaly, the AI can ingest the entire dataset and output a human-readable timeline: *"At 10:00 UTC, User X attempted 50 failed logins via RDP. At 10:05 UTC, a successful login occurred from an anomalous IP. Immediately after, a suspicious child process (`powershell.exe -enc`) was spawned, indicating a likely brute-force compromise and subsequent payload execution."*
