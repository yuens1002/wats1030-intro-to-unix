# *nix Scavenger Hunt

Complete the following challenges using the command-line interface on your favorite
Unix or Linux operating system. You are welcome and encouraged to consult any
additional documentation online or in books.

Please add your answers/responses/text pastes to the document after each prompt.

Note: For some of the challenges you will need to reference files included with
this repository, so you will need to fork the repo into your own Github account
and then clone it to your development environment.

## The Challenges

### Navigating the Filesystem

* Get an idea of where you are in the operating system. Use the `pwd` command to find your "path to working directory"--your current location in the filesystem of your devbox. *Paste the output of the `pwd` command here:*

/Users/sunny

* Discover more about this filesystem. Use `ls` (the "list" command)to see what is in this directory. *What directories and files do you see when you run `ls`?*

Applications			Seattle CUPS
Creative Cloud Files		drink builder
Desktop				myApp
Documents			wats1010-css-zen-garden
Downloads			wats1010-product-page
Google Drive			wats1010-product-page_old
Hover				wats1020-arrays-functions
Library				wats1020-fizzbuzz
Movies				wats1030-intro-to-unix
Music				yuens.github.io
Pictures			yuens1002
Public				yuens1002.github.io

* You can use *options* to modify how a command runs. Try using `ls -alh` to see the contents of your current directory. *How are the results different when you use the `-alh` options?*

there are a whole lot more info given per entry and files that i didn't see before

* The `man` ("manual") command tells you more about how any given command works. (*WARNING:* CodeAnywhere does not support the man command. You can click the following link to complete this task: http://linux.die.net/man/)Run `man` to see instructions about how to use `man`. Then use `man` to learn what the `a`, `l`, and `h` options mean when used with the `ls` command. *Write down what those options do?*

-a      Include directory entries whose names begin with a dot (.)

-l      If the -l option is given, the following information is displayed for
        each file: file mode, number of links, owner name, group name, number of
        bytes in the file, abbreviated month, day-of-month file was last modi-
        fied, hour file last modified, minute file last modified, and the path-
        name

-h      When used with the -l option, use unit suffixes: Byte, Kilobyte,
             Megabyte, Gigabyte, Terabyte and Petabyte in order to reduce the
             number of digits to three or less using base 2 for sizes.

* Commands can also take *arguments*, which are usually the names of files or locations that you want the command to work with. Try running `ls /` to see what files are in the *root* directory of the filesystem. *What files and directories do you see listed?*

Applications			etc
Library				home
Network				installer.failurerequests
System				net
Users				private
Volumes				sbin
bin				tmp
cores				usr
dev				var

* A Unix filesystem has a few special shortcuts to refer to specific locations. `/` indicates the *root* of the filesystem, meaning the top-most directory in the filesystem hierarchy. Use the `cd` ("change directory") command to move to the root directory. (Hint: Use `man` to look up the `cd` command if you have any issues) *Then run `pwd` and paste the output here:*

/  * didn't get anything useful by man cd, wonder why.  I'm on a MAC OS X *

* Another special shortcut in Unix is the `~` location. This indicates the *user root* directory, meaning the top-most directory in the hierarchy that comes below your user account. Use `cd` to move to `~`. *Run `pwd` and paste the response here:*

/Users/sunny

* Change directory into the `challenge_files` directory. Use `ls` to find only the files with a `.demo` pattern. *How many files do you find?*

2015_special_stuff.demo		
scooter-double-mamba.demo
cloaked-wookie.demo

* Use the `cd` command to move "up" one directory. *Where are you in the filesystem now?*

/Users/sunny/wats1030-intro-to-unix

* Press the up arrow on your keyboard. *What just happened?*

last command populated

* Press the up arrow a few more times. *What do you see?*

scrolling of all commands entered

* Run the `history` command. *What do you see?*

that's awesome, see a log of all commands ran in the terminal

### Observing the System

* Discover what account you are logged into using the `whoami` command. *What username are you currently using?*

sunny

* Discover who else is on your system with the `who` command. *Are any other users using your system? If so, list them here:*

sunny    console  Jan 12 21:20 
sunny    ttys000  Jan 15 07:31

* How long has your system been running? Use `uptime` to see, and *paste the result here:*

8:02  up 2 days, 12:23, 2 users, load averages: 1.56 1.83 2.10

* Run `ps aux` and review the results. (Hint: Use `man` to learn more about the `ps` command and options.) *How do you interpret what you see here?*

list of processese done by everyone and the os itself, including processes w/o control of a terminal

* Run `top` and review the results. (Hint: You may need to use `ctrl-c` to get out of this app.) *How do you interpret what you see here?*

list of resources, processes and allication.  realtime usage stats.   

### Finding and Viewing Files

* Make sure you are in the `challenge_files` directory. Use the `*` wildcard to find all the files that have the word "credit" in the filename. *How many files did you find?*

credit_cards.txt	
credit_cards2.txt

* Use the `more` command to view one of the `credit_cards` files you just discovered. (Hint: Type `q` to quit viewing the file. Press the `spacebar` to page down. Use your keyboard arrows to move up/down.) *What is the date in the file you have viewed?*

on the credit_cards.txt 
Last updated: 01-15-2015

* Use the `find` command to search for files more effectively. Search the sub-directories under `challenge_files` to find the location of the file named `modi_laboriosam.txt`. *Where is that file located?*

find . -name modi*

./tmp/modi_laboriosam.txt

* Use the `grep` command to search for text within a file. Use `grep` on all the `.user` files in `challenge_files` to find which files contain "WA" (the abbreviation for Washington state). *How many files did you find?*

grep -r --include="*.user" "WA" .

./Britt-Erdman.user:O'Harachester, WA 37261
./Lissie-Strosin.user:Jewessfurt, WA 00816-7241

* Use the `-r` option of `grep` to *recursively* find the text "Waldo" hidden in a file somewhere under the `challenge_files` directory. *Paste the result showing the file and line where the word "Waldo" shows up.*

grep -ri "Waldo" .

./serial-numbers/eaque_molestiae.txt:Ut est maiores quia autem. Nisi modi Waldo sed corporis sit explicabo ut est. Et est placeat ea sunt sunt consectetur sunt incidunt. Explicabo vel esse blanditiis dolorem culpa non quia.

### Pipes and Connecting Commands

* Sometimes it's useful to output the results of a command to a text file for further analysis, reference, or processing. Try running `ls > files.txt`. Notice that the file `files.txt` was created. View that file using `more`. *What do you see in the `files.txt` file?*

list of all file names in the user directory

* Notice that if you run `ls -alh` in the `challenge_files` directory, the files scroll by very quickly. Sometimes it would be better to get the results in a paginated format. Try running `ls -alh | more`. *Describe what you see when you run `ls -alh | more`.*

the output stopped at the bottom of the page, allows use of the keyboard to scroll 

* Earlier, when you viewed the list of active processes on your devbox using `ps aux`, the list was probably really long. You can make this list more manageable by using the pipe (`|`) to filter the results of `ps` using `grep`. Run `ps aux | grep <your_username>` to see what processes are running for your specific user. *Paste the list of processes that reference your username here:*

i got a bunch of junk by using the -aux option, when i entered just a 

 4999 ttys000    0:00.02 login -pf sunny
 5026 ttys000    0:00.01 grep sunny