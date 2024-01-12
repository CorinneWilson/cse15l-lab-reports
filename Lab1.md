# Lab 1

---
## Using `cd` Command

- No arguments
 
  ![Image](cd_None.png)
  - The working directory was `/home/lecture1` when this command was run.
  - As shown above, this command produces no output. This is because to properly use the `cd` command, you must follow it with a directory as an argument. Having no argument means there is no directory to change to, thus no output is produced.
  - No error occurred.

- A path to a *directory* as an argument

  ![Image](cd_Directory.png)
  - The working directory was `/home` when this command was run.
  - As shown above, this command produces no ouput, but does change the prompt and the working directory. Using the directory to the `lecture1` folder as an argument for the `cd` command changes the working directory from `/home` to `/home/lecture1`. In addition, the prompt changed to `[user@sahara ~/lecture1]$` to remind us of the terminals new directory.
  - No error occurred.

- A path to a *file* as an argument
  
  ![Image](cd_File.png)
  - The working directory was `/home/lecture1` when this command was run.
  - As shown above, this command produces `bash: cd: messages/en-us.txt: Not a directory` as an output. `en-us.txt` is a file within the `messages` folder within the `lecture1` folder. Thus, this output is tells us that `messages/en-us.txt` is not a path to a directory, but rather a path to a file. Thus using it as an argument for the `cd` command will not work.
  - This output is an error 

  
---
## Using `ls` Command

no arguments
a path to a *directory* as an argument

a path to a *file* as an argument

---
## Using `cat` Command

no arguments

a path to a *directory* as an argument

a path to a *file* as an argument
