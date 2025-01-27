# Setting up a dev container for Rust

* Primary author: [Arun Somasundaram](https://github.com/asomasu2)
* Reviewer: [Nathan Jacobs](https://github.com/nathjaco1016)

If you want to set up a development container in the programming language Rust, you have come to the right place to learn! Before we start, here are a couple of prerequisites you must have before we dive right in! Much of the content before setting up the development environment cites the Mkdocs tutorial from Comp 423. 

## **Part 0**: Prerequisites

- Install Visual Studio Code
    - Install the Dev Containers extension for VS Code (Extensions > Type Dev Containers in the search bar and click the first option > Hit Install)
- Install Git
- Install Docker
- Have a GitHub account

## **Part 1**: Initialization

### Step 1: Create a New Directory and Initialize Git :rocket:

(A) Open your terminal or command prompt.

(B) Create a new directory for your project.
``` bash
mkdir rust-dev-container
```
(C) Go into this directory.
``` bash
cd rust-dev-container
```
(D) Initialize a new Git repository.
``` bash
git init
```
(E) Create a README file:
``` bash
echo "# Rust Dev Container" > README.md
git add README.md
git commit -m "Initial commit with README"
```
### Step 2: Create a Remote Repository on GitHub

(A) Log into GitHub and click the green "New" button next to "Top Repositories"

(B) You only need to fill in these details, do not do anything else:

- Repository Name: rust-dev-container
- Description: "Setting up a rust-dev-container"
- Visibility: Public

(D) Click Create Repository.

### Step 3. Link your Local Repository to GitHub

(A) Add the GitHub repository by typing this in the same terminal you opened earlier:
``` bash
git remote add origin https://github.com/<your-username>/rust-dev-container.git
```
(B) Replace <your-username> with your GitHub username.

(C) Check your default branch name with the subcommand git branch. If it's not main, rename it to main with the following command: git branch -M main.

(D) Push your local commits to the GitHub repository:
``` bash
git push --set-upstream origin main
```

## **Part 2**: Setting Up the Development Environment

Now that we have GitHub all set up, it is time to actually set up the development environment.

### Step 1: Make the dev container directory

- Open VS Code
- Click File > Open > rust-dev-container
- Open your terminal and type:
``` bash
mkdir .devcontainer
```
This creates the directory in your project

### Step 2: Set up the JSON file

To make the dev container json file, type the following in the terminal:
``` bash
cd .devcontainer
touch devcontainer.json
```

Now we have this file inside the right directory.

Copy and paste this into .devcontainer.json:
``` json
{
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

### Step 3: Inside the Dev Container

Now to run Rust in the our Docker environment, click Command + Shift + P

Then, type in Dev Container: Reopen in Dev Container, and select this option

After loading for a moment, you will now be inside a Rust project. To make sure you are using rust, type and enter:

``` bash
rustc --version
```
If the following output is rustc followed by a float, you are good to go!

## **Part 3**: Hello World

### Step 1: Create and navigate to a new file for our Rust program

``` bash
cargo new hello-comp423 --vcs none
cd hello-comp423
```

### Step 2: Go to Explorer > hello-comp423 > src > main.rs

The contents of the file should be:

``` RUST
fn main() {
    println!("Hello, world!");
}
```

### Step 3: Modify the inside of the println! parentheses to say "Hello COMP423"

``` RUST
fn main() {
    println!("Hello COMP423");
}
```

### Step 4: Type and enter this inside your VS Code terminal:
``` bash
cargo build
```
Now, we have compiled our code, but we have not run it yet.

### Step 5: To run our code, we can type and enter:

``` bash
./target/debug/hello-comp423
```

You should now see "Hello COMP423" printed in your terminal!

!!! info "Cargo Run"
    We can actually do both of the previous steps in one step by running:

    ```bash
    cargo run
    ```

This step compiles our file, and runs it to see the same output in the terminal!

### Step 6: Pushing the completed project to github

Run the following code in the terminal to update your github repo:

``` bash
git add .
git commit -m "Completed the hello-comp423 program."
git push -u origin main
```

## **Summary** 

In this project, we:

* Initialized a repository and linked it to github
* Set up a development environment
* Created a fully functional RUST program

That's it everyone! Congratulations on building your first ever Rust program! :smile: