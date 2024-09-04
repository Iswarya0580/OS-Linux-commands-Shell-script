# OS-Linux-commands-Shell-scripting
Operating systems Lab exercise
# Linux commands-Shell scripting
Linux commands-Shell scripting
# Developed By:Iswarya P
# Register no: 212223230082 
# AIM:
To practice Linux Commands and Shell Scripting

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Execute the following commands

### Step 3:

Testing the commands for the desired output. 

# COMMANDS:
### Create the following files file1, file2 as follows:
cat > file1
```
chanchal singhvi
c.k. shukla
s.n. dasgupta
sumit chakrobarty
^d
```
cat > file2
```
anil aggarwal
barun sengupta
c.k. shukla
lalit chowdury
s.n. dasgupta
^d
```
### Display the content of the files
cat < file1
## OUTPUT
```
chanchal singhvi
c.k. shukla
s.n. dasgupta
sumit chakrobarty
```

cat < file2
## OUTPUT
```
anil aggarwal
barun sengupta
c.k. shukla
lalit chowdury
s.n. dasgupta
```
# Comparing Files
cmp file1 file2
## OUTPUT
file1 file2 differ: char 1, line 1

comm file1 file2
## OUTPUT
```
        anil aggarwal
        barun sengupta
        c.k. shukla
chanchal singhvi
c.k. shukla
        lalit chowdury
                s.n. dasgupta
sumit chakrobarty
```
 
diff file1 file2
## OUTPUT
```
--- file1
+++ file2
@@ -1,4 +1,5 @@
-chanchal singhvi
+anil aggarwal
+barun sengupta
 c.k. shukla
+lalit chowdury
 s.n. dasgupta
-sumit chakrobarty
```

#Filters

### Create the following files file11, file22 as follows:

cat > file11
```
Hello world
This is my world
^d
```
cat > file22
```
1001 | Ram | 10000 | HR
1002 | tom |  5000 | Admin
1003 | Joe |  7000 | Developer
^d
```


cut -c1-3 file11
## OUTPUT

Hel
Thi


cut -d "|" -f 1 file22
## OUTPUT

1001
1002
1003

cut -d "|" -f 2 file22
## OUTPUT
Ram
tom
Joe

cat < newfile 
```
Hello world
hello world
^d
````
cat > newfile 
Hello world
hello world
 
grep Hello newfile 
## OUTPUT
Hello world


grep hello newfile 
## OUTPUT
Hello world



grep -v hello newfile 
## OUTPUT
Hello world


cat newfile | grep -i "hello"
## OUTPUT

Hello world
hello world


cat newfile | grep -i -c "hello"
## OUTPUT

2


grep -R ubuntu /etc
## OUTPUT

recursion

grep -w -n world newfile   
## OUTPUT

1:Hello world
2:hello world

cat < newfile 
```
Hello world
hello world
Linux is world number 1
Unix is predecessor
Linux is best in this World
^d
```

cat > newfile
```
Hello world
hello world
Linux is world number 1
Unix is predecessor
Linux is best in this World
^d
 ```
egrep -w 'Hello|hello' newfile 
## OUTPUT

Hello world
hello world

egrep -w '(H|h)ello' newfile 
## OUTPUT
Hello world
hello world


egrep -w '(H|h)ell[a-z]' newfile 
## OUTPUT

Hello world
hello world


egrep '(^hello)' newfile 
## OUTPUT
hello world


egrep '(world$)' newfile 
## OUTPUT

hello world
hello world

egrep '(World$)' newfile 
## OUTPUT
Linux is best in the World

egrep '((W|w)orld$)' newfile 
## OUTPUT
Hello world
hello world
Linux is best in this World


egrep '[1-9]' newfile 
## OUTPUT
Linux is world number 1


egrep 'Linux.*world' newfile 
## OUTPUT
Linux is best in this World

egrep 'Linux.*World' newfile 
## OUTPUT
Linux is best in this World

egrep l{2} newfile
## OUTPUT

Hello world
hello world

egrep 's{1,2}' newfile
## OUTPUT 
Unix is predecessor
Linux is best in this World

cat > file23
```
1001 | Ram | 10000 | HR
1001 | Ram | 10000 | HR
1002 | tom |  5000 | Admin
1003 | Joe |  7000 | Developer
1005 | Sam |  5000 | HR
1004 | Sit |  7000 | Dev
1003 | Joe |  7000 | Developer
1001 | Ram | 10000 | HR
^d
```


sed -n -e '3p' file23
## OUTPUT
1002 | tom | 5000 | Admin


sed -n -e '$p' file23
## OUTPUT
1001 | Ram | 10000 | HR


sed  -e 's/Ram/Sita/' file23
## OUTPUT
```
1001 | Sita | 10000 | HR
1001 | Sita | 10000 | HR
1002 | tom | 5000 | Admin
1003 | Joe | 7000 | Developer
1005 | Sam | 5000 | HR
1004 | Sit | 7000 | Dev
1003 | Joe | 7000 | Developer
1001 | Sita | 10000 | HR
```

sed  -e '2s/Ram/Sita/' file23
## OUTPUT
```
1001 | Ram | 10000 | HR
1001 | Sita | 10000 | HR
1002 | tom | 5000 | Admin
1003 | Joe | 7000 | Developer
1005 | Sam | 5000 | HR
1004 | Sit | 7000 | Dev
1003 | Joe | 7000 | Developer
1001 | Ram | 10000 | HR
```

sed  '/tom/s/5000/6000/' file23
## OUTPUT
```
1001 | Ram | 10000 | HR
1001 | Ram | 10000 | HR
1002 | tom | 6000 | Admin
1003 | Joe | 7000 | Developer
1005 | Sam | 5000 | HR
1004 | Sit | 7000 | Dev
1003 | Joe | 7000 | Developer
1001 | Ram | 10000 | HR
```

sed -n -e '1,5p' file23
## OUTPUT
```
1001 | Ram | 10000 | HR
1001 | Ram | 10000 | HR
1002 | tom | 5000 | Admin
1003 | Joe | 7000 | Developer
1005 | Sam | 5000 | HR
```


sed -n -e '2,/Joe/p' file23
## OUTPUT
```
1001 | Ram | 10000 | HR
1002 | tom | 5000 | Admin
1003 | Joe | 7000 | Developer
```



sed -n -e '/tom/,/Joe/p' file23
## OUTPUT
```
1002 | tom | 5000 | Admin
1003 | Joe | 7000 | Developer
```


seq 10 
## OUTPUT
```
1
2
3
4
5
6
7
8
9
10
```


seq 10 | sed -n '4,6p'
## OUTPUT

```
4
5
6
```

seq 10 | sed -n '2,~4p'
## OUTPUT
```
2
3
4
```


seq 3 | sed '2a hello'
## OUTPUT
```
1
2
hello
3
```


seq 2 | sed '2i hello'
## OUTPUT
```
1
hello
2
```

seq 10 | sed '2,9c hello'
## OUTPUT
```
1
hello
10
```

sed -n '2,4{s/^/$/;p}' file23
## OUTPUT
```
$1001 | Ram | 10000 | HR
$1002 | tom | 5000 | Admin
$1003 | Joe | 7000 | Developer
```


sed -n '2,4{s/$/*/;p}' file23
```
1001 | Ram | 10000 | HR
1002 | tom |  5000 | Admin
1003 | Joe |  7000 | Developer
1005 | Sam |  5000 | HR
1004 | Sit |  7000 | Dev
```

#Sorting File content
cat > file21
```
1001 | Ram | 10000 | HR
1002 | tom |  5000 | Admin
1003 | Joe |  7000 | Developer
1005 | Sam |  5000 | HR
1004 | Sit |  7000 | Dev
``` 
sort file21
## OUTPUT


cat > file22
```
1001 | Ram | 10000 | HR
1001 | Ram | 10000 | HR
1002 | tom |  5000 | Admin
1003 | Joe |  7000 | Developer
1005 | Sam |  5000 | HR
1004 | Sit |  7000 | Dev
``` 
uniq file22
## OUTPUT
```
1001 | Ram | 10000 | HR
1002 | tom |  5000 | Admin
1003 | Joe |  7000 | Developer
1005 | Sam |  5000 | HR
1004 | Sit |  7000 | Dev
```
#Using tr command

cat file22 | tr [:lower:] [:upper:]
 ## OUTPUT
```
1001 | RAM | 10000 | HR
1001 | RAM | 10000 | HR
1002 | TOM |  5000 | ADMIN
1003 | JOE |  7000 | DEVELOPER
1005 | SAM |  5000 | HR
1004 | SIT |  7000 | DEV
```
cat > urllist.txt
```
www. yahoo. com
www. google. com
www. mrcet.... com
^d
 ```
cat < urllist.txt
```
www. yahoo. com
www. google. com
www. mrcet.... com
 ```
cat urllist.txt | tr -d ' '
 ## OUTPUT
```
www.yahoo.com
www.google.com
www.mrcet....com
^d
```
 
cat urllist.txt | tr -d ' ' | tr -s '.'
## OUTPUT
```
www.yahoo.com
www.google.com
www.mrcet.com
^d
```


#Backup commands
tar -cvf backup.tar *
## OUTPUT
```
bench.py
file21
file22
hello.c
hello.js
readme.txt
urllist.txt
```

mkdir backupdir
 
mv backup.tar backupdir
 
tar -tvf backup.tar
## OUTPUT


tar -xvf backup.tar
## OUTPUT

gzip backup.tar

ls .gz
## OUTPUT
 
gunzip backup.tar.gz
## OUTPUT

 
# Shell Script
```
echo '#!/bin/sh' > my-script.sh
echo 'echo Hello World‘; exit 0 >> my-script.sh
```
chmod 755 my-script.sh
./my-script.sh
## OUTPUT
```
hello in this world
i ccant stop
for this non stop movement
stop
```
 
cat << stop > herecheck.txt
```
hello in this world
i cant stop
for this non stop movement
stop
```

cat herecheck.txt
## OUTPUT
```
hello in this world
i cant stop
for this non stop movement
```

cat < scriptest.sh 
```bash
\#!/bin/sh
echo “File name is $0 ”
echo "File name is " `basename $0`
echo “First arg. is ” $1
echo “Second arg. is ” $2
echo “Third arg. is ” $3
echo “Fourth arg. is ” $4
echo 'The $@ is ' $@
echo 'The $\# is ' $1#
echo 'The $$ is ' $$
ps
^d
 ```

cat scriptest.sh 
```bash
\#!/bin/sh
echo “File name is $0 ”
echo "File name is " `basename $0`
echo “First arg. is ” $1
echo “Second arg. is ” $2
echo “Third arg. is ” $3
echo “Fourth arg. is ” $4
echo 'The $@ is ' $@
echo 'The $\# is ' $\#
echo 'The $$ is ' $$
ps
```
 
chmod 777 scriptest.sh
 
./scriptest.sh 1 2 3

## OUTPUT
```
./scriptest.sh: line 1: #!/bin/sh: not found
“File name is ./scriptest.sh ”
File name is  scriptest.sh
“First arg. is ” 1
“Second arg. is ” 2
“Third arg. is ” 3
“Fourth arg. is ”
The $@ is  1 2 3
The $\# is  1#
The $$ is  200
PID   USER     TIME  COMMAND
    1 root      0:01 {init} /bin/sh /sbin/init
    2 root      0:00 [kthreadd]
    3 root      0:00 [kworker/0:0]
    4 root      0:00 [kworker/0:0H]
    5 root      0:00 [kworker/u2:0]
    6 root      0:00 [mm_percpu_wq]
    7 root      0:00 [ksoftirqd/0]
    8 root      0:00 [kdevtmpfs]
    9 root      0:00 [oom_reaper]
   10 root      0:00 [writeback]
   11 root      0:00 [kcompactd0]
   12 root      0:00 [crypto]
   13 root      0:00 [bioset]
   14 root      0:00 [kblockd]
   15 root      0:00 [kworker/0:1]
   16 root      0:00 [kswapd0]
   17 root      0:00 [bioset]
   34 root      0:00 [khvcd]
   35 root      0:00 [bioset]
   36 root      0:00 [bioset]
   37 root      0:00 [bioset]
   38 root      0:00 [bioset]
   39 root      0:00 [bioset]
   40 root      0:00 [bioset]
   41 root      0:00 [bioset]
   42 root      0:00 [bioset]
   55 root      0:00 settime -d /
   56 root      0:00 dhcpcd -q
   61 root      0:00 sh -l
   62 root      0:00 [kworker/u2:1]
  200 root      0:00 {busybox} ash ./scriptest.sh 1 2 3
  203 root      0:00 ps
```
 
ls file1
## OUTPUT
file1

echo $?
## OUTPUT 
./one
bash: ./one: Permission denied
 
echo $?
## OUTPUT 
 
abcd
 
echo $?
 ## OUTPUT
127

 
# mis-using string comparisons

cat < strcomp.sh 
```bash
\#!/bin/bash
val1=baseball
val2=hockey
if [ $val1 \> $val2 ]
then
echo "$val1 is greater than $val2"
else
echo "$val1 is less than $val2"
fi
^d
```

cat strcomp.sh 
```bash
\#!/bin/bash
val1=baseball
val2=hockey
if [ $val1 \> $val2 ]
then
echo "$val1 is greater than $val2"
else
echo "$val1 is less than $val2"
fi
```
##OUTPUT



chmod 755 strcomp.sh
 
./strcomp.sh 
## OUTPUT
You are the owner of the /etc/passwd file

# check file ownership
cat < psswdperm.sh 
```bash
\#!/bin/bash
if [ -O /etc/passwd ]
then
echo “You are the owner of the /etc/passwd file”
else
echo “Sorry, you are not the owner of the /etc/passwd file”
fi
^d
```

cat psswdperm.sh 
```bash
/#!/bin/bash
if [ -O /etc/passwd ]
then
echo “You are the owner of the /etc/passwd file”
else
echo “Sorry, you are not the owner of the /etc/passwd file”
fi
 ```
./psswdperm.sh
## OUTPUT
"/root The object exists, is it a file?"
"No,/root it is not a file!"
# check if with file location
cat>ifnested.sh 
```bash
\#!/bin/bash
if [ -e $HOME ]
then
echo “$HOME The object exists, is it a file?”
if [ -f $HOME ]
then
echo “Yes,$HOME it is a file!”
else
echo “No,$HOME it is not a file!”
if [ -f $HOME/.bash_history ]
then
echo “But $HOME/.bash_history is a file!”
fi
fi
else
echo “Sorry, the object does not exist”
fi
^d
```
cat ifnested.sh 
```
\#!/bin/bash
if [ -e $HOME ]
then
echo “$HOME The object exists, is it a file?”
if [ -f $HOME ]
then
echo “Yes,$HOME it is a file!”
else
echo “No,$HOME it is not a file!”
if [ -f $HOME/.bash_history ]
then
echo “But $HOME/.bash_history is a file!”
fi
fi
else
echo “Sorry, the object does not exist”
fi
```

./ifnested.sh 
## OUTPUT



“/home/sec The object exists, is it a file?”
“No,/home/sec it is not a file!”
“But /home/sec/.bash_history is a file!”


# using numeric test comparisons
cat > iftest.sh 
```bash
\#!/bin/bash
val1=10
val2=11
if [ $val1 -gt 5 ]
then
echo “The test value $val1 is greater than 5”
fi
if [ $val1 -eq $val2 ]
then
echo “The values are equal”
else
echo “The values are different”
fi
^d
```


cat iftest.sh 
```bash
\#!/bin/bash
val1=10
val2=11
if [ $val1 -gt 5 ]
then
echo “The test value $val1 is greater than 5”
fi
if [ $val1 -eq $val2 ]
then
echo “The values are equal”
else
echo “The values are different”
fi
```

$ chmod 755 iftest.sh
 
$ ./iftest.sh 
## OUTPUT
“The test value 10 is greater than 5”
“The values are different”

# check if a file
cat > ifnested.sh 
```bash
\#!/bin/bash
if [ -e $HOME ]
then
echo “$HOME The object exists, is it a file?”
if [ -f $HOME ]
then
echo “Yes,$HOME it is a file!”
else
echo “No,$HOME it is not a file!”
if [ -f $HOME/.bash_history ]
then
echo “But $HOME/.bash_history is a file!”
fi
fi
else
echo “Sorry, the object does not exist”
fi
^d
```

cat ifnested.sh 
```bash
\#!/bin/bash
if [ -e $HOME ]
then
echo “$HOME The object exists, is it a file?”
if [ -f $HOME ]
then
echo “Yes,$HOME it is a file!”
else
echo “No,$HOME it is not a file!”
if [ -f $HOME/.bash_history ]
then
echo “But $HOME/.bash_history is a file!”
fi
fi
else
echo “Sorry, the object does not exist”
fi
```

$ chmod 755 ifnested.sh
 
$ ./ifnested.sh 
## OUTPUT
“/home/sec The object exists, is it a file?”
“No,/home/sec it is not a file!”
“But /home/sec/.bash_history is a file!”

# looking for a possible value using elif
cat elifcheck.sh 
```bash
\#!/bin/bash
if [ $USER = Ram ]
then
echo "Welcome $USER"
echo "Please enjoy your visit"
elif [ $USER = Rahim ]
then
echo "Welcome $USER"
echo "Please enjoy your visit"
elif [ $USER = Robert ]
then
echo "Special testing account"
elif [ $USER = gganesh ]
then
echo "$USER, Do not forget to logout when you're done"
else
echo "Sorry, you are not allowed here"
fi
```

$ chmod 755 elifcheck.sh
 
$ ./elifcheck.sh 
## OUTPUT
./elifcheck.sh: line 1: #!/bin/bash: No such file or directory
Sorry, you are not allowed here


# testing compound comparisons
cat> ifcompound.sh 
```bash
\#!/bin/bash
if [ -d $HOME ] && [ -w $HOME ]
then
echo "The file exists and you can write to it"
else
echo "I cannot write to the file"
fi
```
$ chmod 755 ifcompound.sh
$ ./ifcompound.sh 
## OUTPUT
./ifcompound.sh: line 1: #!/bin/bash: No such file or directory
The file exists and you can write to it
# using the case command
cat >casecheck.sh 
```bash
case $USER in
Ram | Robert)
echo "Welcome, $USER"
echo "Please enjoy your visit";;
Rahim)
echo "Special testing account";;
gganesh)
echo "$USER, Do not forget to log off when you're done";;
*)
echo "Sorry, you are not allowed here";;
esac
```
$ chmod 755 casecheck.sh 
 
$ ./casecheck.sh 
## output
./elifcheck.sh: line 1: #!/bin/bash: No such file or directory
Sorry, you are not allowed here

cat > whiletest
```bash
#!/bin/bash
#while command test
var1=10
while [ $var1 -gt 0 ]
do
echo $var1
var1=$[ $var1 - 1 ]
done
```
$ chmod 755 whiletest.sh
 
$ ./whiletest.sh
 
 
cat untiltest.sh 
```bash
\#using the until command
var1=100
until [ $var1 -eq 0 ]
do
echo $var1
var1=$[ $var1 - 25 ]
done
``` 
$ chmod 755 untiltest.sh
 
 ## output
 ./untiltest.sh: line 1: #using: command not found
100
75
50
25

 
cat forin1.sh 
```bash
\#!/bin/bash
\#basic for command
for test in Alabama Alaska Arizona Arkansas California Colorado
do
echo The next state is $test
done
 ```
 
$ chmod 755 forin1.sh
 ## output
 ./forin1.sh: line 1: #!/bin/bash: No such file or directory
./forin1.sh: line 2: #basic: command not found
The next state is Alabama
The next state is Alaska
The next state is Arizona
The next state is Arkansas
The next state is California
The next state is Colorado

 
cat forin2.sh 
```bash
\#!/bin/bash
\# another example of how not to use the for command
for test in I don't know if this'll work
do
echo “word:$test”
done
 ```
 
$ chmod 755 forin2.sh
 
cat forin2.sh 
```bash
\#!/bin/bash
\# another example of how not to use the for command
for test in I don't know if this'll work
do
echo “word:$test”
done
```
$ chmod 755 forin2.sh
 
$ ./forin2.sh 
 
cat forin3.sh 
```bash
\#!/bin/bash
\# another example of how not to use the for command
for test in I don\'t know if "this'll" work
do
echo "word:$test"
done
```
$ ./forin3.sh 
 ## output
 “word:I”
“word:dont know if thisll”
“word:work”


cat forin1.sh 
```bash
#!/bin/bash
# basic for command
for test in Alabama Alaska Arizona Arkansas California Colorado
do
echo The next state is $test
done
```
$ chmod 755 forin1.sh

## OUTPUT
```
The next state is Alabama
The next state is Alaska
The next state is Arizona
The next state is Arkansas
The next state is California
The next state is Colorado
```

cat forinfile.sh 
```bash
#!/bin/bash
# reading values from a file
file="cities"
for state in `cat $file`
do
echo "Visit beautiful $file“
done
```
$ chmod 777 forinfile.sh
$ cat cities
Hyderabad
Alampur
Basara
Warangal
Adilabad
Bhadrachalam
Khammam

## OUTPUT
```
Visit beautiful cities
Visit beautiful cities
Visit beautiful cities
Visit beautiful cities
Visit beautiful cities
Visit beautiful cities
Visit beautiful cities
```

cat forctype.sh 
```bash
#!/bin/bash
# testing the C-style for loop
for (( i=1; i <= 5; i++ ))
do
echo "The value of i is $i"
done
````
$ chmod 755 forctype.sh
$ ./forctype.sh 
## OUTPUT

cat forctype1.sh 
```bash
#!/bin/bash
# multiple variables
for (( a=1, b=5; a <= 5; a++, b-- ))
do
echo "$a - $b"
done
```
$ chmod 755 forctype.sh
$ ./forctype1.sh 
## OUTPUT
```
The value is i is 1
The value is i is 2
The value is i is 3
The value is i is 4
The value is i is 5
```

cat fornested1.sh 
```bash
#!/bin/bash
# nesting for loops
for (( a = 1; a <= 3; a++ ))
do
echo "Starting loop $a:"
for (( b = 1; b <= 3; b++ ))
do
echo " Inside loop: $b"
done
done
```
$ chmod 755 fornested1.sh
 
$ ./fornested1.sh 
 ## OUTPUT
```
1 - 5
2 - 4
3 - 3
4 - 2
5 - 1
```
 
cat forbreak.sh 
```bash
#!/bin/bash
# breaking out of a for loop
for var1 in 1 2 3 4 5
do
if [ $var1 -eq 3 ]
then
break
fi
echo "Iteration number: $var1"
done
echo "The for loop is completed“
```
## OUTPUT
```
Starting loop 1:
 Inside loop: 1
 Inside loop: 2
 Inside loop: 3
Starting Loop 2:
 Inside loop: 1
 Inside loop: 2
 Inside loop: 3
Starting Loop 3:
 Inside loop: 1
 Inside loop: 2
 Inside loop: 3
```

$ chmod 755 forbreak.sh
 
$ ./forbreak.sh 
 
cat forbreak.sh 
```bash
#!/bin/bash
# breaking out of a for loop
for var1 in 1 2 3 4 5
do
if [ $var1 -eq 3 ]
then
continue
fi
echo "Iteration number: $var1"
done
echo "The for loop is completed“
```

 
$ chmod 755 forcontinue.sh
 
$ ./forcontinue.sh 
## OUTPUT
```
 Iteration number: 1
Iteration number: 2
The for loop is completed
```

cat exread.sh 
```bash
#!/bin/bash
# testing the read command
echo -n "Enter your name: "
read name
echo "Hello $name, welcome to my program. "
 ```
 
$ chmod 755 exread.sh 
 
$ ./exread.sh 
## OUTPUT

```
#!/bin/bash
# testing the read command
echo -n "Enter your name: "
read name
echo "Hello $name, welcome to my program. "
```

 cat exread1.sh
```bash
#!/bin/bash
# testing the read command
read -p "Enter your name: " name
echo "Hello $name, welcome to my program. “
``` 
$ chmod 755 exread1.sh 

## OUTPUT
```
Enter your name: Karthikeyan
Hello Karthikeyan, welcome to my program. 
```

$ ./exread1.sh 
 
cat funcex.sh
```bash
#!/bin/bash
# trying to access script parameters inside a function
function func {
echo $[ $1 * $2 ]
}
if [ $# -eq 2 ]
then
value=`func $1 $2`
echo "The result is $value"
else
echo "Usage: badtest1 a b"
fi
```
## OUTPUT
 ./funcex.sh 
Usage: badtest1 a b
 
 ./funcex.sh 1 2
 The result is 2
 
cat argshift.sh
```bash
#!/bin/bash 
 while (( "$#" )); do 
  echo $1 
  shift 
done
```
$ chmod 777 argshift.sh

## OUTPUT
$ ./argshift.sh 1 2 3
 1
2
3

 cat argshift1.sh
```bash
 #/bin/bash 
 # store arguments in a special array 
args=("$@") 
# get number of elements 
ELEMENTS=${#args[@]} 
 # echo each element in array  
# for loop 
for (( i=0;i<$ELEMENTS;i++)); do 
    echo ${args[${i}]} 
done
```
$ chmod 777 argshift.sh
## OUTPUT
$ ./argshift.sh 1 2 3
 1
2
3

cat argshift.sh
```bash
#!/bin/bash 
set -x 
while (( "$#" )); do 
  echo $1 
  shift 
done
set +x
```
## OUTPUT
 ./argshift.sh 1 2 3
 #!/bin/bash 
+ ((  3  ))
+ echo 1 
1
+ shift
+ ((  2  ))
+ echo 2
2
+ shift
+ ((  1  ))
+ echo 3
+ shift
+ ((  0  ))
+ set +x

cat>data.dat
```bash
bcdfghj
abcdfghj
bcdfghj
ebcdfghj
bcdfghj
ibcdfghj
bcdfghj
obcdfghj
bcdfghj
ubcdfghj
```
awk -f nc.awk data.dat
## OUTPUT 
 ```
7         bcdfghj
8	  abcdfghj
7	  bcdfghj
8  	  ebcdfghj
7	  bcdfghhj
8	  ibcdfghj
7	  bcdfghj
8	  obcdfghj
7	  bcdfghj
8 	  ubcdfghj
total characters 75
Number of Lines are 10
No of Words count: 10

```

cat > palindrome.sh
```bash
#num=545
echo "Enter the number"
read num
s=0
rev=""
temp=$num
while [ $num -gt 0 ]
do
	# Get Remainder
	s=$(( $num % 10 ))
	# Get next digit
	num=$(( $num / 10 ))
	# Store previous number and
	# current digit in reverse
	rev=$( echo ${rev}${s} )
done
if [ $temp -eq $rev ];
then
	echo "Number is palindrome"
else
	echo "Number is NOT palindrome"
fi
```
## OUTPUT 
```
locathost:~# chmod 755 palindrome.sh
locathost:~# ./palindrome.sh
Enter the number
21
Number is NOT palindrome

locathost:~# chmod 755 palindrome.sh
locathost:~# ./palindrome.sh
Enter the number
33
Number is palindrome
locathost:~#


```
# RESULT:
The Commands are executed successfully.
