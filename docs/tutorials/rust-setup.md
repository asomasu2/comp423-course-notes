# Setting up a dev container for Rust

* Primary author: [Arun Somasundaram](https://github.com/asomasu2)
* Reviewer: [Nathan Jacobs](https://github.com/nathjaco1016)

If you want to set up a development container in the programming language Rust, you have come to the right place to learn! Before we start, here are a couple of prerequisites you must have before we dive right in! Much of the content before setting up the development environment cites the Mkdocs tutorial from Comp 423. 

- Install Visual Studio Code
- Install Git
- Install Docker
- Have a GitHub account

Step 1: Create a New Directory and Initialize Git

(A) Open your terminal or command prompt.

(B) Create a new directory for your project.
``` py
mkdir rust-dev-container
```
(C) Go into this directory.
``` py
cd rust-dev-container
```
(D) Initialize a new Git repository.
``` py
cd rust-dev-container
```
(E) Create a README file:
``` py
echo "# Rust Dev Container" > README.md
git add README.md
git commit -m "Initial commit with README"
```
Step 2. Create a Remote Repository on GitHub

(1) Log into GitHub account and navigate to the Create a New Repository page.

(2) Fill in the details as follows:

- Repository Name: rust-dev-container
- Description: "Setting up a rust-dev-container"
- Visibility: Public

(3) Do not initialize the repository with a README, .gitignore, or license.

(4) Click Create Repository.

Step 3. Link your Local Repository to GitHub

(1) Add the GitHub repository:
```py
git remote add origin https://github.com/<your-username>/comp423-course-notes.git
```
(2) Replace <your-username> with your GitHub username.

(2) Check your default branch name with the subcommand git branch. If it's not main, rename it to main with the following command: git branch -M main. Old versions of git choose the name master for the primary branch, but these days main is the standard primary branch name.

(3) Push your local commits to the GitHub repository:
```py
git push --set-upstream origin main
```

Part 2. Setting Up the Development Environment

Now that we have GitHub all set up, it is time to actually set up the development environment.

Step 1. Add Development Container Configuration

- In VS Code, open the rust-dev-container directory. You can do this via: File > Open Folder.
- Install the Dev Containers extension for VS Code.
- Create a .devcontainer directory in the root of your project with the following file inside of this "hidden" configuration directory:
.devcontainer/devcontainer.json

- Copy and paste this into .devcontainer.json
```py
{
    "name": "Rust Development Environment",
    "image": "mcr.microsoft.com/devcontainers/rust:latest",
    "customizations": {
        "vscode": {
            "extensions": [
                "rust-lang.rust-analyzer"
            ]
        }
    }
}
```


