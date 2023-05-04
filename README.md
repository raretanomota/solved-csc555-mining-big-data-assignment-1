Download Link: https://assignmentchef.com/product/solved-csc555-mining-big-data-assignment-1
<br>
Suggested reading: <em>Mining of Massive Datasets</em>: Chapter 1, Chapter 2 (sections 2.1, 2.1 only). <em>Hadoop: The Definitive Guide</em>: Appendix A (available on D2L)

Supplemental document <strong>UsingAmazonAWS.doc</strong>.

<h1>Part 1</h1>

<ol>

 <li>Compute (you can use any tool you wish, but if you do not know to perform this computation, please talk to me about prerequisite courses):</li>

</ol>

2<sup>10</sup>

4<sup>10</sup>

8<sup>4</sup>

842 MOD 100 (MOD is the modulo operator, a.k.a. the remainder)

837 MOD 20

15 MOD 37

37 MOD 15




<ol>

 <li>Given vectors V1 = (1, 2, 3) and V2 = (2, 1, 3) and a 3×3 matrix M = [(2, 1, 3), (1, 2, 1), (1, 0, 2)], compute:</li>

</ol>

V2 – V1

V2 + V1

|V1| (vector length, not the number of dimensions)

|V2|

M * V1 (matrix times vector, transpose it as necessary)

M * M (or M<sup>2</sup>)

M<sup>3</sup>




<ol>

 <li>Suppose we are flipping a coin with Head (H) and Tail (T) sides. The coin is <u>not</u> balanced with 0.6 probability of H coming up (and 0.4 of T). Compute the probabilities of getting:</li>

</ol>

HTTT

THTT

Exactly 1 Head out of a sequence of 4 coin flips.

Exactly 1 Tail out of sequence of 4 coin flips.




<ol>

 <li>Consider a database schema consisting of two tables, Employee (<u>ID</u>, Name, Address), Project (<u>PID</u>, Name, Deadline), Assign(<u>EID</u>, <u>PID</u>, Date). Assign.EID is a foreign key referencing employee’s ID and Assign.PID is a foreign key referencing the project.</li>

</ol>

Write SQL queries for:

<ol>

 <li>Find unassigned projects (PID and Name of the project).</li>

</ol>




<ol>

 <li>Find employees that are assigned to more than 3 projects.</li>

</ol>




<ul>

 <li>Find all projects that have fewer than 3 employees assigned to them (note that this should include 2, 1 and 0 in order to be correct – if you )</li>

</ul>







<ol>

 <li>Mining of Massive Datasets, Exercise 1.3.3</li>

</ol>




<u>Justify your answer</u> – simply naming a constant will not provide credit.




<ol>

 <li>Describe how you would implement a MapReduce job consisting of Map and Reduce description. You <u>do not</u> have to write code or even pseudo-code. Just describe, in your own words, what the Map and Reduce tasks are going to do.  Map task reads the input file and produces (key, value) pairs.  Reduce task takes a list of (key, value) pairs for each key and combines all values for each key.</li>

</ol>

Please remember that Map operates on individual blocks and Reduce on individual keys with a set of values. Thus, for Mapper you need to state what your code does given a block of data (i.e., for each block, not for the whole file) and for Reduce you need to state what your reducer does for each key (without being able to see other keys).

For a data file that contains the following columns: (ID, First, Last, Grade)




<ol>

 <li>Find the average of all grades in the input file, i.e.,</li>

</ol>

<strong>SELECT AVG(Grade) FROM Student</strong>.

(hint: the number of distinct keys used should match the number of results you expect)




<ol>

 <li>For each first name, find the GPA (grade point average) of each student, i.e.,</li>

</ol>

<strong>SELECT First, AVG(Grade) FROM Student GROUP BY First</strong>.




<ul>

 <li>For each full student name, find the best grade, i.e.,</li>

</ul>

<strong>SELECT First, Last, MAX(Grade) FROM Student GROUP BY First, Last</strong>.




<h1>Part 2: Linux Intro</h1>




This part of the assignment will serve as an introduction to Linux. Make sure you go through the steps below and submit screenshots where requested – submit the entire screenshot of a command terminal.




Use at least a t2.small instance or Hadoop may not run properly with insufficient memory.

All Linux commands are in Berlin Sans FB. Do not type the “$” symbol. The “$” represents the prompt “[<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="5c393f6e71292f392e1c352c7124242471242471242471242424">[email protected]</a> ~] $ ” in your particular Linux instance.




<ol>

 <li><strong>Login to your Amazon EC2 Instance </strong>(NOTE: <u>instructions on how to create a new instance and log in to it are provided in a separate file,</u> UsingAmazonAWS.doc)</li>

</ol>




Connect to your instance through Putty.







Your instance should look like as the following image:










<ol>

 <li><strong>Create a text file.</strong></li>

</ol>

Instructions for 3 different text editors are provided below. You only need to choose <u>one editor</u> that you prefer. <strong>nano</strong> is a more basic text editor, and is much easier to start. <strong>vim</strong> and <strong>emacs</strong> are more advanced and rely on keyboard shortcuts quite a bit and thus have a steeper learning curve.

<ul>

 <li><strong> Tip</strong>: To paste into Linux terminal you can use <u>right-click</u>. To copy from the Linux terminal, you only need to highlight the text that you want to copy with your mouse. Also please remember that Linux is <u>case-sensitive</u>, which means <strong>Nano</strong> and <strong>nano</strong> are not equivalent.</li>

</ul>




Nano Instructions(Option 1):




$ nano myfile.txt




Type something into the file: “This is my text file for CSC555.”

Save changes: Ctrl-o and hit Enter.

Exit: Ctrl-x




Emacs Instructions(Option 2):




You will need to install emacs.

$ sudo yum install emacs

Type “y” when asked if this is OK to install.




$ emacs myfile.txt

Type something into the file: “This is my text file for CSC555.”

Save changes: Ctrl-x, Ctrl-s

Exit: Ctrl-x Ctrl-z




Vim Instructions(Option 3):

<ul>

 <li>NOTE: When <strong>vim</strong> opens, you are in <em>command</em> mode. Any key you enter will be bound to a command instead of inserted into the file. To enter <em>insert </em>mode press the key “i”. To save a file or exit you will need to hit Esc to get back into <em>command</em> mode.</li>

</ul>




$ vim myfile.txt

Type “i” to enter <em>insert</em> mode

Type something into the file: “This is my text file for CSC555.”

Save changes: hit Esc to enter <em>command</em> mode then type “:w”

Exit: (still in <em>command</em> mode) type “:x”




Confirm your file has been saved by listing the files in the working directory.

$ ls

You should see your file.

Display the contents of the file on the screen.

$ cat myfile.txt




Your file contents should be printed to the terminal.




<ul>

 <li><strong> Tip</strong>: Linux will fill in partially typed commands if you hit Tab.</li>

</ul>

$cat myfi

Hit Tab and “myfi” should be completed to “myfile.txt”. If there are multiple completion options, hit Tab twice and a list of all possible completions will be printed. This also

applies to commands themselves, i.e. you can type in ca and see all possible commands that begin with ca.




<ol start="2">

 <li><strong> Copy your file.</strong></li>

</ol>

<strong> </strong>

Make a copy.

$ cp myfile.txt mycopy.txt

Confirm this file has been created by listing the files in the working directory.

Edit this file so it contains different text than the original file using the text editor instructions, and confirm your changes by displaying the contents of the file on the screen.

<strong> </strong>

<strong>SUBMIT: </strong>Take a screen shot of the <u>contents</u> of your copied file displayed on the terminal screen.




<ol start="3">

 <li><strong> Delete a file</strong></li>

</ol>

<strong> </strong>

Make a copy to delete.

$ cp myfile.txt filetodelete.txt

$ ls




Remove the file.

$ rm filetodelete.txt

$ ls




<ol start="4">

 <li><strong> Create a directory to put your files.</strong></li>

</ol>

<strong> </strong>

Make a directory.

$mkdir CSC555




Change the current directory to your new directory.

$cd CSC555




Print your current working directory

$pwd




<ol start="5">

 <li><strong> Move your files to your new directory.</strong></li>

</ol>

<strong> </strong>

Return to your home directory.

$cd

OR

$cd ..

OR

$ cd /home/ec2-user/




<ul>

 <li>NOTE: cd will always take you to your home directory. cd .. will move you up one directory level (to the parent). Your home directory is “/home/[user name]”, /home/ec2-user in our case</li>

</ul>




Move your files to your new directory.




$ mv myfile.txt CSC555/

$ mv mycopy.txt CSC555/




Change the current directory to CSC555 and list the files in this directory.

<strong> </strong>

<strong>SUBMIT:</strong> Take a screen shot of the files listed in the CSC555 directory.




<ol start="6">

 <li><strong> Zip and Unzip your files.</strong></li>

</ol>

<strong> </strong>

Zip the files.

$ zip myzipfile mycopy.txt myfile.txt

OR

$ zip myzipfile *




<ul>

 <li>NOTE: * is the wildcard symbol that matches <u>everything</u> in current directory. If there should be any additional files in the current directory, they will also be placed into the zip archive. Wildcard can also be used to match files selectively. For example zip myzipfile my* will zip-up all files beginning with “my” in the current directory.</li>

</ul>




Move your zip file to your home directory.

$ mv myzipfile.zip /home/ec2-user/




Return to your home directory.

Extract the files.

$ unzip myzipfile.zip




<strong>SUBMIT:</strong> Take a screen shot of the screen after this command.




<ol start="7">

 <li><strong> Remove your CSC555 directory.</strong></li>

</ol>

<strong> </strong>

<ul>

 <li><strong>Warning</strong>: Executing “rm -rf” has the potential to delete ALL files in a given directory, including sub-directories (“r” stands for recursive). You should use this command very carefully.</li>

</ul>

Delete your CSC555 directory.

$ rm -rf CSC555/




<ol start="8">

 <li><strong> Download a file from the web.</strong></li>

</ol>

<strong> </strong>

Download the script for Monty Python and the Holy Grail.

$ wget <a href="http://www.textfiles.com/media/SCRIPTS/grail">http://www.textfiles.com/media/SCRIPTS/grail</a>




The file should be saved as “grail” by default.




<ol start="9">

 <li><strong> ls formats</strong></li>

</ol>

<strong> </strong>

List all contents of the current directory in long list format.

<ul>

 <li><strong>Note</strong>: the option following “ls” is the character “l”; not “one”.</li>

</ul>

$ ls -l




The 1<sup>st</sup> column gives information regarding file permissions (which we will discuss in more detail later). For now, note that the first character of the 10 total will be “-“ for normal files and “d” for directories. The 2<sup>nd</sup> Column is the number of links to the file. The 3<sup>rd</sup> and 4<sup>th</sup> columns are the owner and the group of the file. The 5<sup>th</sup> column displays the size of the file in bytes. The 6<sup>th</sup> column is the date and time the file was last modified. The 7<sup>th</sup> column is the file or directory name.




List all contents of the current directory in long list and human readable formats. “-h” will put large files in more readable units than bytes.

$ ls -lh




<strong>SUBMIT:</strong> The size of the grail file.




<ol start="10">

 <li><strong> More on viewing files.</strong></li>

</ol>

<strong> </strong>

If you issue “cat grail”, the contents of grail will be printed. However, this file is too large to fit on the screen.




Show the grail file one page at a time.

$ more grail

Hit the spacebar to go to the next page. Type “b” to go page up, hit “space” key to go page down. Type “q” to quit.




OR




$ less grail

<em>Less</em> has more options than <em>more</em> (“<em>less</em> is more and <em>more</em> is less”). You can now use the keyboard Arrows and Page Up/Down to scroll. You can type “h” for help, which will display additional options.




View the line numbers in the grail file. The <em>cat</em> command has the -n option, which prints line numbers, but you may also want to use <em>more</em> to view the file one page at a time. A solution is to <em>pipe</em> the output from <em>cat</em> to <em>more</em>. A <em>pipe</em> redirects the output from one program to another program for further processing, and it is represented with “|”.




$ cat -n grail | more




Redirect the standard output (stdout) of a command.

$ cat myfile.txt &gt; redirect1.txt

$ ls -lh &gt; redirect2.txt




Append the stdout to a file.

$ cat mycopy.txt &gt;&gt; myfile.txt

mycopy.txt will be appended to myfile.txt.




<ul>

 <li><strong>Note</strong>: “cat mycopy.txt &gt; myfile.txt” will <u>overwrite</u> myfile.txt with the contents output by “cat mycopy.txt”. Thus using &gt;&gt; is crucial if you want to preserve the existing file contents.</li>

</ul>




<ol start="11">

 <li><strong> Change access permissions to objects with the <em>change mode</em> command.</strong></li>

</ol>

<strong> </strong>

The following represent roles:

u – user, g – group, o – others, a – all




The following represent permissions:

r – read, w – write, x – execute




Remove the read permission for your user on a file.

$ chmod u-r myfile.txt

Try to read this file. You should receive a “permission denied” message because you are the user who owns the file.




<strong>SUBMIT:</strong> The screenshot of the permission denied error




Give your user read permission on a file. Use the same file you removed the read permission from.

$ chmod u+r myfile.txt

You should now be able to read this file again.




<ol start="12">

 <li><strong> Python examples </strong></li>

</ol>




Install Python if it is not available on your machine.




$ sudo yum install python




Create a Python file. These instructions will use Emacs as a text editor, but you can still chose the text editor you want.




$ emacs lucky.py

(Write a simple Python program)

print “*”*22

print “My Lucky Numbers”.rjust(20)

print “*”*22




for i in range(10):

lucky_nbr = (i + 1)*2

print “My lucky number is %s!” % lucky_nbr




Run your Python program.

$ python lucky.py




Redirect your output to a file

$ python lucky.py &gt; lucky.txt




Pipe the stdout from lucky.py to another Python program that will replace “is” with “was”.

$ emacs was.py




import sys




for line in sys.stdin:

print line.replace(“is”, “was”)




$ python lucky.py | python was.py




Write python code to read a text file (you can use myfile.txt) and output “word 1 True” if the word had already occurred in that file before or “word 1 False” if this is the first time you encounter this word.




<strong>SUBMIT:</strong> The screen output from running your python code <u>and a copy of your python code</u>. Homework submissions without code will receive no credit.




<h1>Part 3: Lab</h1>

For this part of the assignment, you will run wordcount on a single-node Hadoop instance.  I am going to provide detailed instructions to help you get Hadoop running. The instructions are following Hadoop: The Definitive Guide instructions presented in Appendix A: Installing Apache Hadoop.




You can download 2.6.4 from here. You can copy-paste these commands (right-click in PuTTy to paste, but please watch out for error messages and run commands one by one)

Install ant to list java processes

sudo yum install ant




(wget command stands for “web get” and lets you download files to your instance from a URL link)

wget <a href="http://rasinsrv07.cstcis.cti.depaul.edu/CSC555/hadoop-2.6.4.tar.gz">http://rasinsrv07.cstcis.cti.depaul.edu/CSC555/hadoop-2.6.4.tar.gz</a>







(unpack the archive)

tar xzf hadoop-2<em>.</em>6.4.tar.gz




Modify the conf/hadoop-env.sh to add to it the JAVA_HOME configuration

You can open it by running (using nano or your favorite editor instead of nano).

nano hadoop-2.6.4/etc/hadoop/hadoop-env.sh

Note that the # comments out the line, so you would comment out the original JAVA_HOME line replacing it by the new one as below.

<strong> </strong>

<strong>NOTE</strong>: you would need to determine the correct Java configuration line by executing the following (underlined) command

[<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="482d2b7a653d3b2d3a08213865797f7a657b7965797e657e7b">[email protected]</a> ~]$ <strong><u>readlink -f $(which java)</u></strong>

which will output:

/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.191.b12-0.amzn2.x86_64/jre/bin/java




In my case, Java home is at (remove the bin/java from the output above):

<strong>/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.191.b12-0.amzn2.x86_64/jre/</strong>







modify the .bashrc file to add these two lines:

export HADOOP_HOME=~/hadoop-2.6.4

export PATH=$PATH:$HADOOP_HOME/bin:$HADOOP_HOME/sbin




.bashrc file contains environment settings to be configured automatically on each login. You can open the .bashrc file by running

nano ~/.bashrc







To immediately refresh the settings (that will be <u>automatic on next login</u>), run

source ~/.bashrc




Next, follow the instructions for Pseudodistributed Mode for all 4 files.




(to edit the first config file)

nano hadoop-2.6.4/etc/hadoop/core-site.xml




Make sure you paste the settings between the &lt;configuration&gt; and &lt;/configuration&gt; tags, like in the screenshot below. NOTE: The screenshot below is only one of the 4 files, all files are different. The contents of each file are described in the <strong>Appendix A</strong> in the Hadoop book, the relevant appendix is also included with the homework assignment. I am also including a .txt file (HadoopConfigurationText) so that it is easier to copy-paste.







nano hadoop-2.6.4/etc/hadoop/hdfs-site.xml

(mapred-site.xml file is not there, run the following single line command to create it by copying from template. Then you can edit it as other files.)

<u>cp hadoop-2.6.4/etc/hadoop/mapred-site.xml.template  hadoop-2.6.4/etc/hadoop/mapred-site.xml</u>

nano hadoop-2.6.4/etc/hadoop/mapred-site.xml

nano hadoop-2.6.4/etc/hadoop/yarn-site.xml




To enable passwordless ssh access (we will discuss SSH and public/private keys in class), run these commands:

ssh-keygen -t rsa -P ” -f ~/.ssh/id_rsa

cat ~/.ssh/id_rsa.pub &gt;&gt; ~/.ssh/authorized_keys




test by running (and confirming yes to a one-time warning)

ssh localhost

exit




Format HDFS (i.e., first time initialize)




hdfs namenode -format

<strong> </strong>

Start HDFS, Hadoop and history server (answer a 1-time yes if you asked about host authenticity)

<strong> </strong>

start-dfs.sh

start-yarn.sh

mr-jobhistory-daemon.sh start historyserver




Verify if everything is running:

jps




(NameNode and DataNode are responsible for HDFS management; NodeManager and ResourceManager are serving the function similar to JobTracker and TaskTracker. We will discuss function of all of those on Thursday.)




Create a destination directory

hadoop fs -mkdir /data

Download a large text file using




wget <a href="http://rasinsrv07.cstcis.cti.depaul.edu/CSC555/psd7003.xml%20">http://rasinsrv07.cstcis.cti.depaul.edu/CSC555/bioproject.xml </a>




Copy the file to HDFS for processing




hadoop fs -put bioproject.xml /data/




(you can optimally verify that the file was uploaded to HDFS by hadoop fs -ls /data)

<strong><u>Submit a screenshot of this command</u></strong>




Run word count on the downloaded text file, using the time command to determine the total runtime of the MapReduce job.   You can use the following (single-line!) command. This invokes the wordcount example built into the example jar file, supplying /data/bioproject.xml as the input and /data/wordcount1 as the output directory. Please remember this is <u>one command</u>, if you do not paste it as a single line, it will not work.




time hadoop jar hadoop-2.6.4/share/hadoop/mapreduce/hadoop-mapreduce-examples-2.6.4.jar  wordcount /data/bioproject.xml /data/wordcount1




Report the time that the job took to execute as screenshot

(this reports the size of a particular file or directory in HDFS. The output file will be named part-r-00000)

hadoop fs -du /data/wordcount1/




(Just like in Linux, the cat HDFS command will dump the output of the entire file and grep command will filter the output to all lines that matches this particular word). To determine the count of occurrences of “subarctic”, run the following command:




hadoop fs -cat /data/wordcount1/part-r-00000 | grep subarctic




It outputs the entire content of part-r-00000 file and then uses pipe | operator to filter it through grep (filter) command. If you remove the pipe and grep, you will get the entire word count content dumped to screen, similar to cat command.




Congratulations, you just finished running wordcount using Hadoop.





