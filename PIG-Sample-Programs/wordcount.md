##Q) How to find the number of occurrences of the words in a file using the pig script?

You can find the famous word count example written in map reduce programs in apache website. Here we will write a simple pig script for the word count problem.

The following pig script finds the number of times a word repeated in  a file:

Word Count Example Using Pig Script:

lines = LOAD '/user/hadoop/HDFS_File.txt' AS (line:chararray);
words = FOREACH lines GENERATE FLATTEN(TOKENIZE(line)) as word;
grouped = GROUP words BY word;
wordcount = FOREACH grouped GENERATE group, COUNT(words);
DUMP wordcount;


The above pig script, first splits each line into words using the TOKENIZE operator. The tokenize function creates a bag of words. Using the FLATTEN function, the bag is converted into a tuple. In the third statement, the words are grouped together so that the count can be computed which is done in fourth statement.

You can see just with 5 lines of pig program, we have solved the word count problem very easily.

Please comment here if you have any problems in running the above pig script and you are not getting expected word count. 
