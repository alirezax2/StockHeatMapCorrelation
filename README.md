# StockHeatMapCorrelation
A docker based web app to show correlation between stocks and sectors as a heat map





## How to install uv
To install `uv` (a fast Python package installer and resolver) in GitHub Codespaces, you can follow these steps:

### 1. Open Your Codespace
- Open your GitHub repository in Codespaces by clicking the "Code" button and selecting "Open with Codespaces."

### 2. Open the Terminal
- Once your Codespace is running, open the terminal within Codespaces.

### 3. Install `uv`
- Run the following command to install `uv`:

  ```bash
  curl -LsSf https://astral.sh/uv/install.sh | sh
  ```

  This script will download and install `uv` for you.

### 4. Add `uv` to Your PATH
- After installation, the script will prompt you to add `uv` to your PATH. If you missed it, you can manually add it by running:

  ```bash
  echo 'export PATH="$HOME/.cargo/bin:$PATH"' >> ~/.bashrc
  source ~/.bashrc
  ```

  This ensures that `uv` is available in your terminal session.

### 5. Verify Installation
- Verify that `uv` is installed correctly by running:

  ```bash
  uv --version
  ```

  This should display the version of `uv` that was installed.

### 6. Use `uv`
- You can now use `uv` to manage Python packages in your Codespace. For example, to create a virtual environment and install packages:

  ```bash
  uv venv myenv
  source myenv/bin/activate
  uv pip install requests
  ```

Add a requirements.in or pyproject.toml File
Create a requirements.in file (for pip-tools-style workflows) or a pyproject.toml file (for modern Python projects).

Example requirements.in:

  ```
requests
numpy
  ```
Example pyproject.toml (for a Poetry-like setup):
toml
  ```
[project]
name = "my_project"
version = "0.1.0"
dependencies = [
    "requests",
    "numpy",
]  
  ```

Install Dependencies
Use uv to install dependencies:

bash
  ```
uv pip install -r requirements.in
  ```
Or, if using pyproject.toml:

bash
  ```
uv pip install .
  ```
  
### Notes:
- If you encounter any issues, ensure that your Codespace has the necessary permissions and dependencies installed.
- `uv` is designed to be a drop-in replacement for `pip` and `pip-tools`, so you can use it in place of those tools for faster package management.

That's it! You've successfully installed `uv` in your GitHub Codespace.










