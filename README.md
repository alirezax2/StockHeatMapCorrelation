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




























Using `uv` in a fresh GitHub repository can streamline your Python development workflow significantly. Below, I'll guide you through the best practices for setting up `uv` in a new repository, explain what `uv project add` does, and show you how to manage Python versions effectively.

---

### **Best Way to Use `uv` in a Fresh GitHub Repo**

#### 1. **Initialize Your Repository**
   - Create a new GitHub repository and clone it locally or open it in GitHub Codespaces.

#### 2. **Install `uv`**
   - Install `uv` using the installation script:
     ```bash
     curl -LsSf https://astral.sh/uv/install.sh | sh
     ```
   - Add `uv` to your PATH if it isn't already:
     ```bash
     echo 'export PATH="$HOME/.cargo/bin:$PATH"' >> ~/.bashrc
     source ~/.bashrc
     ```

#### 3. **Set Up a Virtual Environment**
   - Use `uv` to create a virtual environment:
     ```bash
     uv venv .venv
     ```
   - Activate the virtual environment:
     ```bash
     source .venv/bin/activate
     ```

#### 4. **Add a `requirements.in` or `pyproject.toml` File**
   - Create a `requirements.in` file (for `pip-tools`-style workflows) or a `pyproject.toml` file (for modern Python projects).
   - Example `requirements.in`:
     ```
     requests
     numpy
     ```
   - Example `pyproject.toml` (for a Poetry-like setup):
     ```toml
     [project]
     name = "my_project"
     version = "0.1.0"
     dependencies = [
         "requests",
         "numpy",
     ]
     ```

#### 5. **Install Dependencies**
   - Use `uv` to install dependencies:
     ```bash
     uv pip install -r requirements.in
     ```
     Or, if using `pyproject.toml`:
     ```bash
     uv pip install .
     ```

#### 6. **Generate a Lock File (Optional)**
   - Use `uv pip compile` to generate a lock file for reproducible builds:
     ```bash
     uv pip compile requirements.in -o requirements.txt
     ```
   - This creates a `requirements.txt` file with pinned versions of all dependencies.

#### 7. **Add a `.gitignore` File**
   - Add a `.gitignore` file to exclude the virtual environment and other unnecessary files:
     ```gitignore
     .venv/
     __pycache__/
     *.pyc
     ```

#### 8. **Commit and Push**
   - Commit your changes and push them to GitHub:
     ```bash
     git add .
     git commit -m "Initial commit with uv setup"
     git push origin main
     ```

---

### **What is `uv project add`?**
As of now, `uv` does not have a `project add` command. However, this might refer to adding dependencies to your project. Here's how you can manage dependencies with `uv`:

- **Add a Dependency**:
  - Add the package name to your `requirements.in` or `pyproject.toml` file.
  - Reinstall dependencies:
    ```bash
    uv pip install -r requirements.in
    ```
    Or:
    ```bash
    uv pip install .
    ```

- **Install a Dependency Directly**:
  - You can also install a package directly and add it to your requirements file:
    ```bash
    uv pip install requests
    uv pip freeze > requirements.txt
    ```

---

### **How to Manage Python Versions**
Managing Python versions is crucial for ensuring compatibility across environments. Here's how to do it with `uv`:

#### 1. **Use a `.python-version` File**
   - Create a `.python-version` file in your repository to specify the Python version:
     ```
     3.9
     ```
   - Tools like `pyenv` can read this file to automatically switch to the correct Python version.

#### 2. **Use `pyenv` to Manage Python Versions**
   - Install `pyenv` to manage multiple Python versions:
     ```bash
     curl https://pyenv.run | bash
     ```
   - Install the desired Python version:
     ```bash
     pyenv install 3.9.0
     ```
   - Set the local Python version for your project:
     ```bash
     pyenv local 3.9.0
     ```

#### 3. **Use `uv` with the Correct Python Version**
   - Ensure `uv` uses the correct Python version by activating the virtual environment created with the desired Python version:
     ```bash
     uv venv .venv --python=3.9
     source .venv/bin/activate
     ```

#### 4. **Specify Python Version in `pyproject.toml`**
   - If using `pyproject.toml`, you can specify the Python version compatibility:
     ```toml
     [project]
     requires-python = ">=3.9,<3.10"
     ```

#### 5. **Check Python Version in CI/CD**
   - In your CI/CD pipeline (e.g., GitHub Actions), ensure the correct Python version is used:
     ```yaml
     jobs:
       build:
         runs-on: ubuntu-latest
         steps:
           - uses: actions/checkout@v3
           - uses: actions/setup-python@v4
             with:
               python-version: '3.9'
           - run: uv pip install -r requirements.txt
     ```

---

### **Summary**
- Use `uv` to create virtual environments, install dependencies, and generate lock files.
- Manage Python versions with tools like `pyenv` or by specifying the version in your project configuration.
- `uv` simplifies dependency management and speeds up workflows, making it an excellent choice for modern Python projects.

By following these steps, you can set up a clean, efficient, and reproducible Python development environment in your GitHub repository using `uv`.

