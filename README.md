# ScalaCoursera

Cheat sheet for Scala is available here - http://docs.scala-lang.org/cheatsheets/

ROUGH NOTES:-

1. There is no need of an explicit return statement - methods will automatically return what the last statement returns

2. Method definitions have parameter types to the right of the parameter names

3. Class definitions also have paramaters, they serve as constructors

4. Objects can be directly defined - https://dzone.com/articles/brief-overview-object-scala

5. IMPORTANT - Case statements are very powerful, they can work on lists, check if lists are empty, have a single element, have a head and a tail etc. These can serve as powerful tool for expressing recursion.

6. IMPORTANT - Case statements can also explore object content - but those classes have to be "CASE" classes. This can also serve as a powerful tool for recursive processes like Inorder traversal.

6.5. There can be wildcards or variables within pattern matching

    def weight(tree: CodeTree): Int = tree match {

	case Leaf(_,w) => w
	case Fork(l,r,_,_) =>  weight(l) + weight(r)

    }	
    
    and there can be further conditions in the LHS
    
       def decode(tree: CodeTree, bits: List[Bit]): List[Char] = {
    def decode0(tree0: CodeTree, bits0: List[Bit], accu: List[Char]): List[Char] = bits0 match {
	case Nil => tree0 match {
	    case l: Leaf => accu :+ l.char
	    case f: Fork => println("Invalid encoding!"); accu
	}
	case x :: xs => tree0 match {
	    case l: Leaf => decode0(tree, bits0, accu :+ l.char)
	    case f: Fork => decode0(if (x == 0) f.left else f.right, xs, accu)
	}
    }
    decode0(tree, bits, List())
  }  
    
  

7. In step 5, the concat operator :: is used conjunction with pattern matching. 

8. Functions can be arguments to other functions e.g.
 def until(condF:List[CodeTree] => Boolean, processF: List[CodeTree]=> List[CodeTree]): List[CodeTree] = {}
 
9. Functions can have 2 argument sets - called currying, but just seem like extension of the same.

10. Collections are supposed to be immulatble.

11. :: is different from ::: http://stackoverflow.com/questions/6566502/whats-the-difference-between-and-in-scala

12. :: is different from :+  http://stackoverflow.com/questions/15236211/whats-the-difference-between-and

13. Scala has the concept of pairs () and they can be subject to pattern matching too.

14. List methods are - head, init, tail last, reverse, contains, indexOf, ++, sortWith

15. Vector - is a list that is implemented as a 32 child tree

16. Other methods covered - Range, Zip - Used to create pairs out of lists, Unzip

17. For (s) yield e, filter, map (method not collection) applies method to all elements of an array, flatMap

18. Set is similar to java - unique, has no order.

19. Map - key value pair, is supposed to be both function and iterable.

20. groupBy - http://alvinalexander.com/scala/how-to-split-sequences-subsets-groupby-partition-scala-cookbook

21. Any collection of pairs can be transformed into a `Map` using the `toMap` method. Similarly, any `Map` can be transformed into a `List` of pairs using the `toList` method.
