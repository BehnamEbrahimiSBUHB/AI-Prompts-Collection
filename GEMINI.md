# Directory Overview

This repository, "AI Prompts Collection," is a curated collection of resources for interacting with various AI models, including Google's Gemini, OpenAI's GPT series, and GitHub Copilot. It is a non-code project, meaning it does not contain source code, build scripts, or application logic. Instead, it serves as a knowledge base and toolkit for developers, prompt engineers, and AI enthusiasts.

The primary purpose of this directory is to provide a structured and comprehensive set of prompts, instructional materials, and configuration files to enhance the effectiveness of AI-assisted workflows in software development and other domains.

## Key Files and Directories

The repository is organized into the following key areas:

*   **`README.md`**: The main entry point for understanding the project. It provides a high-level overview of the repository's purpose, structure, and usage.

*   **`.github/`**: This directory is the core of the collection and contains resources primarily for enhancing the GitHub Copilot experience.
    *   **`prompts/`**: Contains a variety of pre-written prompts for common software development tasks, such as creating README files, generating multi-stage Dockerfiles, and writing conventional commit messages.
    *   **`instructions/`**: A collection of markdown files with detailed instructions and best practices for various technologies (e.g., Docker, C#, PowerShell) and methodologies. These are intended to be used as context for AI assistants.
    *   **`chatmodes/`**: Custom "personas" or modes for GitHub Copilot Chat, allowing users to tailor the AI's responses to specific roles, such as a critical thinker or a C#/.NET specialist.

*   **`.gemini/`**: Contains resources specifically for Google's Gemini models.
    *   **`commands/`**: Holds `.toml` files that define custom commands for the Gemini CLI.
    *   **`gemini-for-google-workspace-prompting-guide-101.pdf`**: A PDF guide on how to effectively prompt Gemini within the Google Workspace ecosystem.

*   **`openai/`**: Includes guides and Jupyter notebooks for working with OpenAI's GPT models. It has subdirectories for different model versions (`gpt-4.1/`, `gpt-5/`) containing prompting guides and best practices.

*   **`guides/`**: A collection of general guides and text files on various technical topics, such as data science libraries and visualization tools.

## Usage

The contents of this directory are intended to be used as a reference and a practical toolkit for improving interactions with generative AI models. The intended workflow is as follows:

1.  **Browse and Discover:** Users can explore the different directories to find prompts, instructions, or chat modes relevant to their current task.
2.  **Copy and Adapt:** The prompts and instructions can be copied and pasted directly into an AI chat interface or used as a foundation for creating more specific and customized prompts.
3.  **Integrate and Configure:** The chat modes in the `.github/chatmodes/` directory can be used to configure GitHub Copilot to adopt a specific persona, leading to more specialized and context-aware responses. The instructions in `.github/instructions/` can be provided to the AI to give it a better understanding of the desired output and conventions.
