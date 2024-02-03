file://<WORKSPACE>/jobs/java/spark-job/src/main/java/com/sztabers/spark/WordCountJob.java
### java.util.NoSuchElementException: next on empty iterator

occurred in the presentation compiler.

action parameters:
offset: 110
uri: file://<WORKSPACE>/jobs/java/spark-job/src/main/java/com/sztabers/spark/WordCountJob.java
text:
```scala
package com.sztabers.spark;

/**
 * Hello world!
 *
 */
public class App 
{
    public static void WordCountJo@@( String[] args )
    {
        System.out.println( "Hello World!" );
    }
}

```



#### Error stacktrace:

```
scala.collection.Iterator$$anon$19.next(Iterator.scala:973)
	scala.collection.Iterator$$anon$19.next(Iterator.scala:971)
	scala.collection.mutable.MutationTracker$CheckedIterator.next(MutationTracker.scala:76)
	scala.collection.IterableOps.head(Iterable.scala:222)
	scala.collection.IterableOps.head$(Iterable.scala:222)
	scala.collection.AbstractIterable.head(Iterable.scala:933)
	dotty.tools.dotc.interactive.InteractiveDriver.run(InteractiveDriver.scala:168)
	scala.meta.internal.pc.MetalsDriver.run(MetalsDriver.scala:45)
	scala.meta.internal.pc.completions.CompletionProvider.completions(CompletionProvider.scala:46)
	scala.meta.internal.pc.ScalaPresentationCompiler.complete$$anonfun$1(ScalaPresentationCompiler.scala:136)
```
#### Short summary: 

java.util.NoSuchElementException: next on empty iterator