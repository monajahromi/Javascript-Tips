# Ways Of Copying Array In JavaScript

you can copy a object in JavaScript using different approaches, I have found 5 ways of copying array, if you have found any more feel free to share it with me :)

The important thing in copying Object in JavaScript is to notice that if we are copying the object using copying reference or its value,
To understand this you have to know that all the primitive are store using reference to value, and all the Objects are strode using reference, this means that the follow code will save the reference to 

let persons = [{name :'mona'}]; 

JavaScript will store {name : 'mona'} somewhere in memory and save the reference to it in persons, when we create a copy named personCopy  using reference copy it will copy the reference not the exact value,  so we have two pointer to the main value,  one is persons and second pointer is personCopy , if we change the name to ‘tine’ both persons and its copy will be affected.

I hope that was clear, now we will see different ways of copying object in JavaScript with example: 


## 1) Using Slice()  

>The **array.slice(start,end)** method returns the selected elements in an array, as a new array object.
if we don’t provide start and end, it will return a copy of array

```
let persons = [{name :'mona'},{name : 'hana'}];  
personCopy = persons.slice()
```

## 2) Using Splice()
>The **array.splice(index, howmany, item1, ....., itemX)** method adds/removes items to/from an array, and returns the removed item(s).
if we remove all the array elements and replace all of elements again, the deleted value will be returned and we can use it as copy of object :

```
let persons = [{name :'mona'},{name : 'hana'}];  
personCopy = persons.splice(0,persons.length,...persons)
```

## 3) Using concat()
The 
> The **array.concat(array2, array3, ..., arrayX)** method is used to join two or more arrays. If we don’t sent any arguments to method, it will return the original array 

```
let persons = [{name :'mona'},{name : 'hana'}];  
let personCopy = persons.concat();
```

## 4) using Object.assigne()
>The **Object.assign(target, ...sources)** method copies all enumerable own properties from one or more source objects to a target object. 
It returns the target object.

```
let persons = [{name :'mona'},{name : 'hana'}];  
let personCopy = [];
Object.assign(personCopy  , persons);
```

## 5) Json.parse(Json.stringyfy(array))

Json.stringyfy() : 
>Any JavaScript object can be stringyfied (converted to a string) with the JavaScript function

JSON.parse() :
> JSON.parse() method parses a JSON string, constructing the JavaScript value or object described by the string. 
An optional reviver function can be provided to perform a transformation on the resulting object before it is returned.

```
let persons = [{name :'mona'},{name : 'hana'}];  
let personCopy = Json.parse(Json.stringyfy(oldObj)) ; 
```


***Notice***

**Slice(),Splice(),Concat(),Object.assign 
Use the following strategy for copying each elements of array :
if the element is primitive it will copy the value and if the element is object it will copy the reference.**

**For making sure the elements will be copied totally you have to use 
Json.parse(Json.stringyfy(array))**
