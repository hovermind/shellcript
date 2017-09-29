typeofvar () {

    local type_signature=$(declare -p "$1" 2>/dev/null)

    if [[ "$type_signature" =~ "declare --" ]]; then
        printf "string"
    elif [[ "$type_signature" =~ "declare -a" ]]; then
        printf "array"
    elif [[ "$type_signature" =~ "declare -A" ]]; then
        printf "map"
    else
        printf "none"
    fi

}


# In Linux (Shell), there are two types of variable:
# 1. System variables - Created and maintained by Linux itself. This type of variable defined in CAPITAL LETTERS.
# 2. User defined variables (UDV) - Created and maintained by user. This type of variable defined in lower letters.

# Variable:
thisScriptName="lol.sh"
echo $thisScriptName

# N.B: 
# - Don't put spaces on either side of the equal sign when assigning value to variable. 
# - declare without $, use $ to get value (without $ => echo myVar will print variable itself instead of value)

# to see all environmental variables: env or printenv
# https://www.cyberciti.biz/faq/linux-list-all-environment-variables-env-command/

# Script name (with & without path)
scriptNameWithPath=$0
scriptName=`basename $scriptNameWithPath`  # backtick not single qoute

# N.B:
# whatever inside backtick is treated as command and will be executed

# Parameter substitution
# when `cmd` is used with other command, it's called Parameter substitution
# i.e. we want to copy files from /home/tmp to current directory (/home/vault)
# cp   /home/tmp/*.log   /home/vault => cp /home/tmp/*.log `pwd`		
# `pwd` => current directory => /home/vault


# echo Command
# echo [options] [string, variables...] Displays text or variables value on screen.
# Options
# -n Do not output the trailing new line.
# -e Enable interpretation of the following backslash escaped characters in the strings:
# \a alert (bell)
# \b backspace
# \c suppress trailing new line
# \n new line
# \r carriage return
# \t horizontal tab
# \\ backslash


# Shell Arithmetic
# expr 1 + 3
# expr 2 - 1
# expr 10 / 2
# expr 20 % 3
# expr 10 \* 3

# Note:
# expr 20 %3 - Remainder read as 20 mod 3 and remainder is 2.
# expr 10 \* 3 - Multiplication use \* and not * since its wild card.

result=`expr 6 + 3`   # backtick not single qoute
echo $result

# double qoute, single qoute & backtick
# "" => string with interpolation for  \ and $
# '' => verbatim string (no interpolation)
# `` => `cmd` => To execute command
# backtick in "" => echo "today is `date`"
# "" in backtick => `basename "$0"`

# $() => instead of `` [ $(pwd) == `pwd` ]
# ${} => variable interpolation (msg="lol"; echo "message: ${msg}")


# Exit Status: 
# whether command or shell script executed is successful or not
# zero    => command is successful.
# nonzero => command is not successful or some sort of error executing command/shell script.


# read => to get input (data from user) from keyboard and store (data) to variable.
# read name

# Wild cards
# *       => any >=1 characters
# ?       => any single character
# []      => characters inside []
# [x-y]   => range from x to y
# [^x-y]  => !(from x to y)


# ; => more than one command in one line i.e. date; who 

# $#        => holds number of arguments specified on command line
# $* or $@  => all arguments passed to script.



# passing arguments to myShell
myShell foo bar

# catching arguments in myShell (positional parameters - $0 $1 $2)
# $0 => name of the script itself => "myShell"
# $1 => foo
# $2 => bar

# redirection symbols >, >>, <
# Linux-command > filename   => if file already exist, it will be overwritten else new file is created
# Linux-command >> filename  => if file exist , it will append, And if file is not exist, then new file is created
# Linux-command < filename   => take input to Linux-command from file instead of key-board

# Pipe
# output of one command is stored and then passed as the input for second command
# command1 | command2


# flag (short & long)
# head -n20         => n for number of lines (20)
# head −−lines=20   => 20 lines

# filter => head, tail these command are called filter

# running script
# ./your_script.sh  => execute the script in a separate process
# . your_script.sh or . ./your_script.sh =>  executes the code of the file test.sh inside the running instance of bash. 
# It works as if the content file test.sh had been included textually instead of the . ./test.sh lin


# ~      => home directory
# $      => normal user
# #      => admin (root user)


# [user@machine ~]$     => RedHat
# user@machine: ~$      => Ubuntu
# user@machine: ~>      => openSUSE

# running a command in background => &
# Linux Command Related with Process => http://www.freeos.com/guides/lsst/ch02sec20.html

# branching

# normal if
if condition
then

fi

# else if
if condition
then

else

fi

# else if ladder
if condition
then

elif condition1 
then
 
elif condition2
then
          
else

fi


# if condition; then  => then can be put in same line - use ;


# switch

case  $variable-name  in
	pattern1)  command

	pattern2)  command

	patternN)  command

	*)         command
esac


# 'test command' or '[ expr ]' & logical operators => http://www.freeos.com/guides/lsst/ch03sec02.html



# looping

# for loop
for { variable name } in { list }
do

done

for i in 1 2 3 4 5
do
	echo "Welcome $i times"
done


for ((  i = 0 ;  i <= 5;  i++  ))
do
  echo "Welcome $i times"
done


# while loop
while [ condition ]
do

done



# deugging shell script
# sh   option   { shell-script-name } OR bash   option   { shell-script-name }
# options:
# -v   => Print shell input lines as they are read.
# -x   => After expanding each simple-command, bash displays the expanded value system variable



# command > /dev/null => send unwanted output of program
# Output of above command is not shown on screen its send to this special file. The /dev directory contains other device files

# by default script variables are local
# to send one script variable to other script  => export var1, var2 ... varN


# Conditional execution
# command1 && command2  => command2 is executed if, and only if, command1 returns an exit status of zero.
# command1 || command2  => command2 is executed if and only if command1 returns a non-zero exit status.

# I/O redirectors
# I/O redirectors are used to send output of command to file or to read input from file
# By default in Linux every program has three files associated with it. when we start our program these three files are automatically opened by your shell. 
# stdin  => file-descriptor-number : 0
# stdout => file-descriptor-number : 1
# stderr => file-descriptor-number : 2

# Syntax: 
# file-descriptor-number>file_name    (no space i.e. 2>file_name)
# rm bad_file_name 2>errors.log    => print error messages(2) to errors.log

# from>&destination  => get from & redirect to destination
# 1>&2               => get from stdout(1) & redirect to stderr(2)



# function
function-name( )
{
	command1
	command2
	...
	commandN
	
	return
}

# call: function-name

# array
# ARRAY=(one two three)
# echo ${ARRAY[1]}   => two
# echo ${ARRAY[*]}   => one two three
# ${#ARRAY[@]}       => 3 (elements)
# ${!ARRAY[@]}       => index (0, 1, 2)
# ${ARRAY[@]}		 => items

# utility
# awk => awk pattern filename
# sed
# uniq => sort personame | uniq
# grep => grep "too" demofile


# Using range of characters in regular expressions
# http://www.freeos.com/guides/lsst/ch06sec09.html



# ; => commamnd terminator
# & => new process (also commamnd terminator)


#string empty check
line=""
if [ ! -z "$line" ]; then

	# will check for empty and null
fi

#removing nrt from string
# remove \n \r \t ' '
line_no_nrt="${line//[$'\t\r\n ']}"


#reading file

tf="foo/bar/baz.txt"

# read text file
while IFS= read -r line; do

	if [ ! -z "$line" ]; then
	
		# remove \n \r \t ' '
		line_no_nrt="${line//[$'\t\r\n ']}"
		
		# call function to copy
		loop_and_copy "$line_no_nrt" "$tf"
	fi

done <"$tf"


# substring
"$string" | sed -r 's/[xyz]+/_/g'

You might find this link helpful:

http://tldp.org/LDP/abs/html/string-manipulation.html

In general,

To replace the first match of $substring with $replacement:

${string/substring/replacement}
To replace all matches of $substring with $replacement:

${string//substring/replacement}
EDIT: Note that this applies to a variable named $string.






#!/bin/sh

# message print in stdout
IS_STDOUT_INABLED=0

# constants
THIS_DIR=$(pwd)

# input date
USER_INPUT_DATE=$1
if [ -z "$USER_INPUT_DATE" ]; then
	USER_INPUT_DATE=$(date +%y%m%d)
fi
#echo "$USER_INPUT_DATE"

#copy folder
COPY_DIR="$THIS_DIR/tmp_copy"
if [[ ! -d "$COPY_DIR" ]]; then
	#printf "\ncreating copy folder..........\n\n"
	$(mkdir "$COPY_DIR" 2>/dev/null)
fi

# backup folder
BACKUP_DIR="$THIS_DIR/tmp"
if [[ ! -d "$BACKUP_DIR" ]]; then
	#printf "\ncreating backup folder..........\n\n"
	$(mkdir "$BACKUP_DIR" 2>/dev/null)
fi

# txt files directory
FIND_STRING_CONFIG_DIR="$THIS_DIR/find_string_config"


loop_and_copy(){

	# arguments
	local find_str=$1
	
	# finding all files in the folder
	local FILES=($(find $find_str -type f))
	
	# previous command failure
	if [ $? -ne 0 ]; then
	
		if [ $IS_STDOUT_INABLED -eq 1 ]; then
			printf "\n============ command failed for  (find $find_str -type f)\n" 
		fi

		return 0
	fi
	
	# empty check
	if [ ${#FILES[@]} -le 0 ]; then
	
		if [ $IS_STDOUT_INABLED -eq 1 ]; then
			printf "\n============ emtpty folder ($find_str)\n" 
		fi

		return 0
	fi
	
	if [ $IS_STDOUT_INABLED -eq 1 ]; then
		printf "\n============ $find_str\n\n"
	fi
	
	# loop files
	for fileToCopy in "${FILES[@]}"; do
	
		# copy command
		cp $fileToCopy $COPY_DIR
		
		if [ $IS_STDOUT_INABLED -eq 1 ]; then
			echo "    - $(basename "$fileToCopy")"
		fi
		
	done
}


process_line_and_copy(){

	local line=$1
	
	#${filename:offset:length}
	local day=${USER_INPUT_DATE:4:2}
	local md=${USER_INPUT_DATE:2:4}
	
	local find_str=""

	if [[ "$line" =~ ^(.*\/sa\*)$ ]]; then
		
		# /var/log/sa/sa* => /var/log/sa/sa*29
		find_str="${line/\*/*$day}"
		
		if [ $IS_STDOUT_INABLED -eq 1 ]; then
			printf "\n\n============ $line ==>> $find_str"
		fi

	elif [[ "$line" =~ ^(.*\.\*\.log\.\*)$ ]]; then
	
		# /home/image/syst_tools/log/SysTool_Netstat.*.log.* => /home/image/syst_tools/log/SysTool_Netstat.*0929.log.*
		find_str="${line/.*.log.*/.$md.log*}"

		if [ $IS_STDOUT_INABLED -eq 1 ]; then
			printf "\n\n============ $line ==>> $find_str"
		fi

	else
		find_str="$line"
	fi
	
	loop_and_copy "$find_str"
}


zip_dir(){

	# argument
	local DIR_TO_ZIP=$1
	
	# date time
	local DATE_TIME=$(date +%Y%m%d-%H%M%S)
	
	# zip file name
	local ZIP_NAME_WITH_PATH="$BACKUP_DIR/backup_$DATE_TIME.zip"
	
	zip -r "$ZIP_NAME_WITH_PATH" "$DIR_TO_ZIP" 1>/dev/null 2>/dev/null
	
	if [ $IS_STDOUT_INABLED -eq 1 ]; then
		if [ $? -eq 0 ]; then
			printf "\n\n zipped successfully : $ZIP_NAME_WITH_PATH\n\n"
		else
			echo "\n\n failed to zip : $ZIP_NAME_WITH_PATH\n\n"
		fi
	fi
}

# get text files only - text files contain search string i.e "/home/emc/ivr/log/*"
text_files=($(find $FIND_STRING_CONFIG_DIR -type f -name *.txt))

# loop text files
for tf in "${text_files[@]}"; do

	# read text file
	while IFS= read -r line; do
	
		if [ ! -z "$line" ]; then
		
			# remove \n \r \t ' '
			line_no_nrt="${line//[$'\t\r\n ']}"
			
			# function will process & will call loop_and_copy
			process_line_and_copy "$line_no_nrt"
		fi

	done <"$tf"
	
done

# now zip it 
if [ $IS_STDOUT_INABLED -eq 1 ]; then
	printf "\n\n copying completed ............................................\n"
	printf "\n\n zipping ......................................................\n\n"
fi
# zip command
zip_dir $COPY_DIR

#remove copy folder
if [ -d "$COPY_DIR" ]; then
	if [ $IS_STDOUT_INABLED -eq 1 ]; then
		printf "\n\n removing tmp copy folder .....................................\n\n"
	fi
	
	# remove tmp copy folder
	$(rm -rf "$COPY_DIR")
	
	if [ $IS_STDOUT_INABLED -eq 1 ]; then
		printf "\n\n all done .....................................................\n\n\n"
	fi
fi















