# Data Science Repository Template
![license](https://img.shields.io/badge/license-MIT-green)
![python](https://img.shields.io/badge/python->3.10-orange?logo=Python&logoColor=white)
![R](https://img.shields.io/badge/R->4.4.2-blue?logo=R)
![Quarto](https://img.shields.io/badge/quarto->1.6-skyblue?logo=quarto)


## 📊 Overview

This repository serves as a data science project template that enables seamless reproducibility using **Quarto**. It supports both **Python** (via UV) and **R** (via renv), ensuring a streamlined workflow for working with Jupyter notebooks and publishing results to **GitHub Pages**.

## 🚀 Features

- 📂 **Structured project layout** for easy navigation.
- 📜 **Quarto-powered** rendering of Jupyter notebooks.
- 🏗 **GitHub Actions workflow** to automate Quarto rendering and deployment of results to GitHub Pages.
- 🐍 **Python dependency management** with [UV](https://github.com/astral-sh/uv).
- 📦 **R dependency management** with [renv](https://rstudio.github.io/renv/).
- 📑 Example Jupyter notebook to get started.

## 🛠 Generating a New Project

This project template is managed using **Copier**, which allows you to quickly generate a new repository with the predefined structure. To create a new project, run:

```bash
copier copy https://github.com/AlFontal/data-science-quarto-template.git my-new-project
cd my-new-project
```

This will prompt you for necessary project details and generate a customized project setup.


## 🔧 Setup & Usage

### 1️⃣ Install Dependencies

#### Python
```bash
uv venv .venv
source .venv/bin/activate
uv pip install
```

#### R
```r
install.packages("renv")
renv::restore()
```

### 2️⃣ Run Quarto
```bash
quarto render
```

### 3️⃣ Deploy (GitHub Actions)
Push changes to `main`, and the **GitHub Actions workflow** will automatically render and deploy to **GitHub Pages**. While it would be possible if desired to re-run each of the notebooks in GitHub Actions, we have opted to only render the notebooks to avoid unnecessary computation time and resources (especially given that GitHub Actions has a limit on the amount of time a workflow can run and extra time is charged).

## 📁 Project Structure
```
{{ project_name }}/
├── .github/workflows/render.yml   # GitHub Actions workflow
├── notebooks/                     # Jupyter notebooks
│   ├── example.ipynb              # Example notebook
├── quarto.yml                      # Quarto project config
├── pyproject.toml                  # Python dependencies (UV)
├── renv.lock                       # R dependencies
└── README.md                       # This file
```

