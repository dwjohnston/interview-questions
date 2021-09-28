## Philosophy around conducting interviews

In my opinion, for a general developer position, it is more important to assess a candidate according to _their_ strengths, rather than 'What do we need for this position'. 

For example, say a candidate says that they don't have any experience with creating REST APIs, and part of the position requires them to create REST APIs, then there's no point in asking them questions that they themselves wouldn't profess to be experienced with. 

Now, lets say that for the position, you really _do_ need someone who is experienced with creating REST APIs, then the recruiter/hiring manager should have only sent you people who have said they're good with REST APIs, and your process if process has broken down if you are interviewing a candidate who doesn't rate themselves highly in that skill. 



## Calibration questions 

### 1. Rank your skills relative to each other. 

Make it clear that you're not asking them to compare themselves with others, but your asking 'What are you most comfortable with, and what are you less comfortable with'. 

This serves a couple of purposes: 




## JavaScript questions 

### 1. What does this code output? (`const` keyword)

```javascript
const a ="a"; 
a = "b"; 
```
**Purpose:** Tests basic JavaScript syntax knowledge. 

**Answer:** It throws an error at runtime, because the `const` keyword prevents variable reassignment. 


### 2. What does this code output? (object equality) 

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


### 3. What does this code output? (object mutation) 

```javascript 
const a = {
    a: 1
}; 

const b = a; 

b.a = "hello";. 

console.log(a);
console.log(b); 
```

**Purpose:** It tests that they that variables in JavaScript are pointers to object, and how object mutation works. 

**Answer:** They both print `{a: "hello"}` - as `a` and `b` point to the same object. 



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