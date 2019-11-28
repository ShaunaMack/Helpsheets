# Bash

### What is bash?
> Bash is the programming language that is used by our unix shells. Every time we echo/touch/cat we are using the bash language

### Automation is progress
> If we can write a ruby script to automate ruby commands, can we write a bash script to automate our bash commands

# YES!

That is a bash script and it starts with line of code called the Shebang. It must be on the very first line.

```bash
  #!/bin/bash
```

This is how the computer knows you are executing a bash program.

### What can we do?

Everything that we can do in other programming languages like loops, ifs, functions we can do in our bash script.

We can also execute the same commands we use in the terminal line.

``` bash
  #!/bin/bash
  echo "Hello World"
  mkdir "new-folder"
  
  # This command doesn't work and requires additional config
  # For ease of understanding let's assume that it does work
  cd "new-folder"
  echo "I'm in new-folder now!"
```

### How do we run it?
We can run a bash script by executing it in our command line.

But first we need to grant the correct permission to the file so that we ***can*** execute it.

``` bash
  chmod 775 my_script.sh  
```

Now we can execute it like a regular file.

``` bash
  ./my_script.sh
```

### Using Variables

We set variables similarly to how we do in ruby.We only need to omit the white space around the equals sign.
``` bash
  first="Hello"
  second="World"
```

To use these variables, we add a $ before it.

``` bash
echo $first $second
 # outputs Hello World
```

These are variables that we have defined in our code manually. We also have access to system variables that are already available for us to use.

These include the name of the user, the arguments passed in the command line, a randomly generated number, and many more. 

***Research Bash Variables for more information***

### Input

We can capture user inputs and store it in a variable. It is different to how we do in ruby.

``` bash
 echo "What's your name?"
 read username
 echo "Hello " $username
```

### Examples

Mixing multiple git commands into a one-liner
``` bash
  #!/bin/bash
  current_branch={"im not going to give you the solution"}

  git add -A
  git commit -m $1
  git checkout 'master'
  git merge current_branch
  git push origin master
```
Then running command

```bash
  ./git-shortcut.sh "my commit message"
```

#### Link to powerpoint
https://docs.google.com/presentation/d/16UNkfnADRalE0mYiyOvs0x4kAz6S4IRT3DOkF5cKYcI/edit?usp=sharing




