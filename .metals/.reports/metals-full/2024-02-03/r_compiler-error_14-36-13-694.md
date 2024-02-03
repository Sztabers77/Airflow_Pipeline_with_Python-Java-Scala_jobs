file://<WORKSPACE>/jobs/java/spark-job/src/main/java/com/sztabers/spark/WordCountJob.java
### java.util.NoSuchElementException: next on empty iterator

occurred in the presentation compiler.

action parameters:
offset: 347
uri: file://<WORKSPACE>/jobs/java/spark-job/src/main/java/com/sztabers/spark/WordCountJob.java
text:
```scala
package com.airscholar.spark;

import org.apache.spark.SparkConf;
import org.apache.spark.api.java.JavaPairRDD;
import org.apache.spark.api.java.JavaRDD;
import org.apache.spark.api.java.JavaSparkContext;
import scala.Tuple2;

import java.util.Arrays;
import java.util.List;
import java.util.regex.Pattern;


public class WordCountJob
{
	private s@@tatic final Pattern SPACE = Pattern.compile(" ");

    public static void main( String[] args )
    {
        SparkConf conf = new SparkConf().setAppName("Word Count Job").setMaster("local");
		JavaSparkContext sc = new JavaSparkContext(conf);

		//hardcoded text
		String text = "hello world hello spark hello docker hello Yusuf hello java";
		List<String> data = Arrays.asList(text.split(" "));

		//parallelize the data
		JavaRDD<String> lines = sc.parallelize(data);

		//split into words and perform the word count
		JavaPairRDD<String, Integer> counts = lines
							.flatMap(s -> Arrays.asList(SPACE.split(s)).iterator())
							.mapToPair(word-> new Tuple2<>(word, 1))
							.reduceByKey(Integer::sum);

		//collect and print the word count results
		List<Tuple2<String, Integer>> output = counts.collect();

		for(Tuple2<?, ?> tuple: output) {
			System.out.println(tuple._1() + ": " + tuple._2());
		}

		//close the context
		sc.close();
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
	scala.meta.internal.pc.HoverProvider$.hover(HoverProvider.scala:34)
	scala.meta.internal.pc.ScalaPresentationCompiler.hover$$anonfun$1(ScalaPresentationCompiler.scala:342)
```
#### Short summary: 

java.util.NoSuchElementException: next on empty iterator