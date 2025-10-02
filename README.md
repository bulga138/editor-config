# editor-config

This repository uses `.editorconfig` to maintain consistent coding styles and settings across all files. The configuration ensures that all developers use the same formatting rules regardless of their editor or IDE.

## Setup as Git submodule

To use this editor configuration as a submodule in your parent project:
```bash
# Add the submodule to your repository
git submodule add https://github.com/bulga138/editor-config.git .editor-config

# Initialize and update the submodule
git submodule init
git submodule update
```

Create the file `.editorconfig` in the main project:
```bash
# This is the .editorconfig file in your MAIN PROJECT repo root
root = true

# Import all rules from the shared submodule
[**]
include = .editor-config/.editorconfig
```

To avoid repeating the submodules commands, configure git:
```bash
# Configure Git to automatically recurse into submodules on clone and pull
git config --global submodule.recurse true

# Configure Git to automatically update submodules on fetch
git config --global fetch.recurseSubmodules true

# Create a convenient alias for the standard pull + submodule update command
git config --global alias.pullall '!git pull && git submodule update --init --recursive'

# To pull latest version of the submodule
git pull --recurse-submodules
# or the created alias
git pullall
```

### Parent Project Configuration

The parent project should include the following in its `.gitmodules` file:

```bash
[submodule ".editor-config"]
    path = .editor-config
    url = https://github.com/bulga138/editor-config.git
```
