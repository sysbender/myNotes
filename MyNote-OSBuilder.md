# MyNote-OSBuilder

## reference

https://www.deploymentresearch.com/building-the-perfect-windows-server-2019-reference-image/



## install and update
```
# install

Install-Module -Name OSDBuilder -Force
Import-Module -Name OSDBuilder -Force

# update

Uninstall-Module OSBuilder -AllVersions -Force
Install-Module OSDBuilder -Force
Import-Module OSDBuilder -Force

# 

OSDBuilder -update


```

## get started

```
 Get-OSBuilder -SetPath v:\osdbuilder

# import media
Import-OSMedia -ImageIndex 6 -SkipGrid
Import-OSMedia -ImageName 'Windows 10 Enterprise' -SkipGrid


# import and update
Import-OSMedia -Edition Enterprise -SkipGrid -Update

```

## sample workflow

```
$ISOpath = 'c:\win10.iso'

# install/update OSDbuilder 

# 
Mount-DiskImage -ImagePath $isopath
Import-OSMedia -ImageName 'Windows 10 Pro' -SkipGrid -Update -BuildNetFX


```
## OSMedia

```
# list imported OS
Get-OSMedia

# download update and apply to OS
Update-OSMedia -Download -Name "Windows 10 Pro x64 20H2 19042.508" -execute







```


