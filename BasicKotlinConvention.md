#BASIC KOTLIN CONVENTION

## Variables

* Write in **lowerCamelCase**

* Single character value must be avoided, except for temporary looping variables.

**GOOD**

~~~kotlin
var studentName: String
~~~

**BAD**

~~~kotlin
var StudentName: String
~~~

## Type Inference

* Type inference should be preferred where possible to explicitly decleard types

**GOOD**

~~~kotlin
val student = Student()
val age = 21
~~~

**BAD**

~~~kotlin
val student: Student = Student()
val age: Int = 21
~~~

## Strings

* Always prefer string interpolation if possible.

**GOOD**

~~~kotlin
val name = "${user.firstName} ${user.lastName}"
~~~

**BAD**

~~~kotlin
val name = user.firstName + " " + user.lastName
~~~

## If Expression

**GOOD**

~~~kotlin
if (someTest) {
...
} else {
...
}
~~~

**BAD**

~~~kotlin
if (someTest) {
...
}
else {
...
}
~~~

## When Expression

* Unlike `switch` statements in Java, `when` statements do not fall through. Separate cases using commas if they should be handled the same way. Always include the else case.

**GOOD**

~~~kotlin
when (Input) {
    1, 2 -> doSomethingForCaseOneOrTwo()
    3 -> doSomethingForCaseThree()
    else -> print("No case satisfied")
}
~~~

**BAD**

~~~kotlin
when (Input) {
    1 -> doSomeThingForCaseOne()
    2 -> doSomeThingForCaseOneOrTwo()
    3 -> doSomeThingForCaseThree()
}
~~~

## Smart Cast

**GOOD**

~~~kotlin
dog as? Animal ?: throw IllegalArgumentException("not Animal!")
dog.foo()
~~~

**BAD**

~~~kotlin
if (dog !is Animal) {
    throw IllegalArgumentException("not Animal!")
}
dog.foo()
~~~

## Collections

* Should be used `MutableList` if that `List` change data in future
* If you create the list to read only, you can use `List` instead of using `MutableList`

**GOOD**

~~~kotlin
val students: MutableList<Int> = ArrayList()
~~~

**BAD**

~~~kotlin
val students :List<Int> = ArrayList()
~~~

## Equality

* Should be used equal instead of "==" operator

**GOOD**

~~~kotlin
a.equal(b)
!a.equal(b)
~~~

**BAD**

~~~kotlin
a == b
a != b
~~~

## This Expression

* Don't use `this@label` if compiler uderstood that `this`

**GOOD**

~~~kotlin
data class Test(var name: String) {

    fun showName(name: String) {
        this.name = name
    }
}
~~~

**BAD**

~~~kotlin
data class Test(var name: String) {

    fun showName(name: String) {
        this@Test.name = name
    }
}
~~~