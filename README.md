# Jupyter environment template

This is a repo to demonstrate how you can set up a containerized jupyter environment.

## Intro to dev containers

Dev containers allow you to define you development environment in a declarative way. By cloning this repo and using the vscode command ![launch in container](readme/outside-container.png), vscode will build the development container and re-launch vscode. From then on, your vscode is running from inside the container. Any terminals you open are terminals in that container. Anything installed in those terminals are installed to the container and not to your local machine. Its simple to get back to a clean original state, so don't hesitate to experiment!

In this repo you'll see a .devcontainer/devcontainer.json file. It lists vscode extensions, so everyone working on this repo is guaranteed to have the same set. It also lists features, which are publicly available units of installation code which make it easy to install libraries and tools into your development environment. They're very powerful, and I recommend learning more!

## Reseting your development container

The first step is understanding if your vscode is in the development container or outside it your local machine. If you're on your local, the bottom left corner of vscode will look like touching green aligator clips ![running local](readme/local-vscode.png.png). If you're in the development container, the bottom left corner of vscode say "Dev Container: jupyter" ![remote vscode](readme/remote-vscode.png.png). Next, open the command pallete with `VIEW -> Command Palette`. If you're on your local, run the command `Dev Containers: Rebuild and Reopen in Container`. If your in the development container, run the command `Dev Containers: Rebuild Container`.

## Adding to the environment

If you want to add stuff to create your own dev container so you too can have a clean, dependable notebooks setup, there are two spots to know about.

In .devcontainer/devcontainer.json you can add extensions to vscode and add features to your environment. In scripts/install-dependencies.sh, you can you can add on to a bash script that runs after the container starts. I recommend using features over manually managing dependency install commands because its an easy way to bake what you need in to the container image which makes rebuilding faster (typically).

## Connecting to things outside the dev container

If there is some resource you need to connect to that can only be accessed by your local machine, you can use `host.docker.internal` as in this example where we connect to a MySQL instance running on your local machine from inside your dev container.

## Containers in containers

This repo comes with Docker-in-docker installed in you development container. This allows you to spin up containers within your development environment. Want to spin up a temp MySQL that only you dev container knows about? No problem! 