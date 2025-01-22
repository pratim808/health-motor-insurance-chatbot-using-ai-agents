# health-motor-insurance-chatbot-using-ai-agents
Okay, that's a good point. Here's the updated README file that reflects the .ipynb file structure:

# Insurance Chatbot using AI Agents

## Overview

This project implements a customer service chatbot designed to provide information about health and motor insurance policies. It leverages multiple AI agents, integrated with data from TATA AIG's health and motor insurance websites, to answer user inquiries and provide policy details.

## Description

The chatbot is built using Langchain and utilizes the following components:

*   **Web Scrapers:** WebBaseLoader to fetch content from TATA AIG's website regarding health and motor insurance policies.
*   **Text Splitters:** RecursiveCharacterTextSplitter to break down the scraped text into manageable chunks.
*   **Embeddings:** HuggingFaceEmbeddings to create vector representations of the text chunks using `sentence-transformers/all-MiniLM-L6-v2`.
*   **Vector Store:** FAISS (Facebook AI Similarity Search) to store the vectorized text for efficient retrieval.
*   **Retrieval Tools:** create_retriever_tool to make the vector stores searchable by the chatbot.
*   **Large Language Model (LLM):** ChatGroq with model_name `Llama3-8b-8192` is used to generate human readable text from queries and tool interactions.
*   **Agent:** ReAct agent to handle conversations and tool usage.
*   **Memory:** ConversationBufferMemory to maintain the context of the conversation.

The chatbot is designed to answer questions about:

*   **Health Insurance:** Waiting periods, coverage details, etc.
*   **Motor Insurance:** Types of policies, claim processes, coverage details etc..

## Project Structure

The main file for this project is a Jupyter Notebook: `Insurance_Chatbot.ipynb`.

The notebook contains the following logic, organized into cells:
1.  **Installation:** Installs required libraries.
2.  **Data Loading and Processing:**
    *   Loads the health and motor insurance pages using WebBaseLoader.
    *   Splits the text into chunks using RecursiveCharacterTextSplitter.
    *   Generates embeddings with HuggingFaceEmbeddings and stores them in FAISS vector stores.
    *   Creates retriever tools for the vector stores.
3.  **LLM Setup:**
     *   Initializes the ChatGroq LLM using API key (This should be kept secret in a different location or environment variable if in production).
4.  **Tools Creation:**
    *  Combines the health and motor insurance retriever tools.
5.  **Agent Initialization:**
    *   Loads the ReAct prompt.
    *   Initializes an agent with the tools, prompt, and LLM using the AgentExecutor to chain together the various components of the agent.
    *   Adds the conversation buffer memory to keep track of the conversation context.
6.  **Example Interactions:**
    *   Demonstrates the agent working with a few example prompts.

## Getting Started

### Prerequisites

*   Python 3.10 or higher
*   Jupyter Notebook environment (e.g., Jupyter Lab, Google Colab)
*   API Key for the Groq LLM model
*   Required libraries installed (see Installation section)

### Installation

1.  Download the `insurance_ai_agents.ipynb` file.
2.  Open the Jupyter Notebook using your preferred environment.
3.  Run the first cell to install the required Python libraries:

    ```python
    !pip install -U langsmith langchain langchain-community  sentence-transformers langchain_huggingface faiss-gpu langchain_groq
    ```

4.  Set up your Groq API Key as a variable named `groq_api_key`. Replace `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` with your own API Key.

5. Run all cells of the notebook sequentially.

## Usage

After completing the above steps, run all cells in the `Insurance_Chatbot.ipynb` notebook.

The script will run example prompts. You can further interact with the chatbot by adding new cells at the end of the notebook and executing them with the following command, 
```python
print(agent_executor.invoke({"input": "YOUR PROMPT HERE"})["output"])
content_copy
download
Use code with caution.
Markdown
Future Enhancements

Implement more robust error handling.

Improve the chatbot's ability to understand complex queries.

Add support for user authentication and policy-specific data.

Deploy the chatbot as a web application for wider access.

Use a dedicated vector database instead of the in-memory FAISS store for production usage.

Support for multiple languages.

Credits

This project utilizes the Langchain framework and the Groq API.

Data is sourced from TATA AIG's website.

Hugging Face transformers is used for embedding.

Disclaimer

This chatbot provides information based on the content scraped from the provided TATA AIG webpages. It is not an official customer support channel and should not be used for claims processing.

**Changes made:**

*   **Project Structure:** Corrected the description to reference the `.ipynb` file instead of a `.py` file.
*   **Installation Instructions:** Modified the installation instructions to reflect running commands directly in the notebook (using `!pip`) and to open the notebook in a jupyter environment.
*   **Usage Instructions:** Updated the "Usage" section to mention running cells in the Jupyter Notebook sequentially.
*   **Removed the python execution command** since now its expected to be done in jupyter notebook environment.

This README is now tailored to your `.ipynb` notebook environment and provides accurate instructions.
content_copy
download
Use code with caution.
