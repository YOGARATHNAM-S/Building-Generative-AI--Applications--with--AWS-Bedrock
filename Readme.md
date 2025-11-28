# AWS Bedrock GenAI Workshop

## 📖 Project Overview

This repository contains a comprehensive, hands-on workshop designed to teach developers how to build production-grade Generative AI applications using **Amazon Bedrock**.

The project is structured as a progressive learning path. It provides a "Concept-to-Code" experience where students can experiment with Foundation Models (FMs), implement Retrieval-Augmented Generation (RAG), generate and manipulate images, and build autonomous agents.

---

## 🧭 Architecture Overview

The following diagram illustrates the high-level architecture of the workshop application, including the interaction between the frontend, AWS Bedrock, vector stores, and supporting services.


![AWS Bedrock GenAI Workshop Architecture](/assets/architecture.png)

---

## 🏗 Project Structure

The repository is organized to support both self-paced learning and instructor-led workshops:

  * **📂 `module/`**: The workspace for students. Contains skeleton code and "TODO" markers where you implement the logic to connect to AWS Bedrock.
  * **📂 `completed/`**: Fully functional reference implementations of all features. Use this to check your work or see the final solution.
  * **📂 `data/`**: specialized datasets, PDF documents for RAG, and sample CSV/JSON files used for labs.

---

## 🚀 Features & AWS Services Used

This project leverages the **AWS Bedrock API** via the `boto3` SDK. Below is a detailed breakdown of how each feature maps to specific AWS services and models.

### 1. 💬 Conversational Chatbot

  * **Functionality:** A streaming chat interface capable of maintaining context and handling natural language queries.
  * **AWS Service:** **Amazon Bedrock Runtime (InvokeModelWithResponseStream)**.
  * **Models Used:**
      * **Anthropic Claude 3 (Sonnet/Haiku)** or **Amazon Titan Text**: Selected for their high reasoning capabilities and context window handling.

### 2. 📚 RAG (Retrieval-Augmented Generation)

  * **Functionality:** Allows the AI to answer questions based on specific external documents (PDFs/Text) rather than just its training data.
  * **AWS Service:** **Amazon Bedrock Embeddings** & **Vector Stores**.
  * **Architecture:**
      * **Embeddings Model:** **Amazon Titan Embeddings G1 - Text** converts text into vector representations.
      * **Vector Database:** Uses **FAISS** or **ChromaDB** (local vector stores) to index and search document chunks.
      * **Orchestration:** Retrieves relevant chunks based on semantic similarity and feeds them into the LLM context window.

### 3. 🎨 Image Generation & Manipulation

  * **Functionality:** A suite of tools to generate new images or surgically alter existing ones (inpainting, outpainting, background removal).
  * **AWS Service:** **Amazon Bedrock Image Generation APIs**.
  * **Models Used:**
      * **Stable Diffusion XL (SDXL)** or **Amazon Titan Image Generator G1**.
  * **Key Capabilities Implemented:**
      * **Text-to-Image:** Generating visual assets from descriptive prompts.
      * **Inpainting (Masking):** Using image masks to replace specific objects (e.g., "changing curtains") while keeping the rest of the image intact.
      * **Outpainting:** Extending an image beyond its original borders.
      * **Variation:** Creating stylistic variations of an input image using image-to-image techniques.

### 4. 🛡️ Guardrails & Safety

  * **Functionality:** Enforces safety policies to prevent the AI from generating harmful content, PII (Personally Identifiable Information), or discussing restricted topics.
  * **AWS Service:** **Amazon Bedrock Guardrails**.
  * **Implementation:**
      * **Content Filters:** Blocks hate speech, insults, and violence.
      * **PII Redaction:** Automatically detects and masks sensitive data like emails or SSNs.
      * **Denied Topics:** Custom rules configured to refuse answering questions about specific off-limits competitors or topics.

### 5. 🤖 Agents & Tool Use

  * **Functionality:** Autonomous agents that can break down complex user requests and "call" external tools or APIs to complete tasks.
  * **AWS Service:** **Amazon Bedrock Agents**.
  * **Implementation:**
      * Uses LLM reasoning to determine when to execute a Python function (e.g., "GetWeather", "QueryDatabase").
      * Parses structured data (JSON) from the model to execute backend logic.

### 6. 📊 Structured Data Extraction (CSV/JSON)

  * **Functionality:** Extracting specific fields from unstructured text and formatting them into usable JSON or CSV output.
  * **Technique:** Prompt Engineering coupled with **Anthropic Claude's** strong instruction-following capabilities to enforce output schemas.

---

## 🛠 Technology Stack

  * **Frontend:** [Streamlit](https://streamlit.io/) - For building the interactive web UI.
  * **SDK:** [AWS Boto3](https://aws.amazon.com/sdk-for-python/) - To interact with Amazon Bedrock services.
  * **Language:** Python 3.10+
  * **Vector DB:** FAISS / ChromaDB - For local vector storage and semantic search.
  * **Data Handling:** Pandas (for CSV), PyPDF2 (for document parsing).

---

## ⚙️ Prerequisites

Before running the labs, ensure you have the following:

1. **AWS Account** with active subscription.
2. **Bedrock Model Access**: Go to the AWS Console → Bedrock → Model Access and enable:
      * Anthropic Claude 3
      * Amazon Titan Text & Embeddings
      * Stable Diffusion XL
3. **AWS Credentials**: Configured locally via AWS CLI (`aws configure`) or environment variables.

---

## 📦 Installation & Setup

1. **Clone the repository:**

    ```bash
    git clone https://github.com/your-repo/Building-Generative-AI-Applications-with-AWS-Bedrock.git
    cd modules
    ```

2. **Create a Virtual Environment:**

    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows: venv\Scripts\activate
    ```

3. **Install Dependencies:**

    ```bash
    pip install -r requirements.txt
    ```

4. **Run the Application:**

   Navigate to the `completed` folder to see the final app, or `labs` to start building.

    ```bash
    streamlit run Home.py
    ```

---

## 📸 Sample Output

Below is an example of the workshop UI and model output in action (for example: chatbot, RAG response, or image generation result).

---
![Sample Application Output](/assets/app-in-use.png)
---

---
![Sample Application Output](assets/app-in-use2.png)
---

---
![Sample Application Output](/assets/app-in-use1.png)
---

---
![Sample Application Output](/assets/app-in-use3.png)
---

---
![Sample Application Output](/assets/app-in-use4.png)
---
