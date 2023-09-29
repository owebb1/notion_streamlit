# Notion Content Ingestion and Chatbot Interface

This repository consists of two main components: the ingestion script (`ingest.py`) which processes and vectorizes Notion documents, and a Streamlit application (`app.py`) that provides a chat interface for interacting with the ingested content.

## Features

- **Notion Document Ingestion**:

  - Load Notion documents from a specified directory.
  - Split the documents into manageable chunks.
  - Vectorize the chunks using OpenAI's models.
  - Index the vectors using FAISS for efficient nearest-neighbor lookups.

- **Streamlit Chat Interface**:
  - Customizable page configuration.
  - Session-based chat history to maintain conversation across app reruns.
  - Simulated typing effect for a more interactive user experience.
  - Custom avatars for the assistant and user in the chat interface.

## Dependencies

- streamlit
- openai
- langchain
- faiss-cpu
- tiktoken

## Installation

1. Clone this repository:

```bash
git clone <repository_url>
cd <repository_name>
```

2. Create a virtual environment and activate it:

```bash
python -m venv <envname>
source <envname>/bin/activate
```

3. Install the necessary packages using the following command:

```bash
pip install -r requirements.txt
```

4. Obtain an API key from OpenAI and set it in Streamlit's secrets management system. Follow Streamlit's [documentation](https://docs.streamlit.io/library/api-reference/secrets) on how to manage secrets in your app.

Now, with your virtual environment activated, you can run the `ingest.py` script to process and index your Notion documents, and then launch the Streamlit app to interact with the chatbot interface.

## Usage

### Notion Document Ingestion

1. Place your Notion documents in a folder named `notion_content`.
2. Run the `ingest.py` script to process and index the documents:

```bash
python ingest.py
```

This will create a local FAISS index which will be used by the chatbot to lookup relevant content based on user queries.

### Streamlit Chat Interface

1. Run the Streamlit application:

```bash
streamlit run app.py
```

2. Navigate to the URL provided in the terminal output.
3. Start interacting with the chatbot in the provided interface. Your conversation will be persisted in the session, allowing for a continuous chat experience.

## Configuration

- **Ingestion**:

  - Adjust the `NotionDirectoryLoader` path if your Notion documents are located in a different directory.
  - Modify the `RecursiveCharacterTextSplitter` parameters to change how documents are split into chunks.
  - Change the FAISS index save location by modifying the `save_local` argument.

- **Streamlit Interface**:
  - Customize the `company_logo` URL and `page_title` in `st.set_page_config` to reflect your brand.
  - The `load_chain` function is expected to return a pre-trained language model. Ensure `utils.py` and `load_chain` are properly configured to load your desired model.

## Files

- `ingest.py`: Script for processing and indexing Notion documents.
- `app.py`: The Streamlit application file containing the chatbot logic.
- `utils.py`: Utility file where `load_chain` and any other necessary functions are defined.
- `requirements.txt`: List of required Python packages.

## License

This project is open-source and available under the [MIT License](LICENSE).

Contributions to this project are welcome via issues and pull requests.
