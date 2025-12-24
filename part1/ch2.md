```scala
object MyModule{

  def abs(n: Int):Int = {
    if (n<0) -n
    else n
  }
  def fib(a: Int):Int = {
    if (a<=1) 1
    else fib(a-1) + fib(a-2)
  }
  private def formatAbs(x: Int) ={
    val msg = "The absolute value of %d is %d"
    msg.format(x,abs(x))
  }
  private def find_fib(n: Int) ={
    val fibo= "The fibonacci sequence of %d terms is %d"
    fibo.format(n,fib(n))
  }
  def main (args:Array[String]): Unit = 
  //0 1 1 2 3 5
    println(find_fib(1))
}
```
Higher order function - accepts a function as an argument

Tail position - when a portion of the code just returns some value, does not process anything else. When there is no additional work left to be done (termination of loop)



Ex1
```scala
object MyModule{

  def fib_nth(n: Int):Int = {
   def start (n: Int,a: Int,b: Int): Int ={
      if (n == 1) a // tail recursive
      else start(n-1,b,a+b)
   }
   start(n,0,1)
  }

  
  private def find_fib(n: Int) ={
    val fibo= "The fibonacci sequence of %d st term is %d"
    fibo.format(n,fib_nth(n))
  }
  
  def main (args:Array[String]): Unit = 
  //0 1 1 2 3 5 8 13 21 34
    println(find_fib(10))
}
```
```scala
//monomorphic only one type of data (Int in this cases)
object MyModule{

  def fib_nth(n: Int):Int = {
   def start (n: Int,a: Int,b: Int): Int ={
      if (n == 1) a // tail recursive
      else start(n-1,b,a+b)
   }
   start(n,0,1)
  }

  def fact (n:Int):Int = {
    def loop(n: Int,prod: Int): Int = {
      if (n<=0) prod
      else loop(n-1,prod*(n))
    }
    loop(n,1)
  }
  
  private def result(name: String, n: Int, f:Int => Int) ={
    val msg= "The %s of %d is %d"
    msg.format(name,n,f(n))
  }
  
  def main (args:Array[String]): Unit = 
  //0 1 1 2 3 5 8 13 21 34
    println(result("nth fib",7,fib_nth))
}
```

Ex2 

```scala
object MyModule{

  def isSorted[A](as: Array[A],ordered: (A,A)=>Boolean):Boolean ={
    def loop(n: Int): Boolean ={
      if (n>=as.length) true
      else if (!ordered(as(n-1),as(n))) false
      else loop(n+1)
    }
    loop(1)
  }
  def result[A](arr: Array[A],ordered:(A,A)=>Boolean) :String= {
    if (isSorted(arr,ordered)) "Array is sorted"
    else "Array is not sorted"
  }
  def main (args:Array[String]): Unit = 
    val numbers = Array(1, 2, 3, 4, 5)
    println(result(numbers,(a:Int,b:Int)=>a<b))//checks ascending order for array
    
}
```