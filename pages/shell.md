# Instruction on using shell script to run code from different programs:

   1.  Use any plain text editor to create a file with the following content and save as `filename.sh`:

```
#!/bin/bash

#The first line of comment has to be there, so you can add any comments

#if you want to display some messages in the console

echo "something you want the command prompt to display”

#if you want to run stata code

stata -b do do-file-name-that-you-want-to-run.do

#if you want to run R code

Rscript r-code-file-name-that-you-want-to-run.R
```

   2. Put it in the same directory as all your code

   3. `cd` to that directory, type in command prompt `sh filename.sh`, and hit Enter. 
   The script should start running. Using `echo` to display some messages from time to time is recommended so that you know your script is running properly.

   4. If an error with something like not having privilege or access right appears, use the command:

`chmod +x script_name.sh`

and repeat step 3.
