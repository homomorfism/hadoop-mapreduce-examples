// This file is swapping the frequencies and words and sorted asc the frequency of words. This map-reduce job should be run after the WordCount/NewWordCount jobs.

// How to run this hadoop job:
//      $ hadoop jar SortWordCount.jar SortWordCount output/* sorted_output/*

// Example of output of the program:
//      vagrant@server-1:~/ReverseWordCount$ hdfs dfs -cat  alice_sorted_v3/part-r-00000 | tail
//      428     in
//      429     you
//      462     said
//      538     she
//      541     it
//      625     of
//      685     a
//      801     to
//      912     and
//      1804    the


import java.io.IOException;
import java.util.StringTokenizer;

import org.apache.hadoop.conf.Configuration;
import org.apache.hadoop.fs.Path;
import org.apache.hadoop.io.IntWritable;
import org.apache.hadoop.io.Text;
import org.apache.hadoop.mapreduce.Job;
import org.apache.hadoop.mapreduce.Mapper;
import org.apache.hadoop.mapreduce.Reducer;
import org.apache.hadoop.mapreduce.lib.input.FileInputFormat;
import org.apache.hadoop.mapreduce.lib.output.FileOutputFormat;
import java.util.stream.Collectors;
import java.util.StringTokenizer;
public class SortWordCount {

  public static class SortMapper
       extends Mapper<Object, Text, IntWritable, Text>{

    // private final static IntWritable one = new IntWritable(1);
    // private Text word = new Text();

    public void map(Object key, Text value, Context context
                    ) throws IOException, InterruptedException {
        StringTokenizer tok = new StringTokenizer(value.toString());
        Text text = new Text(tok.nextToken());
        Integer frequency = Integer.parseInt(tok.nextToken());
        // Text text = new Text(tok.nextToken());
        context.write(new IntWritable(frequency), text);
    }
  }

  public static void main(String[] args) throws Exception {
    Configuration conf = new Configuration();
    Job job = Job.getInstance(conf, "word count");
    job.setJarByClass(SortWordCount.class);
    job.setMapperClass(SortMapper.class);
    job.setOutputKeyClass(IntWritable.class);
    job.setOutputValueClass(Text.class);
    FileInputFormat.addInputPath(job, new Path(args[0]));
    FileOutputFormat.setOutputPath(job, new Path(args[1]));
    System.exit(job.waitForCompletion(true) ? 0 : 1);
  }
}
