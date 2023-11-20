## Different between Interface and Type in TypeScipt
1. Delcaration merging
- Interface - Samename will merge
- Type - Error

2. Extends and Intersection
- Interface -  be extended a type
```ts
interface PersonNameInterface { name: string }
interface Person1 extends PersonNameInterface { age: number }

type PersonNameType = { name: string }
interface Person2 extends PersonNameType { age: number }

class PersonClass { name = "Jhon" }
interface Person3 extends PersonClass { age: number }
```

- Type - Can't be extended, type can't extend class, we can combine numerous type into one type to form intersection type
```ts
type PersonNameType = { name: string; }
type Person1 = PersonNameType & { age: number; }

interface PersonNameInterface { name: string; }
type Person2 = PersonNameInterface & { age: number; }
```

3.  Implements and Union
- Class can implement/extend a interface or type in same way exepted for Uniontype
```ts
interface PersonInterface {
 name: string;
 age: number;
}

class John implements PersonInterface {
 name = "John";
 age = 26;
}

type PersonType = {
 name: string;
 age: number;
};

class Ann implements PersonType {
 name = "Ann";
 age = 26;
}

type UnionType = { name: string; } | { age: number; };

// Gives an error
class Joel implements UnionType {
 name = "Joel";
 age = 2;
}
```

- Type not support for implements and extends

We can use union for both type and interface combination

#### What should we use ?
- Interface : 
  - a new object or an object methoid needs to be defined.
  - You wish the benefit from declaration merging

- Type:
  - You need to define a promitive-type alias
  - Defining tuple type
  - Defining a union

Types are better for working with functions, complex types, etc.

Interfaces work better with objects and method objects.

***Need to get more real experience on that ***

## When will we use implement and extends in typescript ?
- Extends : that can reuse all methods from parent
- Implement: That we need to override all the method of inteface



