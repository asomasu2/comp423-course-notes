# Setting up a dev container for Rust

* Primary author: [Arun Somasundaram](https://github.com/asomasu2)
* Reviewer: [Nathan Jacobs](https://github.com/nathjaco1016)

If you want to set up a development container in the programming language Rust, you have come to the right place to learn! Before we start, here are a couple of prerequisites you must have before we dive right in! Much of the content before setting up the development environment cites the Mkdocs tutorial from Comp 423. 

- Install Visual Studio Code
    - Install the Dev Containers extension for VS Code (Extensions > Type Dev Containers in the search bar and click the first option > Hit Install)
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
git init
```
(E) Create a README file:
``` py
echo "# Rust Dev Container" > README.md
git add README.md
git commit -m "Initial commit with README"
```
Step 2. Create a Remote Repository on GitHub

(1) Log into GitHub and click the green "New" button next to "Top Repositories"

(2) You only need to fill in these details:

- Repository Name: rust-dev-container
- Description: "Setting up a rust-dev-container"
- Visibility: Public

(3) Do not initialize the repository with a README, .gitignore, or license.

(4) Click Create Repository.

Step 3. Link your Local Repository to GitHub

(1) Add the GitHub repository by typing this in the same terminal you opened earlier:
```py
git remote add origin https://github.com/<your-username>/rust-dev-container.git
```
(2) Replace <your-username> with your GitHub username.

(2) Check your default branch name with the subcommand git branch. If it's not main, rename it to main with the following command: git branch -M main.

(3) Push your local commits to the GitHub repository:
```py
git push --set-upstream origin main
```

Part 2. Setting Up the Development Environment

Now that we have GitHub all set up, it is time to actually set up the development environment.

Step 1. Add Development Container Configuration

- Open VS Code
- Click File > Open > rust-dev-container
- Open your terminal and type:
```py
mkdir .devcontainer
```
This creates the directory in your project

Next type:
```py
touch .devcontainer.json
```

Now we have this file inside the right directory.

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

Now to run Rust in the our Docker environment, click Command + Shift + P

Then, type in Dev Container: Reopen in Dev Container, and select this option

After loading for a moment, you will now be inside a Rust project. To make sure you are using rust, type and enter:

```py
rustc --version
```
If the following output is rustc followed by a float, you are good to go!

Part 3: Hello World

(A) Create and navigate to a new file for our Rust program

```py
cargo new hello-comp423 --vcs none
cd hello-comp423
```

(B) Go to Explorer > hello-comp423 > src > main.rs

The contents of the file should be:

```py
fn main() {
    println!("Hello, world!");
}
```