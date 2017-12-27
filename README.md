## Variable
 **In Linux (Shell), there are two types of variable:**
 1. System variables - Created and maintained by Linux itself. This type of variable defined in CAPITAL LETTERS.
 2. User defined variables (UDV) - Created and maintained by user. This type of variable defined in lower letters.

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

