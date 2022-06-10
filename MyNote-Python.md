# MyNote-Python


## h2


### enumerate in for loop
```

for rowno , row in enumerate(rows, start=1)
    print(rowno, row)

```

### don't catch all Exception

```
try:
    a = 'a' +1
except Exception as err:
    print("this could hide some bug")

```

### data structure

* tuple - record :  pack/unpack, immutable, (1,2,3)
* list - same type, [1,2,3]
* set - distinct , {1,2,3}
* dict - {'a':1, 'b':2}


 