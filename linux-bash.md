
# Bash scripting

### Command Substitution
 - by default, alias is not expanded in sub-shell in bash script, add the command:
 ```
 shopt -s expand_aliases
 ```
 
### Exit status
 - by default, shell script will run through even there is an error in the middle
 - command show the last command exit status, 0 means success and non-zero values mean fail:
  ```
  echo $? 
  ```
