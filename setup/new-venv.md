# Install Python versions
```
pyenv install 3.9.8     
```

To set a specific version as the local (inside a directory) or global (everywhere) Python version you can use:
```
pyenv local 3.9.8
pyenv global 3.9.8
```


Run in terminal within your working directory to set up:
```
pyenv local 3.9.8
python -m venv .venv
source .venv/bin/activate
```

And if you have requirements to install
```
pip install -r requirements.txt
```

Make a requirement.txt file based on installed packages
```
# shows list of packages
pip freeze   
# writes list to file 
pip freeze > requirements.txt     
```
