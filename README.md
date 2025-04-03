# Data Science Repository Template
![license](https://img.shields.io/badge/license-MIT-green)
![python](https://img.shields.io/badge/python->3.10-orange?logo=Python&logoColor=white)
![R](https://img.shields.io/badge/R->4.4.2-blue?logo=R)
![Quarto](https://img.shields.io/badge/quarto->1.6-skyblue?logo=quarto)

## Overview

This repository serves as a data science project template that enables seamless reproducibility using **Quarto**. It supports both **Python** (via `uv`) and **R** (via `renv`), ensuring a streamlined workflow for working with Jupyter notebooks and publishing results to **GitHub Pages**.

I made it to serve my own needs, but I hope it can be useful to others as well. Feel free to use it as a starting point for your own projects, and let me know if you have any suggestions or improvements!

## Features

- 📂 **Structured project layout** for easy navigation.
- 📜 **Quarto-powered** rendering of Jupyter notebooks.
- 🏗 **GitHub Actions workflow** to automate Quarto rendering and deployment of results to GitHub Pages.
- 🐍 **Python dependency management** with [uv](https://github.com/astral-sh/uv).
- 📦 **R dependency management** with [renv](https://rstudio.github.io/renv/).
- 📑 Example Jupyter notebook to get started.

I include some opinionated choices and customizations of my own liking, such as the `custom.css` file for styling the rendered notebooks, and the default usage of `hypothes.is` for comments and annotations. These are all optional and can be removed or modified as needed.

## Generating a New Project

This project template is managed using **Copier**, which allows you to quickly generate a new repository with the predefined structure. To create a new project, run:

```bash
copier copy https://github.com/AlFontal/data-science-quarto-template.git my-new-project
cd my-new-project
```

This will prompt you for necessary project details and generate a customized project setup.


## 🔧 Setup & Usage

### Installation of Dependencies

This will depend on whether you are using Python or R (or both). The following steps outline the setup process for each language, assuming that your `pyproject.toml` and `renv.lock` files are already present with some dependencies defined. I have (very opinionatedly) chosen to include some common data science libraries in the dependencies of both template files, but you can modify these as needed.

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

### Running Quarto

You can render the notebooks and see how they look locally by running the following command from the root of the project:

```bash
quarto render notebooks
```

### Deployment to GitHub Pages

Push changes to `main`, and the **GitHub Actions workflow** will automatically render and deploy to **GitHub Pages**. While it would be possible if desired to re-run each of the notebooks in GitHub Actions, we have opted to only render the notebooks to avoid unnecessary computation time and resources (especially given that GitHub Actions has a limit on the amount of time a workflow can run and extra time is charged).

## 📁 Project Structure

The way the project structure is thought is the following: We have 4 main folders — `data/`, `output/`, `code/`, and `reports/` — where we store our data files, output files (generated by the analyisis), source code, and Jupyter notebooks executing the analyses respectively. We also have a `assets/` folder for static assets such as images or any other files not directly related to the analysis. The idea is that the `data/` folder contains the immutable source files that are wrangled and modified by the code in the `code/` folder, which in turn generates the output files in the `output/` folder.

The other files in the top level directory serve as configuration files for the project, such as the `pyproject.toml` and `renv.lock` files for managing dependencies, the `.gitignore` file to specify which files to ignore when pushing to the repository, and the workflow file for GitHub Actions.

```
{{ project_name }}/
├── .github/workflows/render.yml     # GitHub Actions workflow
├── data/                           # Data files folder
├── output/                         # Output files folder
├── code/                           # Source code files
├── assets/                         # Static assets
└── reports/                        # GH Pages reports and notebooks
    ├── _quarto.yml                 # Quarto project config
    ├── example.ipynb               # Example notebook
    └── custom.css                  # CSS for styling
├── pyproject.toml                  # Python dependencies (uv)
├── renv.lock                       # R dependencies
├── README.md                       # Main repository README
└── .gitignore                      # Git ignore file
```

