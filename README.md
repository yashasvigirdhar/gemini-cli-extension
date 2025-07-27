# My Gemini CLI Extensions, Commands, and Settings

This repository is a collection of my personal extensions, custom commands, and settings for the [Google Gemini CLI](https://github.com/google-gemini/gemini-cli). If you are looking for a cheat sheet, see the [cheatsheet here](https://www.philschmid.de/gemini-cli-cheatsheet).

## 🚀 How to Use
    
You can install these configurations globally for all projects or locally for a single project.

**Global Installation:**

```bash
git clone --depth 1 https://github.com/philschmid/gemini-cli-extension.git ~/.gemini-tmp && rsync -av ~/.gemini-tmp/.gemini/ ~/.gemini/ && rm -rf ~/.gemini-tmp
```

**Project-Specific Installation:**

```bash
git clone --depth 1 https://github.com/philschmid/gemini-cli-extension.git .gemini-tmp && rsync -av .gemini-tmp/.gemini/ ./.gemini/ && rm -rf .gemini-tmp
```

**Note:** Both methods may overwrite existing configuration files with the same name.

## 🛠️ Custom Commands

Custom commands allow you to create powerful, reusable prompts. They are defined in TOML files and stored in a `commands` directory.

-   **Global commands:** `~/.gemini/commands/`
-   **Project-specific commands:** `<project>/.gemini/commands/`

### Example Command

Here is an example of a custom command definition in a `.../commands/test/gen.toml` file:

```toml
# Invoked as: /test:gen "Create a test for the login button"
description = "Generates a unit test based on a description."
prompt = """
You are an expert test engineer. Based on the following requirement, please write a comprehensive unit test using the Jest testing framework.

Requirement: {{args}}
"""
```

See the [custom commands guide](https://github.com/google-gemini/gemini-cli/blob/main/docs/cli/commands.md#custom-commands) for more details.

---

## ✨ Extensions

Extensions allow you to bundle tools, context, and configurations. Each extension is a directory with a `gemini-extension.json` file.

-   **Global extensions:** `~/.gemini/extensions/`
-   **Project-specific extensions:** `<workspace>/.gemini/extensions/`

### Example Extension

An extension is defined by a `gemini-extension.json` file inside its own directory, for example `<workspace>/.gemini/extensions/my-extension/gemini-extension.json`:

```json
{
  "name": "my-extension",
  "version": "1.0.0",
  "mcpServers": {
    "my-server": {
      "command": "node my-server.js"
    }
  },
  "contextFileName": "GEMINI.md",
  "excludeTools": ["run_shell_command"]
}
```

For more details, see the [extensions guide](https://github.com/google-gemini/gemini-cli/blob/main/docs/extension.md).

---

## ⚙️ Settings (`settings.json`)

You can customize the Gemini CLI's behavior by creating a `settings.json` file.

-   **Project-level:** `.gemini/settings.json`
-   **User-level:** `~/.gemini/settings.json`
-   **System-level:** `/etc/gemini-cli/settings.json`

### Example `settings.json`

```json
{
  "theme": "GitHub",
  "autoAccept": false,
  "sandbox": "docker",
  "checkpointing": {
    "enabled": true
  },
  "fileFiltering": {
    "respectGitIgnore": true
  },
  "usageStatisticsEnabled": true
}
```

All details are in the [configuration guide](https://github.com/google-gemini/gemini-cli/blob/main/docs/cli/configuration.md).

---

## 📄 Context Files (`GEMINI.md`)

Use `GEMINI.md` files to provide instructions and context to the model for your projects. The CLI loads these files hierarchically.

-   **Global context:** `~/.gemini/GEMINI.md`
-   **Project/Ancestor context:** `GEMINI.md` files from the current directory up to the root.

You can use imports to modularize your context: `@./path/to/another.md`.

### Example `GEMINI.md`

```markdown
# Main Project Context: My Awesome App

## General Instructions
- All Python code must be PEP 8 compliant.
- Use 2-space indentation for all new files.

## Component-Specific Style Guides
@./src/frontend/react-style-guide.md
@./src/backend/fastapi-style-guide.md
```
