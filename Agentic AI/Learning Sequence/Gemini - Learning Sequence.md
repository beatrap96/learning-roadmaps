# Agentic AI — Practical Learning Sequence (Beginner → Intermediate → Advanced)

This sequence builds skills progressively from core concepts to production-ready systems, optimized for a beginner with limited time and budget.

---

### **Beginner** phase (4–8 weeks)
*Focus: Grasping the fundamentals by building a knowledge-based system.*

1.  **What**: Master core Python, Git, and fundamental data structures.
    **Why**: This is the non-negotiable foundation for writing any robust software, including AI agents.
2.  **What**: Learn to use LLM APIs (like OpenAI's) and practice prompt engineering.
    **Why**: To understand how to control the "brain" of the agent directly and cost-effectively.
3.  **What**: Build a basic Retrieval-Augmented Generation (RAG) application.
    **Why**: This is the most common and powerful pattern for making LLMs useful with custom data. It teaches you about embeddings and semantic search.

**Phase Deliverable**: A command-line Q&A tool that uses RAG to answer questions about a specific book or a set of personal documents.

---

### **Intermediate** phase (8–12 weeks)
*Focus: Moving from static knowledge to dynamic action and deployment.*

1.  **What**: Learn an agent orchestration framework (e.g., LangChain or LlamaIndex) to give your agent tools.
    **Why**: To enable your agent to interact with the outside world (e.g., search the web, run code, use APIs) and perform complex tasks.
2.  **What**: Set up a local vector database (e.g., ChromaDB) and pipeline for data ingestion.
    **Why**: To manage larger amounts of knowledge efficiently and build a scalable foundation for your RAG system.
3.  **What**: Build and containerize a simple web API (using FastAPI/Flask and Docker) for your agent.
    **Why**: To make your agent accessible to other applications and learn the first step of productionization.
4.  **What**: Experiment with parameter-efficient fine-tuning (PEFT) on a small, local model.
    **Why**: To understand how to specialize a model's behavior or style without the high cost of full fine-tuning.

**Phase Deliverable**: A containerized web API for a "research assistant" agent that can be given a topic to search online and summarize.

---

### **Advanced** phase (12+ weeks)
*Focus: Building reliable, efficient, and production-ready agentic systems.*

1.  **What**: Implement a robust evaluation framework (e.g., using Ragas) and a monitoring solution (e.g., Langfuse).
    **Why**: To prove your agent works, measure improvements, and understand its behavior in production. "If you can't measure it, you can't improve it."
2.  **What**: Deep dive into cost/latency optimization by comparing models and caching strategies.
    **Why**: To ensure your agent is economically viable and provides a good user experience at scale.
3.  **What**: Implement security guardrails to defend against prompt injection and other LLM-specific vulnerabilities.
    **Why**: To build safe, trustworthy agents that can handle untrusted user input.
4.  **What**: Deploy your agent as part of a full-stack application with a simple UI (e.g., using Streamlit).
    **Why**: To create a complete, user-facing product and demonstrate end-to-end development skills.

**Phase Deliverable**: A deployed, monitored, and secure web application showcasing a specialized agent, accompanied by a technical blog post explaining the architecture.

---

### **90-Day Example Plan**
-   **Days 1–20**: Foundations. Focus on Python, Git, and making your first LLM API calls. Build simple prompt chains.
-   **Days 21–45**: Core Agent Skills. Build your first RAG application. Learn an agent framework like LangChain and give your agent its first tool (e.g., a calculator).
-   **Days 46–70**: Productionization. Wrap your agent in a FastAPI service, containerize it with Docker, and deploy the API to a cloud service free tier.
-   **Days 71–90**: Polish & Refine. Integrate evaluation and monitoring (Langfuse). Build a simple Streamlit UI for your API and write a blog post about your project.

### **Deliverables to show employers**
-   A GitHub profile with 2-3 well-documented agentic AI projects.
-   A live, deployed web application demonstrating a functional AI agent.
-   A technical blog post detailing the architecture, challenges, and evaluation of your most complex agent.
-   An active Hugging Face profile with a fine-tuned model adapter (LoRA) you have trained.

---

**Why this sequence works:** It prioritizes hands-on building of practical applications (RAG → Tool-Use → Deployed Product), ensuring you develop job-ready skills before getting lost in complex theory.