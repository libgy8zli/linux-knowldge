
# Bash scripting

### Command Substitution
 - by default, alias is not expanded in sub-shell in bash script, add the command:
 ```
 shopt -s expand_aliases
 ```
 
### Exit status
 - command show the last command exit status: 
  ```
  echo $? 
  ```
