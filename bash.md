# Bash shell

[toc]

### Introduction

Try to customize your own**Shell environment** to ease your way of working, e.g. adding a new directory to the `$PATH`, or changing the look of the **shell prompt** (PS1). These configurations can go into either `.bashrc` or `bashrc_profile` depending on the if an `interactive login` or `non-login` shell is being invoked. The following lines of codes can be used to check this:



You can detect if you are in an interactive or non-interactive shell with **(bash only)**

```
[[ $- == *i* ]] && echo 'Interactive' || echo 'not-interactive' 
```



To detect if you are in a login shell or not you have to use the **shopt** command.

```
shopt -q login_shell && echo 'login' || echo 'not-login'
```



#### Interactive Login vs Non-Login shell

A shell can be **interactive** (reads and writes to a user's terminal) or **non-interactive** (executes a script). And an **interactive shell** can be **login** or **non-Login**. Here we focus on **interactive login/non-login shell**. For **non-interactive shell**, study when you need.



When an **interactive login shell** invoked, Bash reads and executes commands from a set of **startup files** in `/~/.bash_profile`, `~/.bash_login`, and `~/.profile` files, **in the listed order!** And executes commands from the **first readable file found!**

Typically, `~/.bash_profile` contains lines below that source the `.bashrc` file:

```
if [ -f ~/.bashrc ]; then
	. ~/.bashrc
fi
```

This means **an interactive login shell** will always execute the commands in **both** `~/.bash_profile` and `~/.bashrc` files. (limited to **login shell only!**)



When an **interactive non-login shell** invoked, Bash reads and executes commands from `~/.bashrc`, if that file exists and is readable. (**no limitations! Always executed!**)





##### ==We can make a summary for the above:==

`~/.bashrc` files will be executed **no matter what** or whether you are invoking the**login or non-login** next time. If you want your commands always to be executed, then put it in `~/.bashrc`. 

Otherwise put it in `~/.bash_profile` if you **want this newly added commands to be executed for this time only!**, and **you do not care if you might have non-login shell invoked next time** where only `~/.bashrc` file will be executed. 