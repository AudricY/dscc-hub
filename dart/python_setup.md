# Setting Up Python and Visual Studio Code

## Step 1: Install Python

1. **Download Python**:

   - Visit the official Python website: [python.org/downloads](https://www.python.org/downloads/)
   - Download the latest version for your operating system.

2. **Run the Installer**:

   - Run the installer you downloaded.
   - Make sure to check the box that says **"Add Python to PATH"**.
   - Select **"Install Now"**.

3. **Verify the Installation**:
   - Open a terminal or command prompt.
   - Type `python --version` to check the Python version installed.

## Step 2: Install Visual Studio Code

1. **Download Visual Studio Code**:

   - Visit the official Visual Studio Code website: [code.visualstudio.com](https://code.visualstudio.com/)
   - Download the version for your operating system.

2. **Run the Installer**:
   - Run the installer you downloaded.
   - Follow the prompts to complete the installation.
   - Optionally, select to add "Open with Code" to the context menu for files and folders during installation.

## Step 3: Set Up Python in Visual Studio Code

1. **Open Visual Studio Code**:

   - Launch Visual Studio Code.

2. **Install Python Extension**:

   - Open the Extensions view by clicking on the Extensions icon in the Activity Bar on the side of the window or pressing `Ctrl+Shift+X`.
   - Search for the Python extension by Microsoft.
   - Click **Install**.

3. **Configure Python Interpreter**:

   - Open the Command Palette by pressing `Ctrl+Shift+P`.
   - Type `Python: Select Interpreter` and select it.
   - Choose the Python interpreter you installed earlier from the list.

4. **Create a Python File**:

   - Create a new file with a `.py` extension, for example, `hello.py`.
   - Add a simple Python script to the file:
     ```python
     print("Hello, world!")
     ```

5. **Run the Python File**:
   - Open the integrated terminal by pressing `Ctrl+`` (backtick).
   - Ensure you are in the directory where your Python file is located.
   - Run the script by typing `python hello.py`.

## Step 4: Set Up a Virtual Environment (Optional)

1. **Create a Virtual Environment**:

   - Open a terminal in Visual Studio Code.
   - Navigate to your project directory.
   - Run the following command to create a virtual environment:
     ```bash
     python -m venv venv
     ```
   - This creates a virtual environment in a folder named `venv`.

2. **Activate the Virtual Environment**:

   - On Windows:
     ```bash
     .\venv\Scripts\activate
     ```
   - On macOS and Linux:
     ```bash
     source venv/bin/activate
     ```

3. **Install Packages**:

   - With the virtual environment activated, you can install packages using `pip`:
     ```bash
     pip install <package_name>
     ```

4. **Configure Visual Studio Code to Use the Virtual Environment**:
   - Open the Command Palette (`Ctrl+Shift+P`).
   - Type `Python: Select Interpreter` and select it.
   - Choose the interpreter from the `venv` folder (it will be listed as something like `.\venv\Scripts\python.exe`).

By following these steps, you'll have a Python development environment set up with Visual Studio Code, ready for your projects.

## Common mistakes:

1. **Python setup**
   - **DO NOT INSTALL FROM MICROSOFT STORE**, download from the website itself
   - If you did not install to path, get the full path of your python folder and add it manually to your environment variables under **Path** in **System variables**, or you can reinstall python if you are having troubles

## Tips:

1. **Python tips**

   - You can use jupyter files to test segments of your code, especially useful for AIML

2. **VSC tips**
   - VSC has many extensions that can help improve your coding experience. Here are some we would suggest using:
     - GitLens (When you start using github)
     - Live Server (For frontend development)
