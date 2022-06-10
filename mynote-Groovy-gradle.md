# mynote-Groovy-gradle

type enforement at runtime， not compile
* parenthesis - optional , mandatory when no arguments
* string interpolation
* closure implicity parameter : it ; 
    * always return a value 
    * pass closure as parameter
    * closure keep a reference to the variable in the parent content
    * delegate - how closure resolve symbol
    * 


```
def sayIt = {
it -> it * it
}

sayIt("foo")

// pass closure as parameter

def method1(closure){
    closure() * 2
}
```

common closure use

for iteration

```
for (int i in [1,2,3]){
    println(i)
}

[1,2,3].each{
    println it
}


```

delegate

```
class Person {
    String name

    def executeInside(Closure c){
        c.delegate = this
        c()
    }
}


def Person = new Person(name: "john")
Person.executeInside { println name}

```

closure resolution strategy : owner, delegate
```
closure.resolveStrategy = Closure.DELEGATE_FIRST // Closure.OWNER_FIRST
$owner.name
$delegate.name

```

methodMissing - special method 



