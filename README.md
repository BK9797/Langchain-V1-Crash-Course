# LangChain V1 Crash Course

## Set up the virtual environment

Open a terminal in `Langchain-V1-Crash-Course`. If your prompt already shows that folder, do not run `cd Langchain-V1-Crash-Course` again.

Use Python 3.11 for this course. The project requires Python 3.11 or newer.

On macOS, create and activate the environment:

```bash
python3.11 -m venv .venv
source .venv/bin/activate
```

If `.venv` already exists, only run the activation command. A prompt containing `(.venv)` means it is already active. Confirm the interpreter with `python -c "import sys; print(sys.executable)"`; it should point inside this project's `.venv`.

## Install the requirements

With the virtual environment active, run:

```bash
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
python -m pip install --upgrade "langchain>=1.1.0" ipykernel
```

## Select the notebook kernel

Register the environment as a Jupyter kernel:

```bash
python -m ipykernel install --user --name langchain-v1 --display-name "Python (LangChain V1)"
```

Open a course notebook in Jupyter or VS Code and select **Python (LangChain V1)** as its kernel. Restart the kernel after upgrading packages, then verify the environment in a notebook cell:

```python
import sys
import langchain
from langchain.agents import create_agent

print("Python:", sys.executable)
print("LangChain:", langchain.__version__)
```

The Python path should point to `.venv`, and LangChain should be version 1.1.0 or newer. If `create_agent` cannot be imported, check the selected kernel and restart it.

## Configure API keys

Create a local `.env` file in the project folder and add a key for the provider you use:

```dotenv
OPENAI_API_KEY=your_openai_api_key
GROQ_API_KEY=your_groq_api_key
GOOGLE_API_KEY=your_google_api_key
```

Only configure the providers you need. Load the file before creating a model:

```python
from dotenv import load_dotenv

load_dotenv()
```

Keep `.env` out of Git and never paste real API keys into notebooks or the README.

When finished, leave the virtual environment with:

```bash
deactivate
```
