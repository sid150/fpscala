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