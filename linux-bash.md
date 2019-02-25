
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
   
### Shell Expansion
```
echo sh{ot,ort,oot}
shot short shoot # result
echo ~+ # echo out current dir
echo "${VARNAME:=value}" # set and echo variable 
echo "$[ 2 * 2 ]" # result is 4
```

### Interactive scripting
```
echo "Your first name:"
read FIRSTNAME
```

### Passing Variables to Scripts at the command line
 - var_pass.sh:  
   ```
   #!/bin/bash
   echo "This variable is passed to the script at run time: $1"
   ```
 - command line:
  ```
  var_pass.sh HelloWorld
  This variable is passed to the script at run time: HelloWorld # expected result
  ```
### File descriptor
  [File descriptor](https://www.computerhope.com/jargon/f/file-descriptor.html)
```
echo "Enter a file name to read:
read FILE

exec 5<>$FILE # pick a number ge than 3 

while read -r SUPERHERO; do
  echo "Superhero Name: $SUPERHERO"
done <&5

echo "File was Read on: `date`" >&5

exec 5>&-  # close file descriptor
```
