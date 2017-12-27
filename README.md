## Variable

 ***In Linux (Shell), there are two types of variable:***
  - System variables - Created and maintained by Linux itself. This type of variable defined in CAPITAL LETTERS.
  - User defined variables (UDV) - Created and maintained by user. This type of variable defined in lower letters.

*Syntax*
```
thisScriptName="demo.sh"
echo $thisScriptName
```
**N.B:**
 - Don't put spaces on either side of the equal sign when assigning value to variable. 
 - declare without $, use $ to get value (without $ => echo myVar will print variable itself instead of value)
 
To see [all environment variables](https://www.cyberciti.biz/faq/linux-list-all-environment-variables-env-command/): `env or printenv`

## Script name (with & without path)
```
scriptNameWithPath=$0
scriptNameWithoutPath=`basename $scriptNameWithPath`   // backtick not single qoute
```
**N.B :** whatever inside backtick is treated as command and will be executed

## Parameter substitution

*When \`[a command]\` is used with other command, it's called parameter substitution. For example, we want to copy files from "/home/tmp" to current directory "/home/vault". The \`pwd\` prints current directory which is "/home/vault". So,*
```
cp /home/tmp/*.log `pwd`
```
Is same as:
```
cp /home/tmp/*.log /home/vault
```

## Echo

*Displays text or variables value on screen*

`echo [options] [string, variables...]`

**Options**

| Flag | Meaning |
|------|---------|
| -n | Do not output the trailing new line |
| -e | Enable interpretation of the following backslash escaped characters in the strings<br><br>\\a alert (bell)<br>\\b backspace<br>\\c suppress trailing new line<br>\\n new line<br>\\r carriage return<br>\\t horizontal tab<br>\\\\ backslash |

## Arithmetic
```
expr 1 + 3
expr 2 - 1
expr 10 / 2
expr 20 % 3
expr 10 \* 3
```
**Note:**
 - `expr 20 % 3`  => Remainder read as 20 mod 3 and remainder is 2
 - `expr 10 \* 3` => Multiplication use \\* and not '*' since its wild card.

```
result=`expr 6 + 3` // backtick not single qoute
echo $result
```

## double qoute, single qoute & backtick

|symbol|purpose|
|------|-------|
|double quote : ""|string with interpolation for \\ and $|
|single quote : ''|verbatim string (no interpolation)|
|a command within backtick : \`[a command]\`|To execute a command|
|backtick inside ""|echo "today is \`date\`"|
|"" inside backtick|\`basename "$0"\`|
|`$([a command])`|equivalent to \`[a command]\`<br>i.e. `$(pwd)` & \`pwd\` are same|


## Variable Interpolation `${}` 
```
msg="Hello Hooman"
echo "message: ${msg}"
```

## Exit Status

*Whether command or shell script executed successfully or not*

|exit code|meaning|
|---------|-------|
|zero|command is successful|
|nonzero|command is not successful or some sort of error executing command/shell script|

## Read

*To get input (data from user) from keyboard and store to variable.*
```
read name
```





