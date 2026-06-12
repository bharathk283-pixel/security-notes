Linux Basics
pwd

Purpose:
Print current working directory.

Example Output:
ubuntu@security-lab:~$ pwd
/home/ubuntu

##########
Command: whoami
Shows current user

Example output:
ubuntu@security-lab:~$ whoami
ubuntu

##########
Command: hostname
Shows machine name.

Example output:
ubuntu@security-lab:~$ hostname
security-lab

##########
Command: ls

Used to list all files and directories

__________
Options
ls -t -> Lists last edited file first

Example output:
ubuntu@security-lab:~/bharath_test$ ls -t
sample2.txt  sample1.txt

combine with head to view the number of files
Sample output:

ubuntu@security-lab:~/bharath_test$ ls -t | head -1
sample2.txt

__________
Command: ls -1
Display one file name in a line
Example output:

ubuntu@security-lab:~/bharath_test$ ls -1
sample1.txt
sample2.txt

__________
Command: ls -1