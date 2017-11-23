#abstract
#introduction


#Background
##encore
##ADTs
Algebraic data types (ADTs) is used to define composite data.  Data structures can in type theory be described in terms of products, sums and recursive types. This leads to an algebra for describing data structures (hence Algebraic Data Types). Such data types are common in functional languages, such as ML or Haskell.  Robert Harper describes Producs of types in the book 'Practical Foundations for Programming Languages' as the following: "The binary product of two types consists of ordered pairs of values, one from each type in the order speciﬁed. The associated eliminatory forms are projections, which select the first and second component of a pair. The nullary product, or unit, type consists solely of the unique “null tuple” of no values, and has no associated eliminatory form."

Sums of products can be seen as the choice of two or more variants of a data structure, both producs and sums can be seen in the following example of a polymorphic binary tree.  Here Tree is the name of the type and Nil and Branch are constructors that are used to create new instances of type Tree and t is a type variable.  The type Tree is also recursive as it is defined in terms of itself.

Tree t = Nil | Branch t (Tree t) (Tree t)
(<Fig x> In some made up language)
###In functional languages (this section has more become something like 'ADTs vs Classes' :/ )
In most functional languages there are no objects, so the primary method of defining composite data is with Algebraic Data Types. Though ADTs is in no way equivalent with classes. Some of the major differences is mutability.  Instance variables in a class is generally mutable while values in an ADT is not.  Another distinction is that Algebraic Data Types allow for both sums and products while classes only allows for products.  ADTs also expose their insides to the world in a way that classes do not.  This allows the programmer to perform pattern matching on an Algebraic Data Type.  Pattern matching on types is also a feature that is mostly found in Functional languages and is critical to work with ADTs an effective manner.

###In imperative/OO languages
While Algebraic Data Types is mostly found in functional languages there are examples of imperative languages
that features them. Perhaps most notably in Scala.
Algebraic Data Types in Scala comes in the form of Variant types. A binary tree in Scala could have the following definition:
  sealed trait Tree[+T]
  case object Nil extends Tree[Nothing]
  case class Branch[T](value: T , left: Tree[T], right: Tree[T]) extends Tree[T]
Noteworthy here is that the ADT is defined in terms of a Trait and classes extending the trait.
A sealed trait is a special kind of trait that can only be extended in the same file as it is defined.
A case class is mostly a normal class with a few differences such as its being immutable.
Case classes can also be used in pattern matching:
tree match {
    case Node(value, left, right) => Foo()
    case EmptyTree()  => Bar()
  }

One can easily see the similarities of this implementation and the one in <fig x>.
Here Tree is the new type, Nil and Branch could be seen as constructors for the type Tree.
Using the scheme of traits and classes to create something that looks and behaves a lot like an ADT
Scala have created objects and are both sum and product types, and the fact that case classes can be used
in destructured pattern matching allows for allows for programming patterns normally only found in functional languages.
#Problem -- encoding is bad
#Design
##Suggested Syntax
##Behaviour
#Implementation
## Implementation via desugaring
## Pattern matching optimizatiotn

#Evaluation and discussion
##Expressive power
###Some cool example
##Performance
###Benchmark

#Conclusion and Future work


#Källor:
http://www.cs.cmu.edu/~rwh/pfpl.html
