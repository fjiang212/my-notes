# Creating and Destroying Objects
Item 1: Consider static factory methods instead of constructors
Item 2: Consider a builder when faced with many constructor parameters
Item 3: Enforce the singleton property with a private constructor or an enum
type
Item 4: Enforce noninstantiability with a private constructor
Item 5: Prefer dependency injection to hardwiring resources
Item 6: Avoid creating unnecessary objects
Item 7: Eliminate obsolete object references
Item 8: Avoid finalizers and cleaners
Item 9: Prefer try-with-resources to try-finally
#  Methods Common to All Objects
Item 10: Obey the general contract when overriding equals
Item 11: Always override hashCode when you override equals
Item 12: Always override toString
Item 13: Override clone judiciously
Item 14: Consider implementing Comparable
#  Classes and Interfaces
Item 15: Minimize the accessibility of classes and members
Item 16: In public classes, use accessor methods, not public fields
Item 17: Minimize mutability
Item 18: Favor composition over inheritance
Item 19: Design and document for inheritance or else prohibit it
Item 20: Prefer interfaces to abstract classes
Item 21: Design interfaces for posterity
Item 22: Use interfaces only to define types
Item 23: Prefer class hierarchies to tagged classes
Item 24: Favor static member classes over nonstatic
Item 25: Limit source files to a single top-level class
#  Generics
Item 26: Don’t use raw types
Item 27: Eliminate unchecked warnings
Item 28: Prefer lists to arrays
Item 29: Favor generic types
Item 30: Favor generic methods
Item 31: Use bounded wildcards to increase API flexibility
Item 32: Combine generics and varargs judiciously
Item 33: Consider typesafe heterogeneous containers
#  Enums and Annotations
Item 34: Use enums instead of int constants
Item 35: Use instance fields instead of ordinals
Item 36: Use EnumSet instead of bit fields
Item 37: Use EnumMap instead of ordinal indexing
Item 38: Emulate extensible enums with interfaces
Item 39: Prefer annotations to naming patterns
Item 40: Consistently use the Override annotation
# Lambdas and Streams
## Item 42: Prefer lambdas to anonymous classes
## Item 43: Prefer method references to lambdas
## Item 44: Favor the use of standard functional interfaces
## Item 45: Use streams judiciously
## Item 46: Prefer side-effect-free functions in streams
## Item 47: Prefer Collection to Stream as a return type
## Item 48: Use caution when making streams parallel
#  Methods
Item 49: Check parameters for validity
Item 50: Make defensive copies when needed
Item 51: Design method signatures carefully
Item 52: Use overloading judiciously
Item 53: Use varargs judiciously
