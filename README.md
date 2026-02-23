# AI Agentic RAG

An advanced Agentic Retrieval-Augmented Generation (RAG) system where an AI agent autonomously decides when and how to retrieve information, which retrieval strategy to use, and iteratively refines answers through multi-step reasoning and tool calls.

## Description

Standard RAG retrieves documents once and generates an answer. Agentic RAG goes further — the agent autonomously plans its retrieval strategy, decides when more information is needed, executes multiple retrieval steps, evaluates retrieved content quality, and iterates until it has sufficient context for a high-quality answer. This repository demonstrates a full agentic RAG pipeline.

## Features

- **Autonomous Retrieval Planning** — Agent decides whether to retrieve, what to retrieve, and when to stop
- - **Multi-Step Retrieval** — Iterative retrieval with dynamic query reformulation based on initial results
  - - **Retrieval Strategy Selection** — Agent chooses between semantic search, keyword search, or hybrid
    - - **Document Grading** — Automatically evaluate retrieved document relevance before using in generation
      - - **Query Decomposition** — Break complex questions into sub-queries for more targeted retrieval
        - - **Self-Reflection** — Agent evaluates its own answer and retrieves more if the answer is insufficient
          - - **Re-ranking** — Re-rank retrieved documents by relevance using cross-encoder models
            - - **LangGraph Workflow** — Implement the agentic loop as a stateful LangGraph graph
             
              - ## Agentic RAG Workflow
             
              - ```
                User Question
                      ↓
                [Query Decomposition]
                  - Break into sub-questions
                      ↓
                [Retrieval Agent Loop]
                  1. Retrieve relevant chunks
                  2. Grade document relevance
                  3. If relevant → Add to context
                  4. If not → Reformulate query → Retry
                      ↓
                [Answer Generation]
                      ↓
                [Self-Evaluation]
                  - Is answer grounded in context?
                  - Is answer complete?
                  - If NO → More retrieval
                      ↓
                Final Answer
                ```

                ## Tech Stack

                | Component | Technology |
                |---|---|
                | Language | Python 3 |
                | Agent Framework | LangGraph / LangChain |
                | LLM | OpenAI GPT-4 / Anthropic Claude |
                | Vector Store | FAISS / Chroma |
                | Re-ranking | Cohere Rerank |
                | Notebook | Jupyter (Google Colab) |

                ## Setup Instructions

                ### Prerequisites

                - Python 3.8+
                - - OpenAI API key
                 
                  - ### Installation
                 
                  - ```bash
                    git clone https://github.com/sanikacentric/AI_Agentic_RAG.git
                    cd AI_Agentic_RAG
                    pip install langchain langgraph openai faiss-cpu chromadb cohere jupyter
                    ```

                    ### Configuration

                    ```bash
                    export OPENAI_API_KEY=your-openai-api-key
                    export COHERE_API_KEY=your-cohere-api-key  # for reranking
                    ```

                    ### Running the Notebook

                    ```bash
                    jupyter notebook
                    ```

                    ## License

                    Open source — for educational and AI research purposes.
