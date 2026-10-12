# Enterprise RAG Reliability Lab

A small learning experiment using a fictional company policy and a local phi3:mini model through Ollama.

## What it explores
- Answering questions from policy text.
- Abstaining when the answer is absent.
- Retrieving passages with simple word matching.
- Skipping model generation when retrieval returns no matches.

## Limitations
This pilot contains four test questions. Word overlap does not prove answer support. These examples do not establish production reliability or general model performance.

## Run the lab on Windows

Prerequisites: Python 3.13, Git, and Ollama with `phi3:mini` available.

With Ollama running, open Command Prompt in the project folder:

```bat
python -m venv .venv
.venv\Scripts\activate
python -m pip install -r requirements.txt
python -m jupyterlab
```

Open `01_rag_abstention.ipynb` and run the cells from top to bottom.
The notebook writes local result files. Model responses may vary.

## Observed retrieval failure

For “Who must authorize telecommuting?”, word matching retrieved
unrelated passages and missed the manager-approval rule.

The model abstained with that retrieved context. When the correct
passage was supplied manually, it answered “The employee's manager.”

This single test illustrates how retrieval failure can cause an
answerable question to go unanswered.