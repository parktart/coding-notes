# Bash Scripting

example file:

```bash
#!/bin/bash

your code here


# remember to give executable rights to the owner (user)
# with command "$ chmod u=rwx script-name.sh"

# the user who owns the file (u)
# other users in the file's group (g)
# other users not in the file's group (o)
# or all of the above (a)
```



scripting how to:

```bash
# the fist line is called the shebang
# it points to the program, on your computer, that should be used to execute the script
# in our case, it will almost always be bash, as..

#!/bin/bash

your code here


# you actually don't need the shebang because we can run the script
# from the command line with "$ bash script-name.sh"

# but this requires the user to know which shell this script was written for

# it is better practice to include the shebang and also give some executable rights
# which will allow users to run the script with simply "$ ./script-name.sh"

# use command "$ chmod u=rwx script-name.sh"
# to give executable rights to the file owner

# the user who owns the file (u)
# other users in the file's group (g)
# other users not in the file's group (o)
# or all of the above (a)
```

