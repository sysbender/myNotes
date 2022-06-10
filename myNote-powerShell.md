# myNote-powershell



techthouths

https://www.youtube.com/watch?v=4-L7HwLgsf4&list=PL2j0_s2VJe2hzQuQyn6yfMS2olhhs4UnQ&index=5


## basic command
### get-command

 verb-noun
 
 type:
     function
     alias
     cmdlet

```
get-command -all
get-command -Verb stop
get-command -noun service

get-command -noun *serv*
get-command -commandType cmdlet

```

### get-help

```
# options
get-help help -full -detailed -example -online

get-help get-command -showWindow


```

### get-module

### get-member - what type of object

```
get-random | get-member
```

### find-module - find a module on psgalaxy
```
Find-Module -Tag telegram
```


## pipeline

$PSItem contains current object of the pipeline
$_ - shortcut


```
get-process | sort-object id
get-process notepad | stop-process


# check if accecpt pipeline input
get-help get-process -full 

Get-Process | ForEach-Object { $PSItem}
1,2,3 | ForEach-Object { $PSItem }

Get-Date | Format-Table
Get-Date | Format-List

# get all the property
Get-Process notepad | Format-List *

# select properties
 get-process notepad++ | Select-Object id, name, path
 
 # filter object
 get-process | Where-Object {$_.CPU  -gt 10000}
 
 Get-ChildItem -Path c:\tmp  | Where-Object { $_.Length -gt 10MB }
 
 # count
 Get-ChildItem -Path c:\tmp  | Where-Object { $_.Length -gt 10MB } | Measure-Object
 
 
 # 
 get-process | Stop_process -Whatif
```

## powershell 6

cross-platform

```

 $PSVersionTable
 
 
Install-Module WindowsCompatibility -Scope CurrentUser


```
## visual studio code
install powershell extension

Install-Module PSScriptAnalyzer

#  powershell -超速蜗牛 SpecialPowershell

01 - intro

3 command:
1. Get-Help
1. Get-Member
1. Get-Command

```
get-help get-childItem
get-childItem -?


get-help
get-command

write-host "hello world"



```
## 02 - basic
comment 
* single line #
* multiple line <# here #>

call batch command
```
cmd /c echo "hello"
```

call exe - 3 ways
```
# 1. full path
.\notepad.exe
# with space in path
& "D:\Learning\Wechat\02\notepad with space.exe"  
# 2. start process

# 3. .net class
[void][System.Diagnostics.Process]::Start("notepad")

```

array
```
(1..5)[1,3]  # create 1 to 5 array, and return 2nd and 4th element
$host,$user=$line.split(',')[1,2] 
```

operator
```
5 -gt 2
2 -eq 2
"hello" -eq "hel"


1 -in 1..5
"hello" -like "*he*"

"a","b", "c" -join "-"

"a,b,c".split(",")
"a,b,c" -split ","

"a,b,c" -replace "^a",  "1a"
# format
"{0:yyyy-MM-dd-hh:mm:ss}" -f (get-date)
```

## 03 - format

```
get-date

"{0:yyyyMMdd}" -f (get-date)  # {0:format} -f (array_element1, array_element2) 

# array - @()
@(1..5)
@(1,2,3)

"{0} zero {1} first {2} second" -f (0,1,2)
"c:\temp\{0:yyyyMMdd}-{1}.log" -f (Get-Date),"test"

"{0:n2}" -f 3.14156 # precision 2
"{0:X4}" -f 1324 # 4 hex
```

## 04 - EnvVar , property and method 

```
#  env var

"{0}-{1}-{2}" -f $env:HOMEDRIVE, $env:HOMEPATH, $env:HOMESHARE

# .net [namespace]::

"{0}" -f ([System.Environment]::GetEnvironmentVariable("HOMEDRIVE"))

# property and method

'1234'.Lenght
@(1234).count
(1234).GetType()

'1234'.size -eq $null   # return null when property doesn't exist

# list property and method

Get-Member -InputObject '1234' | sort MemberType

# only run a method when it exists
'1234'|gm|?{$_.MemberType -eq "Method" -and  $_.name -contains 'GetLength'}|%{'1234'.GetLength()}

(Get-Date).ToString()
(Get-Date).ToString("yyyyMMdd HH:mm:ss")
"{0:yyyyMMdd HH:mm:ss}" -f (Get-Date)
```

## 05 -variable

```

#declare var with $

# data type - [datetime] [string] [char] [double] [single] [int] [wmi] [adsi] [wmiclass] [Boolean]


$name = "John"
New-Variable -Name name -Value "John"


## implicit data type
$n = 123
$n.GetType()
## explicit data type
[double]$m = 123
$m.GetType()
```
## 06 variable scope
```
$number = 1

function say-hello($name ){
   write-host "hello $name";
}

function test-number {
    $number = $number +1;  # child scope can read variable in parent, but can not change
    write-host "in function, number = $number";
    return

}


say-hello "john"
say-hello ("world")
test-number

write-host "out of function , number = $number"
# new variable options - None(default), ReadOnly, Private, AllScope, Constant
New-Variable pie -Value 3.14 -Option Constant

$Local:lVar =1   # default
$Global:gVar =2   # can be accessed from other script
$Script:sVar =3  # current script file
$Private:pVar = 4 #can not access from child scope

```

##07-  variable trick

```
# 07
$n = 1
write-host "`$n is $n"   # ` escape $ sign

${@var} ="spefical var name"   # explicit var name enclosure
write-host ${@var} 
 
${d:\ps.txt} = "this is a ps test"   # write content to file
write-host ${d:\ps.txt}   # read from a file

# type convert
$logtime = [datetime]"2020/01/02" 
write-host $logtime.GetType()

```

##08 - pipeline

```
# pipeline
#special varialbe : $_ $^ $$ $?

# where-object where ?
# Foreach-Object Foreach %

ls C:\tmp | where {$_.Name -imatch "png"}


# contine - end the loop
# return - skip to next loop
1..5 | %{ $_ * $_ } | %{
  if ($_ -ne 9)
   {Write-Host $_ }  
  else{
   return
  }

}
```

##09 - loop and switch
```
# switch -Regex -WildCard

$gender = "m"
Switch -Wildcard  ($gender){

"m" {"man";break}
"f" {"woman"; break;}
default {"Guy" }
}

for ($n =0; $n -lt 4 ; $n++) {}

foreach ($n in 1..3){}


```
## 10 break continue exit return


## 11 - hashtable

```
<#

To create a hash table, follow these guidelines:
Begin the hash table with an at sign (@).
Enclose the hash table in braces ({}).
Enter one or more key/value pairs for the content of the hash table.
Use an equal sign (=) to separate each key from its value.
Use a semicolon (;) or a line break to separate the key/value pairs.
Key that contains spaces must be enclosed in quotation marks. Values must be valid PowerShell expressions. Strings must appear in quotation marks, even if they do not include spaces.
To manage the hash table, save it in a variable.
When assigning an ordered hash table to a variable, place the [ordered] attribute before the "@" symbol. If you place it before the variable name, the command fails.

#>


$student =@{}


 $people = @{
name='john';
age=25
}

$people.GetType()

# add item
$people.age
$people.Add("Salary","9999")

#enumerate Items
$people.GetEnumerator() |
%{
 write-host( "key={0} value={1}" -f $_.key, $_.Value )

}

## using the way of .net hashtable
$myhash1 = [System.Collections.Hashtable]::new()
$myhash2 = New-Object System.Collections.Hashtable

$myhash1.GetType()
$myhash2.GetType()


```

## 15 - function parameter

1. end : return , break , exit
2. scope : script
3. parameter - 2 way
4. call - 2 way

```


Function script:Test-Func(){


}

# 
Function Test-param1($param1 , $param2 ){


}

Function Test-Param2(){
    param(
        $param1,
        $param2

    )


}



Function Test-Func2($param1, $param2){

    Write-Host "param1 = $param1, param2 = $param2"
}

# call function - method 1
Test-Func2 "a"  "b"

# call function - method 2
${Function:Test-Func2}.invoke("aa", "bb")

# validate parameter

Function Test-Func5(){
    param(
    [ValidateLength(2,5)]
    [ValidatePattern("^a")]
    $param    
    
    )

    Write-Host( " the length of `$param is {0}` " -f $param.length)

}

Test-Func5 "aaa"

```

## .net

* types
* namespaces
* methods
* enum
* 