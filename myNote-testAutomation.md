# myNote-testAutomation


### automation strategy meet business needs

## pytest

unit test 
feature test




#locater

## 
* html
    * element
        * tagname
        * attribute
* css
* js
* DOM - API
    * element vs locater/selector
* locator type
    * ID
    * name
    * class name
    * 
    * css selector
    * XPath


### css selector
 pattern matching
 
* attribute - [name=Jason]
* or - , 
* class - .
* id - #
* decendant - ' ' space
* direct decendant - >
* :not 
* :nth-child(5)
* 

```


# psudo class
div.result:not(.result--more)




```

### xpath
* absolute - /
* relative - //

* attribte - //li[@class='myclassname']
* and or  = 
    * //img[@width<20][@height<20]
    * //img[@width<20 and @height<20]

* contains
    * //div[contains(@class, 'myclassname')]   # substring

* starts-with 
* not