# In Linux (Shell), there are two types of variable:
# 1. System variables - Created and maintained by Linux itself. This type of variable defined in CAPITAL LETTERS.
# 2. User defined variables (UDV) - Created and maintained by user. This type of variable defined in lower letters.

# Variable:
thisScriptName="lol.sh"
echo $thisScriptName

# N.B: 
# - Don't put spaces on either side of the equal sign when assigning value to variable. 
# - declare without $, use $ to get value ($ => kinda dereferencing, without $ => echo myVar will print variable itself instead of value)

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
# cp /home/tmp/*.log /home/vault => cp /home/tmp/*.log `pwd`		
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
