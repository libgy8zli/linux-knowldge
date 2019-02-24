
# Bash scripting

### Command Substitution
 - by default, alias is not expanded in sub-shell in bash script, add the command:
 ```
 shopt -s expand_aliases
 ```
 
### Exit status
 - by default, shell script will run through even there is an error in the middle, but this can be changed:
  ```
  # this command means exit shell if there is an error 
  set -e 
  ``` 
  
 - command show the last command exit status, 0 means success and non-zero values mean fail:
  ```
  echo $? 
  ```
### Arithmetic Operations
  - use "expr":
  ```
  expr 5 + 2
  ```
  - escape special character
  ```
  expr \(2 + 2 \) \* 4  #  result: 16
  ```
  
### Global and Local Environment Variables
  - printenv or env: show all or part of environment
  - set: show all environment to current session
   
