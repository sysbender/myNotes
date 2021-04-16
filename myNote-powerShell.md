# myNote - powershell

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

## get-help

```
# options
get-help help -full -detailed -example -online

get-help get-command -showWindow


```

## get-module

### get-member - what type of object

```
get-random | get-member
```

### find-module - find a module on psgalaxy
```
Find-Module -Tag telegram
```


