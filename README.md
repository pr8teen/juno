# Juno - Your Personal RAG Chatbot

<img width="1440" height="706" alt="image" src="https://github.com/user-attachments/assets/ea3c41a3-4fbc-4bf4-ad50-04a94fd4dca6" />
<img width="1435" height="705" alt="image" src="https://github.com/user-attachments/assets/fa2d80c3-07b3-4973-aeba-eeefdd5ba32a" />

**[Watch the Video Demo on YouTube](https://www.youtube.com/watch?v=wG-rn6ty3Wk)**

Juno is a private, locally-run AI research assistant that lets you have conversations with your own documents. I built this project to solve a problem I faced while drowning in user research documents for a project—it was impossible to find and synthesize information efficiently.

Unlike general chatbots like ChatGPT, Juno is:
* **Private:** Your documents and conversations never leave your local machine (though the LLM queries are sent to Groq).
* **Multi-Document:** It can cross-reference your *entire* library of uploaded files at once.
* **Persistent:** Your indexed documents are saved, so you can close the app and continue your session later.

---

## ✨ Features

-   **Multi-Document Q&A:** Ask questions across your entire library of uploaded files.
-   **Privacy-Focused:** Your documents are indexed and stored locally.
-   **Multiple AI Models:** Choose between different powerful models like Llama 3.1 and Mixtral.
-   **Persistent Storage:** Uses **ChromaDB** for persistent vector storage and **SQLite** for file/chat history.
-   **Supported Formats:** Upload `.pdf`, `.docx`, `.html`, `.txt`, and `.csv` files.
-   **Modern UI:** A clean, animated interface built with **FastAPI**, **Tailwind CSS**, and **JavaScript**.

---

## 🛠️ Tech Stack

-   **Backend:** Python 3.10+, FastAPI, Uvicorn
-   **Frontend:** HTML, Tailwind CSS, JavaScript
-   **RAG Pipeline:** LangChain
-   **Vector Store:** ChromaDB (for local, persistent vector storage)
-   **LLMs:** Groq (for Llama 3.1 8B & Mixtral 8x7B)
-   **Embeddings:** Hugging Face (Sentence Transformers)
-   **Database:** SQLite (for tracking files and chat history)

---

## 🚀 Getting Started: How to Run Juno Locally

Follow these instructions to get a copy of Juno running on your local machine.

### Step 1: Get Your API Keys (Required)

Juno needs two free API keys to function.

1.  **Groq API Key:** Go to [Groq Console](https://console.groq.com/keys) to get your free API key for fast LLM inference.
2.  **Hugging Face API Token:** Go to [Hugging Face Settings](https://huggingface.co/settings/tokens) to get your API token. This is used for the embedding model.

### Step 2: Installation and Setup

Choose the guide for your operating system.

---

#### 🖥️ On Windows (using PowerShell)

1.  **Open PowerShell** (or Command Prompt).
2.  **Clone the repository:**
    ```powershell
    git clone [https://github.com/pr8teen/juno.git](https://github.com/pr8teen/juno.git)
    cd juno
    ```
3.  **Create a virtual environment:**
    ```powershell
    python -m venv venv
    ```
4.  **Activate the virtual environment:**
    ```powershell
    .\venv\Scripts\Activate.ps1
    ```
    *(If you get an execution policy error, run `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope Process` and try again. For `cmd`, you'd run `.\venv\Scripts\activate.bat`)*

    Your terminal line should now start with `(venv)`.

5.  **Install the required packages:**
    ```powershell
    pip install -r requirements.txt
    ```
6.  **Create the environment file:**
    * In the same folder, create a new file named `.env`
    * Open it with Notepad and paste the following, replacing the placeholders with your keys from Step 1:
    ```ini
    GROQ_API_KEY=your_groq_api_key_here
    HUGGINGFACEHUB_API_TOKEN=your_huggingface_api_token_here
    ```
    * Save and close the file.

---

#### 🍎 On macOS (using Terminal)

1.  **Open Terminal**.
2.  **Clone the repository:**
    ```bash
    git clone [https://github.com/pr8teen/juno.git](https://github.com/pr8teen/juno.git)
    cd juno
    ```
3.  **Create a virtual environment:**
    ```bash
    python3 -m venv venv
    ```
4.  **Activate the virtual environment:**
    ```bash
    source venv/bin/activate
    ```
    Your terminal line should now start with `(venv)`.

5.  **Install the required packages:**
    ```bash
    pip3 install -r requirements.txt
    ```
6.  **Create the environment file:**
    * You can do this directly from the terminal:
    ```bash
    nano .env
    ```
    * Paste the following lines, replacing the placeholders with your keys from Step 1:
    ```ini
    GROQ_API_KEY=your_groq_api_key_here
    HUGGINGFACEHUB_API_TOKEN=your_huggingface_api_token_here
    ```
    * Press `Ctrl+X`, then `Y`, then `Enter` to save and exit.

---

#### 🐧 On Ubuntu/Linux (using Terminal)

1.  **Open your Terminal**.
2.  **Ensure you have `python3-venv`:**
    ```bash
    sudo apt-get update
    sudo apt-get install -y python3-venv
    ```
3.  **Clone the repository:**
    ```bash
    git clone [https://github.com/pr8teen/juno.git](https://github.com/pr8teen/juno.git)
    cd juno
    ```
4.  **Create a virtual environment:**
    ```bash
    python3 -m venv venv
    ```
5.  **Activate the virtual environment:**
    ```bash
    source venv/bin/activate
    ```
    Your terminal line should now start with `(venv)`.

6.  **Install the required packages:**
    ```bash
    pip3 install -r requirements.txt
    ```
7.  **Create the environment file:**
    * You can do this directly from the terminal:
    ```bash
    nano .env
    ```
    * Paste the following lines, replacing the placeholders with your keys from Step 1:
    ```ini
    GROQ_API_KEY=your_groq_api_key_here
    HUGGINGFACEHUB_API_TOKEN=your_huggingface_api_token_here
    ```
    * Press `Ctrl+X`, then `Y`, then `Enter` to save and exit.

---

### Step 3: Run the Application

Now that everything is installed and configured:

1.  Make sure your virtual environment is **still active** (you see `(venv)` in your terminal).
2.  Run the Uvicorn server:
    ```bash
    uvicorn main:app --reload
    ```
    * `--reload` makes the server auto-restart when you save changes to the code.
3.  You will see a confirmation in your terminal, similar to:
    `Uvicorn running on http://127.0.0.1:8000 (Press CTRL+C to quit)`

### Step 4: Open and Use Juno

Open your favorite web browser and go to:

**http://127.0.0.1:8000**

You should see the Juno landing page.

#### User Flow
1.  Click "Get Started For Free" to go to the chat app (`/app`).
2.  On the left, click "Upload Document" and select your files. You will see them appear in the "Uploaded Documents" list.
3.  Wait for the file to be indexed (this is very fast).
4.  Ask your questions in the chatbox!
5.  To delete a document and its knowledge from the app, click the trash can icon next to its name.

---

## 📂 Project Structure

```bash
juno/
├── db/                      # SQLite DBs and ChromaDB vectorstore are created here
├── static/
│   ├── img/                 # Your photo, screenshot, etc.
│   ├── js/                  # Main JavaScript file (script.js)
│   ├── index.html           # The chat application page (/app)
│   └── landing.html         # The main landing page (/)
├── .env                     # Stores your secret API keys (IMPORTANT!)
├── .gitignore               # Tells Git what to ignore (like venv, db/)
├── main.py                  # Main FastAPI application, API routes
├── chroma_utils.py          # Functions for ChromaDB (indexing, deleting)
├── db_utils.py              # Functions for SQLite (logging, file tracking)
├── langchain_utils.py       # Core RAG pipeline logic
├── pydantic_models.py       # Data models for FastAPI
├── requirements.txt         # List of Python packages
└── README.md                # You are here!
```
## 📄 License

This project is licensed under the MIT License.

---

Created by Prasannajeet Ojha.
