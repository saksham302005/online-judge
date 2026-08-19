# 🚀 Online Judge System (Sandboxed RCE Engine)

A high-performance, secure, and scalable **Online Judge Backend** built with **Django REST Framework** and **Docker**. Designed to execute untrusted user code (C++, Python, etc.) in isolated container environments with automated testcase evaluation and resource control (Time & Memory limits).

---

## ✨ Key Technical Features

* **🔒 Sandboxed Remote Code Execution (RCE):** Isolated code execution using ephemeral Docker containers to prevent unauthorized system access or host contamination.
* **⚡ Robust API Integration:** Exposes `CodeSubmitRobustAPI` for processing multi-language submissions asynchronously.
* **🧪 Automated Testcase Evaluation:** Automated file input/output processing with verdict generation (`AC` - Accepted, `WA` - Wrong Answer, `TLE` - Time Limit Exceeded).
* **🛠️ Clean Architectural Patterns:** Built using OOP principles including the **Singleton Pattern** (`CodeExecutionEngine`) for thread-safe execution engine management.
* **🧹 Dynamic Workspace & Auto-Cleanup:** Generates isolated dynamic directories per submission using `UUID` and automatically purges temporary code and binary files post-execution.

---

## 🏗️ System Architecture & Execution Flow

```text
[ Client / Web Interface ]
           │
           ▼ (POST Request)
[ Django REST API View ]  ──►  (CodeSubmitRobustAPI)
           │
           ▼
[ Code Execution Engine ] ──►  (Singleton Manager)
           │
           ▼
[ File Data Processor ]   ──►  (Creates code.cpp, input.txt, testcases.txt)
           │
           ▼
[ Docker Container ]      ──►  (Isolated Execution: algocode/revamped-cpp)
           │
           ▼
[ Testcase Comparator ]   ──►  (Generates Verdict: AC / WA / TLE / Error)
           │
           ▼
[ API Response ]          ──►  (JSON returned to client)
