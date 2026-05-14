# How I think with Agentic Workflow 

## First: Describe the problem in your own sentence

### 1. What are the boundaries of the problem?
* **Scope:** Define what is included and, importantly, what is excluded from the task.
* **Constraints:** Identify technical limits, timeframes, and resource availability.
* **Expected Output:** Clearly visualize what the final successful result looks like.

---

### 2. How can the problem be broken down into repeatable execution?
* Deconstruct complex goals into **atomic, manageable tasks**.
* Standardize workflows so they can be automated or replicated without loss of quality.
* Focus on creating a "pipeline" rather than a one-off solution.

---

### 3. How do we document errors and solutions at each step?
* Maintain a **live error log** that captures specific tracebacks and their corresponding fixes.
* Document the **"bug"**, **"investigation**" and **"proposed solution"** behind logic pivots to prevent repeating past mistakes.
* Ensure the documentation is accessible enough for "Future Me" or a teammate to follow.

---

### 4. Continuously ask: Why are we doing it this way, and how do others do it?
* **Internal Critique:** Is this the most efficient path, or just the most familiar one?
* **External Benchmarking:** Research how industry leaders or peers solve similar problems.
* **Adaptation:** Stay open to integrating better methodologies discovered during the process.

## Architecture
UMPIRE
Understand
Match
Plan 
Implement
Review/Evaluate

## CS146S Inventory 
📍Lossy compression of the internet — 課程比喻：LLM 是網路的有損壓縮檔，記得「什麼常接什麼」而非「什麼是真的」。
📍Swiss Cheese Model of Capability — 課程術語：LLM 能力有不可預測的洞，能解奧林匹亞但會錯 9.9 vs 9.1。用這個 mental model 而非 IQ 模型看待 LLM。
📍Context Poisoning — 早期錯誤寫進對話歷史，agent 一直抓著不放。
📍Defensive Prompting — 把 LLM 當 stochastic 工具的設計紀律：講清楚 how 而非 what、預先列依賴、加 checkpoint、用 typed language。
📍Prompt is the new source code — Shawn Gross 論點：傳統留 source 丟 binary，AI dev 卻是丟 prompt 留 generated code = 留 binary 丟 source。
📍Tool consolidation — 工具數量越少越好，避免 Context Confusion。
📍Verbosity control — 讓 agent 自己決定要 full output 還是摘要，管自己的 token 預算。
📍YOLO mode exploit / CVE-2025-3773 — Agent 改自己的 config file 把防護關掉，靠 prompt injection 觸發。
📍Code Review Hierarchy — 由下而上：Mental alignment（共識）> Correctness > Design > Bug > Style。Bug finding 不是主要目的。
📍Mental alignment — Code review 真正的功能是讓團隊對系統的共同理解保持同步。
📍Trench warfare model — Dev 要 velocity、Ops 要 stability，互相不信任的傳統文化。
📍From syntax to specification — 程式設計的瓶頸從打字變成寫清楚規格。
📍Execution skills vs Judgment skills — AI 吃下執行類技能（implement、test、boilerplate）；人剩下判斷類（拆問題、架構決策、業務脈絡）





## This is how VibeCoding should be done! 程序员老王

Language- prefer python, rust, javascript (python most preferable , rust most reliable, )
0:02:55 Requirements-step1: Must defined requirement(as attached picture)
00:04:57 Design- step2 : conceptual / module design,and detail implementation (as attached pic)
00:06:59 Task-step3 (as picture )
00:08:37 Prompt
00:11:12 Vibe


### Building Prototype with Python

**1. Requirements Gathering (The "No Guessing" Rule)**
Instead of just telling the AI to "build an FC emulator," he forces the AI to act as a systems analyst. He provides the initial environment (a uv Python project) and the end goal (run Super Mario), but explicitly commands the AI: "I don't know anything about this. Ask me questions. Do not guess my intent." This prevents the AI from hallucinating a bad architecture right out of the gate and results in a solid proposal.md.
![image](https://hackmd.io/_uploads/SJsEtBQJGx.png)

**2. High-Level Design**
He feeds that proposal back into the AI to establish the architecture, defining the modules and how they interact to generate high-level-design.md. He strictly maintains the rule that the AI must ask questions rather than make assumptions.

![image](https://hackmd.io/_uploads/rJoHKHXJGg.png)


**3. Task Breakdown (Context Management)**
This step is crucial for managing an LLM's context window. He breaks the design down into the smallest possible executable tasks. Every module gets its own markdown file with checklists, and everything rolls up into a master progress.md file.
![image](https://hackmd.io/_uploads/SyIUFrm1Gg.png)

**4. Implementation (Supervisor & Worker Agents)**
This is where the actual "vibing" happens, but in a controlled environment. He uses a Supervisor Agent (监工Agent) that reads the progress.md file and delegates specific coding tasks to Sub-Agents. Each Sub-Agent is only given the context of the specific module it is working on, keeping the AI focused and reducing errors.

![image](https://hackmd.io/_uploads/ByXDYBmyfe.png)
