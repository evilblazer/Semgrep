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

4. Read custom rule examples and pattern examples and pattern syntax
https://semgrep.dev/docs/writing-rules/pattern-examples/

5. Read some of the existing rules in the semgrep-rules 
(For example, this is the java rules) 
https://github.com/returntocorp/semgrep-rules/tree/develop/java/lang/security/audit

6. Test rules in semgrep playground
https://semgrep.dev/playground/s/clintgibler:no-exec
