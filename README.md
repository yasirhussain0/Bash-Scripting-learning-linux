# Bash Scripting
# learning-linux 
# Basic'a of bash Scripting you need to know all the notes are made by me my own notes if you find any query you can contact me
# currently I'm busy with some university stuff i will update this very soon
# Intro to bash Scripting 
To check which shell you're in 
 1) echo $SHELL
To switch b/w shell like want to go into bash from zsh 
Write : which Bash
/usr/bin/bash

Q what actually is bash Scrripting ?
ans bash is a type of shell that makes it possible to run commands on Linux

What are the shell scripts

A shell script is a computer program designed to run within the shell (in this case, bash). Every shell has its own scripting language and, since bash is the default shell with Linux, most development and admin teams use the bash scripting language.

With these scripts, you can do almost anything. And like Python, they’re fairly easy to learn and don’t require a compiler to use

How to create a bash
#!/bin/bash

Create a new file with the command 
nano date.sh

now we will fomat the date to use our 
firmatted_date=$(date +%m_%d_%y-%H.%M.%S)
or 
echo "the date and time is " $formatted_date

to save the file 
sudo chmod u+x date.sh

Why we need bash Script ?
because if you have zero experience with the programing language still you can write in bash any thing like non-GUI based applicati0on

Advantages of bash Scripting

*simple to create
*can run multiple commands easily
*interactive debugging 
*portable
*time-saving
*cost-effective
*can be autoomated
*installed on nearly all linux OS

# Disadvantages of bashn Scripting

*not nearly as fast as standard program
*limited usability
*launches a new process for every shell command executed.

# lec2 
./Script.sh
Lec 2

to create a file 
nano Script.sh
to change permissions of file
chmod +x Script.sh
 
pta kasy chally ga ki yai bash hai ya nhi
nano Script.sh
/*ls
pwd*/

to write bash Script
#!/bash/bash  /*shebang*/
echo "Yasir is batman"
echo "My present working directory is "
pwd

# LEC3

myname="yasir"
echo "Yasir is here"
to print conext of file
echo $myname
output:yasir

ls="yasir is "
ls
it still works
now
echo $ls
yasir is

exit
new terminal 
echo $ls 
null
why ist not giving in new 
wipped out to save that 
#!/bin/bash
myname="yasir"
myage="21"

echo "hello my is $myname."
echo "I'm $myage years old."
exit
new teminal 
./script.sh
hello my name is yasir 
I'm 21 years old
wow now saved
how do variable help us

#!/bin/bash
word="good"
echo "linux is @word " 
echo "yasir is @word"
./script.sh
linux is good
yasir is good 

by this you can save time by doing that osky


files=$(ls)
echo $ls

date command
nano date.sh
#!/bin/bash
now="date"

echo "date is"

#!/bin/bash
name="yasir chandio"
now=$(date)
echo "hello $name"
echo "The system time and date is:"
echo $now
echo "Your username is: $USER"
./script.sh

to check which enviromental varialbles you have 
...>  env  <...

# <.............LEC4................>

AGENDA:Basic Maths Functions

In other programing languages we add two number like in java , c , c ++ ,python =30+10=40
But here is twist Yasir In bash you do not add like this you do is Simply

expr 30 + 10 note:space is imporant
40
expr 30 - 10
expr 30 / 10
But multiplication has a different way
expr 300 \* 4
now using variables  with maths 

mynum=100
echo $mynum1
or 
expr $mynum1 +50


# <.........LEC5..........>

# AGENDA=IF Statements

#! /bin/bash
 mynum=200
//note -eq=equals to , ne = not equal , -gt =greater than ,  to both are comparison operators 
if[ $mynum -eq 200] also check with if[! $mynum -eq 200]
then
echo "Statement is true "
fi
else
echo "not true statement"
fi
done

Now Combining two if statements
Tip if you want to be good at programing do one thing minimize code as much as you can boy 

#! /bin/bash
//to check presence of file on file system 

if[-f(is for file check) /myfile]
then 
echo "the file exists"
else
echo "the file does not exist"
fi

ans not exist
create a file 
here is command0 named "which" use this command wether or not an application or Binarry command is present on the file or not 

which htop
not install htop install it Yasir
by bash scripting you can install it 
how we will utilize this in command

#! /bin/bash

command=/usr/bin/htop
if[-f $command]
then echo "" $command is available, lets run it "
else
echo "$command is not available, installing it "
sudo apt update && sudo apt install -y(is yes command okay) htop
fi
$command

lets make it more simpler by changing some values

command=htop

if command -v $command

sudo apt update && sudo apt install -y $command
try them to change above okay

man test (all information abt test commands )


# <................LEC6.................>
# Agenda: Exit Codes

Q how do we determine success or failure in bash ?
so here is concept of (Exit codes) weather the command we entered is Successfully executed or not 

ls -l /etc (to check dir)

how does bash represents success or failure?
...>bash provides us special variable that contains (Exit Codes)

echo  $?
(note if it's giving us 0 means the command was successful but if its giving any random number 1,2 etc it means command has failed)

Q: but why do we need to know its executed or not like: it's obvious something fails or if we get error message.

..> well when we write scripts we write them such that they can run by themselves without us needing to watch them normally scripts
Example: a backup script that kicks off at midnight every night in that case we will not wake up every night to make sure script is running or not so basically check for exit code 
we could check for non-zero exit codes DYS(do your self further research)

here is script example to utilize an exit codes

nano script.sh
#! /bin/bash
package=htop
sudo apt install $package
echo "the exit code for the package install is: $?"
done 
sudo apt remove htop

note after running this command in the end you will receive
(The e=exit code for the package install is : 0(if zero command has running successfully))

on other hand if we enter the command totally different 
EX]#! bin/bash
package =nodeknfjfn(this ting doesn't exist if we run)
we will get(The e=exit code for the package install is : 100(didn't worked ))

here why exit codes are good thing we will know 
#! /bin/bash
package=htop
sudo apt install $package
if[$? -eq 0]
echo "the installation of $package was successful."
echo "the new command is available here"
which $package
else
echo "$package failed to install."
fi

To create 
#! /bin/bash
package=htop
sudo apt install $package >> package_install_endresult.log
if[$? -eq 0]
echo "the installation of $package was successful."
echo "the new command is available here"
which $package
else
echo "$package failed to install." >> package_install_endresult.log
fi
save and run 
okay command is successful not check
ls 
cat package_install_endresult.log

checking for the existing directory here new script

nano script1.sh
#! /bin/bash
directory=/etc

if[ -d $directory ]
echo `"The directory $directory exists."
else 
echo "the directory $directory doesn't exists"
fi
echo "the exit code for this script is $?"

important here this will show that directory exists will run successfully but 
ls -l by doing this it will sh0w us dir but it doesn't exists heeeeeeennnnn how ?
lets understand 


#! /bin/bash
directory=/hbhnotgcf

if[ -d $directory ]
echo `"The directory $directory exists."
else 
echo "the directory $directory doesn't exists"
fi
echo "the exit code for this script is $?"

output : what its showing 0 zero means success but this random dir hbhnotegcf doesn't exist how ?
lets find out error
#! /bin/bash
directory=/etc

if[ -d $directory ]
echo `"The directory $directory exists."
else 
echo "the directory $directory doesn't exists"
fi
echo "the exit code for this script is $?"

ans actually here problem is with exit code look its on the last line of code Yasir actually its running in the end 
this is why its giving 0 success so always make sure your exit code should be running on the appropriate time like right timing to use it okay

ex
echo "hello world"
exit 1 
echo $? 
hello world 
echo $?
1
but its showing other than zero what we can control the exit code last line never runs as we have discussed above

#! /bin/bash
directory=/etc

if[ -d $directory ]
echo `"The directory $directory exists."
exit 0
else 
echo "the directory $directory doesn't exists"
exit 1
fi
echo "the exit code for this script is $?"
echo "you didn't see that statement"
echo "You didn't see this one either"

so exit codes gives us the more control to our scripts we can control exit codes 




 
