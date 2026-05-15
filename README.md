# DemoRepo

[![CI](https://github.com/nanddeepn/DemoRepo/actions/workflows/blank.yml/badge.svg)](https://github.com/nanddeepn/DemoRepo/actions/workflows/blank.yml)

A demonstration repository showcasing GitHub Actions. This project contains example implementations of GitHub Actions using both Docker and JavaScript/Node.js, serving as templates and learning resources for creating custom GitHub Actions.

## 📋 Table of Contents

- [Overview](#overview)
- [Project Contents](#project-contents)
  - [Hello World Docker Action](#hello-world-docker-action)
  - [Hello World JS Action](#hello-world-js-action)
- [Getting Started](#getting-started)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)

## Overview

This repository demonstrates how to create and use custom GitHub Actions. It includes two example actions that greet a user or entity and output the timestamp of execution. These actions serve as templates for understanding GitHub Actions structure and capabilities.

## Project Contents

### Hello World Docker Action

A GitHub Action implemented using Docker. This action demonstrates how to containerize and deploy action logic using a Dockerfile.

**Location:** [`hello-world-docker-action/`](hello-world-docker-action/)

**Features:**
- Containerized action using Docker
- Takes a name input and outputs a greeting
- Records and returns the timestamp of execution

**Key Files:**
- `action.yml` - Action metadata and configuration
- `Dockerfile` - Container specification
- `entrypoint.sh` - Docker entry point script
- `README.md` - Action-specific documentation

### Hello World JS Action

A GitHub Action implemented using Node.js/JavaScript. This action demonstrates a lightweight JavaScript-based action without containerization.

**Location:** [`hello-world-js-action/`](hello-world-js-action/)

**Features:**
- Lightweight JavaScript implementation
- Takes a name input and outputs a greeting
- Records and returns the timestamp of execution

**Key Files:**
- `action.yml` - Action metadata and configuration
- `index.js` - Main action logic

## Getting Started

### Prerequisites

- GitHub account with repository access
- Familiarity with GitHub Actions workflows
- For development: Docker (if modifying Docker action) and Node.js (if modifying JS action)

### Using the Docker Action in Your Workflow

```yaml
- name: Hello World Docker Action
  uses: nanddeepn/DemoRepo/hello-world-docker-action@v1
  with:
    who-to-greet: 'Mona the Octocat'
```

### Using the JS Action in Your Workflow

```yaml
- name: Hello World JS Action
  uses: nanddeepn/DemoRepo/hello-world-js-action@v1
  with:
    who-to-greet: 'Mona the Octocat'
```

## Usage

### Action Inputs

Both actions accept the following input:

- **`who-to-greet`** (required): The name of the person or entity to greet
  - Default: `"World"`
  - Example: `"Mona the Octocat"`

### Action Outputs

Both actions provide the following output:

- **`time`**: The timestamp when the greeting was generated

### Example Workflow

```yaml
name: Demo Actions

on: [push]

jobs:
  hello-docker:
    runs-on: ubuntu-latest
    steps:
      - name: Run Docker Action
        uses: nanddeepn/DemoRepo/hello-world-docker-action@v1
        with:
          who-to-greet: 'Developer'
      - name: Print Output
        run: echo "Greeting completed"

  hello-js:
    runs-on: ubuntu-latest
    steps:
      - name: Run JS Action
        uses: nanddeepn/DemoRepo/hello-world-js-action@v1
        with:
          who-to-greet: 'Developer'
      - name: Print Output
        run: echo "Greeting completed"
```

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss what you would like to change.

### Development Setup

1. **For Docker Action:**
   - Modify `hello-world-docker-action/entrypoint.sh` for script changes
   - Update `Dockerfile` if dependencies change
   - Test locally using Docker

2. **For JS Action:**
   - Modify `hello-world-js-action/index.js` for logic changes
   - Ensure Node.js compatibility
   - Test locally before submitting

### Testing

Before submitting changes:
1. Test your modifications locally
2. Ensure the actions still work as expected
3. Update documentation if behavior changes

## License

This project is licensed under the MIT License. See the LICENSE file for details.

## Security

For security-related information, please see [SECURITY.md](SECURITY.md).
