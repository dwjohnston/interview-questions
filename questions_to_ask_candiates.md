## Philosophy around conducting interviews

The questions here are intended for generalist JavaScript developers, whether junior to tech lead. They're not intended for someone you're hiring for experience with a specific technology. 

In my opinion, for a general developer position, it is more important to assess a candidate according to _their_ strengths, rather than 'What do we need for this position'. 

For example, say a candidate says that they don't have any experience with creating REST APIs, and part of the position requires them to create REST APIs, then there's no point in asking them questions that they themselves wouldn't profess to be experienced with. 

Now, lets say that for the position, you really _do_ need someone who is experienced with creating REST APIs, then the recruiter/hiring manager should have only sent you people who have said they're good with REST APIs, and your process if process has broken down if you are interviewing a candidate who doesn't rate themselves highly in that skill. 



## Calibration questions 

### 1. Rank your skills relative to each other. 

Make it clear that you're not asking them to compare themselves with others, but your asking 'What are you most comfortable with, and what are you less comfortable with'. 

You can use the experience listed on their CV to prompt them ('OK, it says you have experience with SQL, how does that rank relative to React and CSS?) 

This serves a couple of purposes: 

- Firstly, it gives you a better picture of who they are as a developer. Candidates have the incentive to list every technology they've ever touched, even if they're not particularly comfortable with that technology, because otherwise the recruiter/hiring manager may pass their CV over.

- It helps calibrate and weight the questions you ask them. For example, it might be quite common for someone to have listed 'React/CSS/Express/Mongo' as their experience, but actually they have very little experience with Mongo - they were more of a frontend developer. You can still ask them a Mongo related question, and it's a great sign if they can answer it, but you're not discounting them too much if they can't. 


### 2. Say we had a magic wand, in what context (tooling, processes, people around you) would you be happiest, and do your most effective work? 

This is a good question perhaps for the end of the interview, or just before you geting into the technical stuff. The purpose of it is to get a picture of what _they want_ in a role, and you can place them accordingly. 

## Process Questions 

### 1. You are stuck with an error or some code that isn't working - what is your approach to solving it? 



## JavaScript questions 

### 1. What does this code output? (`const` keyword)

```javascript
const a ="a"; 
a = "b"; 
```
**Purpose:** Tests basic JavaScript syntax knowledge. 

**Answer:** It throws an error at runtime, because the `const` keyword prevents variable reassignment. 

### 2. What does this code output? (object mutation) 

```javascript 
const a = {
    a: 1
}; 

a.a = 2; 

console.log(a); 
```

**Purpose:** This question should be asked in conjunction with question 1. It basically tests that they know what the `const` keyword is doing - that it isn't preventing object mutation. 

**Answer:**  It prints `{a: 2}`. The const keyword does not prevent object mutation. 
### 3. What does this code output? (object equality) 

```javascript 
const a = {
    a: 1
}; 

const b = {
    a: 1
}

console.log(a===b); 
```

**Purpose:** It tests that they know about how object equality in JavaScript works. 

**Answer:** `false` - a and b are two different objects, that happen to have the same data. 





### 4. What does this code output? (object references and mutation) 

```javascript 
const a = {
    value: 1
}; 

const b = a; 

b.value = "hello";

console.log(a);
console.log(b); 
```

**Purpose:** It tests that they that variables in JavaScript are pointers to object, and how object mutation works. 

**Answer:** They both print `{a: "hello"}` - as `a` and `b` point to the same object. 

## TypeScript Questions 


### 1. Why does this code have an error? 

```typescript
function getRandomValue() : number | string {
    if (Math.random() > 0.5) {
        return Math.random(); 
    }
    else {
        return `${Math.random()}`; 
    }
}

function myFunction(value: number) {

}

const value = getRandomValue(); 
myFunction(value);
```

**Purpose** Tests basic knowledge of TypeScript

**Answer** Because value can be a number _or_ a string, and the `myFunction` function _only_ wants a number. 



### 2. Add arguments to the function call such that there are no type errors

```typescript
type SomeThing<T> = {
    value: T; 
    label: string; 
}


function usesSomeThing<T>(thing: SomeThing<T>, value: T) {
    
}

// Add arguments to the function call to avoid type errors
usesSomething(); 
```

**Purpose** Basic TypeScript question - checks if they understand generics syntax. 

**Answer:** 

```typescript
usesSomeThing({
    value: 9, 
    label: "hello"
}, 11); 
```

For example. 


### 3a. How would you make the properties of a type optional? 

Given this code: 

```typescript
type Foo = {
    a: string;
    b: number; 
    c: string; 
}

function usesFoo(foo: Foo) {

}

usesFoo({a: "hello"});
usesFoo({a: "hello", b: 99});
usesFoo({b: 11}); 
usesFoo({c: "hello"}); 


```

How would you change the signature of the function `usesFoo` such that there are no type errors in our example usage? 

**Answer** 

Use the `Partial` utiltiy type. 

```diff
-function usesFoo(foo: Foo) {
+function usesFoo(foo: Partial<Foo>{
}
```

The `Partial` utility type makes all properties optional. 

### 3b. How would you implement a Partial utility type from scratch? 

**Ask if:** They say they have expert TypeScript knowledge/the role requires expert TypeScript knowledge. 

**Answer** 

```typescript 
type OurPartial<T> = {
   [K in keyof T]? : T[K]; 
}
```

Explanation: 

`OurPartial<T>` : We introduce a generic parameter `T`, which is going to be whatever type we want to have optional properties. 

`[K in keyof T]?` We derive a second type `K` which is a union list of of the keys of the the type `T`. We use this type in a *mapped type*, adding the `?` to make them optional. 

` T[K]` We use an *index type* to make the existing value of the property match the original typings property value. 






## CSS Questions 

### 1. What is the difference between these two selectors? 

```
div .foo {

}

div.foo {

}
```

**Purpose:** Demonstrates basic knowledge of CSS selectors. 

**Answer:** The first selects all `.foo` inside a div, the second selects all divs that also have the `.foo` class. 


### 2. How would you center a div horizontally?  How would you center a div vertically? 

**Purpose:** Test basic competency of CSS. 

**Answer:** Use flexbox, grid, `margin:0 auto` for horizontal. 

**Bad answers:** Use float, absolute or relative positioning. 

### 3. What's the difference between a block and inline element in CSS? 

**Ask if:** They rate them self as expert in CSS. 

**Purpose:** Test more advanced, fundamental knowledge of CSS. 

**Answer:** Inline elements can wrap, block elements will always be rectangular. Block elements fill their parent width by default (unless being controlled by a flex or grid container )

Bonus points, but it's ok to miss, is that padding and margin behaves differently on inline elements. 


### 3. What does position:absolute do in CSS, and when would you use it? 

**Ask if:** They rate them self as expert in CSS. 

**Purpose:** Test more advanced, fundamental knowledge of CSS. 

**Answer:** Takes the element out of flow and positions itself relative to the boundings of its next relatively or absolutely positioned parent. 

You tend to use it if you need to create overlapping elements. 

## REST questions 

### What's the difference between POST/PUT/PATCH in a REST API? 

**Ask if:** They rate themselves as experienced with REST. 

**Purpose:** Tests whether they have a more formal understanding of REST structures, rather that simply being able to create endpoint and make HTTP calls against them. 

**Answer:** POST - Create new resource, PATCH - update existing resource, given a subset of that resource, PUT - idempotent 'make the resource look like this'. 



## GraphQL questions 

### What are the pros and cons of REST vs GraphQL 

**Ask if** They rate themselves as experienced with GraphQL

**Purpose:** Really is to detect if they are cargo cult programming with GraphQL. 

I'm clearly a bit opinionated here, but I think that GraphQL is overused, and has a bit of 'shiny new thing' faddiness attached. 

**Answer** 

| REST                                                                                                                                                      |     | GraphQL                                                                                                                                                                                                                                                                                                                                          |                                                                                                                                                                                    |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------|-----|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| PRO                                                                                                                                                       | CON | PRO                                                                                                                                                                                                                                                                                                                                              | CON                                                                                                                                                                                |
| Simple                                                                                                                                                    |     |                                                                                                                                                                                                                                                                                                                                                  |                                                                                                                                                                                    |
| REST API can reflect a relational database.                                                                                                               |     |                                                                                                                                                                                                                                                                                                                                                  |                                                                                                                                                                                    |
| More universally adopted.   More developers are going to be able to write queries against your REST API, as far more developers are  familiar with REST.  |     |                                                                                                                                                                                                                                                                                                                                                  |                                                                                                                                                                                    |
|                                                                                                                                                           |     | The frontend tooling that comes with Apollo  is helpful. (eg. caching, loading state).                                                                                                                                                                                                                                                           |                                                                                                                                                                                    |
|                                                                                                                                                           |     | Solves a lot of boilerplate like code when  otherwise having to perform multiple joins.   (eg. student has their favourite book, the books author is, and their dogs is, and the breed is,  and that breed is from the country...). This query can be performed as one query in GraphQL  But requires multiple queries and joins in a REST API.  |                                                                                                                                                                                    |
|                                                                                                                                                           |     |                                                                                                                                                                                                                                                                                                                                                  | GraphQL queries are not effectively serverside cached?   Eg. You request {name, age} for student with ID 123, this will be cached differently as {name} for student with ID 123.   |
|                                                                                                                                                           |     |                                                                                                                                                                                                                                                                                                                                                  |                                                                                                                                                                                    |


## Feedback Questions

### What questions did we miss, that we should have asked? 

**Ask if:** It's a more senior/leadership focused role and/or they seem like a confident candidate who would enjoy answering it.  

**Purpose:** This is a fun question for the candidate, and it can help improve your interview process. 

For a (good) senior developer I would expect to see them offering opinions on interview process and so a disinterest in the question may be a red flag. 
