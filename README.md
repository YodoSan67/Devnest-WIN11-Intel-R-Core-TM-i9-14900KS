# 🖥 Windows 11 ARM64

This project provides a simple way to deploy a clean, temporary Windows environment directly from GitHub Actions. Get on-demand access to a full Windows graphical user interface, perfect for testing, development, or running specific Windows applications without needing a local virtual machine.

## ✨ Key Features

*   🚀 **On-Demand Deployment**: Run the workflow whenever you need a fresh Windows environment.
*   🔧 **Customizable Setup**: Use your own PowerShell script from a Gist to automatically install any software or configurations you need.
*   🔒 **Secure Tunneling**: Utilizes Ngrok to create a secure, accessible connection to your environment from anywhere.
*   ☁️ **Fully Cloud-Based**: Requires no installation or configuration on your local machine. Everything runs on GitHub's infrastructure.

## ⚙️ How It Works

This workflow automates the entire process for you:

1.  **📥 Download Script**: The workflow fetches your custom PowerShell setup script from the Gist URL you provide.
2.  **⚙️ Execute**: The script is run inside a Windows runner, preparing the environment, installing applications, and setting up users.
3.  **🔗 Create Tunnel**: A secure tunnel is established using Ngrok, exposing the environment's connection port to the public internet.
4.  **📊 Display Details**: The unique address and port for your connection are displayed in the workflow logs, ready for you to use.

## 🚀 Getting Started Guide

Follow these steps to get your first Windows environment running.

### 1. Prerequisites

*   A GitHub account.
*   An [Ngrok](https://ngrok.com/) account (a free account is sufficient).

### 2. Configuration: Set Your Ngrok Token

The workflow requires your Ngrok authentication token to create a secure tunnel. You must save this as a repository secret.

1.  Copy your **Auth Token** from your [Ngrok dashboard](https://dashboard.ngrok.com/get-started/your-authtoken).
2.  In your GitHub repository, go to **Settings** > **Secrets and variables** > **Actions**.
3.  Click **New repository secret**.
4.  Name the secret `NGROK_AUTH_TOKEN`.
5.  Paste your Auth Token into the **Secret** field.
6.  Click **Add secret**.

### 3. Run the Workflow

1.  Go to the **Actions** tab in your repository.
2.  Under the workflows list on the left, select **"🖥️ Deploy Windows Environment 🚀"**.
3.  Click the **Run workflow** button on the right.
4.  (Optional) You can change the **Gist URL** if you want to use your own custom setup script.
5.  Click the green **Run workflow** button.

### 4. Connect to Your Environment

Once the workflow starts, navigate to the running job's summary page.

1.  Wait for the main execution job to start running.
2.  Click on the job to view the live log output.
3.  Towards the end of the log, you will see a clearly printed box containing the connection details.

    ```text
    +-----------------------------------------------------------------+
    |                                                                 |
    |      ✅💻 YOUR WINDOWS ENVIRONMENT IS READY! 💻✅               |
    |                                                                 |
    +-----------------------------------------------------------------+
    |   Use the details below to start your graphical session:          |
    |                                                                 |
    |   🖥️  Address (IP/Hostname) : 0.tcp.ngrok.io:12345              |
    |   👤  Username              : (As set in your script)           |
    |   🔑  Password              : (As set in your script)           |
    |                                                                 |
    +-----------------------------------------------------------------+
    ```
4.  Use this address and credentials with your preferred remote desktop client to access the Windows graphical interface.

The environment will remain active until the workflow reaches its timeout (360 minutes) or you cancel it manually.

## 🔧 Customization

You can easily customize the environment by modifying the PowerShell script. Simply create your own public Gist with a `setup.ps1` file and provide its raw URL when running the workflow. This allows you to:

*   Install specific software (e.g., `winget install vscode`).
*   Set up environment variables.
*   Download and configure project files.

## 📄 License

This project is licensed under the [MIT License](LICENSE).
