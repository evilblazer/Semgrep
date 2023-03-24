Dummy instructions

1. Install Semgrep
# For macOS
$ brew install semgrep

2. Check if semgrep is installed
semgrep --version

3. Run recommended semgrep rules
If it is on a different directory, you can configure the path by specifying PATH/TO/SRC, 
semgrep --config=auto PATH/TO/SRC
The other way is to change to the project directory and then run the following command,
semgrep --config=auto


