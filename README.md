# kfp-hello-world

## Installation instructions

Assumes pyenv and poetry. 

```zsh
pyenv install 3.10.0
pyenv local 3.10.0
poetry new kfp-hello-world
cd kfp-hello-world
poetry config virtualenvs.in-project true # facilitates VS Code finding poetry venv
poetry env use 3.10.0
poetry add kfp=2.0.1
# When you come back to this later, may need to activate poetry shell
# poetry shell
code .
```

In VS Code, open Command Palette, Select Python Interpreter... select matching
poetry env.

Run code by right-clicking and running in IDE or use 
`poetry run python <script>.py` from shell.