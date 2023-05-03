Download Link: https://assignmentchef.com/product/solved-cs-211-assignment-2-bit-manipulation
<br>






<h1>Assignment Introduction</h1>

This assignment is designed to give you a better understanding of bits and bit manipulation. Your task is to write 3 small C bit-related programs. Your programs must follow the input-output guidelines listed in each section, with no additional or missing output.

You can assume all your input files will be in proper format as described.

<h1>Bit Introduction</h1>

Because this assignment is focused on bits, to receive credit, all parts of this assignment must only use bit operations to complete the tasks of the program. You may not use arithmetic or logic equivalents to the bit tasks being asked for.

C provides six operators for bit manipulation:

<table width="544">

 <tbody>

  <tr>

   <td width="30">&amp;</td>

   <td width="137">bitwise AND</td>

   <td width="378">The bits in the result are set to 1 if the corresponding bits in the two operands are both 1.</td>

  </tr>

  <tr>

   <td width="30">|</td>

   <td width="137">bitwise inclusive OR</td>

   <td width="378">The bits in the result are set to 1 if at least one of the corresponding bits in the two operands is 1.</td>

  </tr>

  <tr>

   <td width="30">^</td>

   <td width="137">bitwise exclusive OR</td>

   <td width="378">The bits in the result are set to 1 if exactly one of the corresponding bits in the two operands is 1.</td>

  </tr>

  <tr>

   <td width="30">&lt;&lt;</td>

   <td width="137">left shift</td>

   <td width="378">Shifts the bits of the first operand left by the number of bits specified by the second operand.</td>

  </tr>

  <tr>

   <td width="30">&gt;&gt;</td>

   <td width="137">right shift</td>

   <td width="378">Shifts the bits of the first operand right by the number of bits specified by the second operand.</td>

  </tr>

  <tr>

   <td width="30">~</td>

   <td width="137">complement</td>

   <td width="378">All 0 bits are set to 1 and 1 bits are set to 0.</td>

  </tr>

 </tbody>

</table>

For example:

<table width="633">

 <tbody>

  <tr>

   <td width="337">unsigned short x = 5 , y = 2 , z ; //in binary 5 is z = x &amp; y ; // result : 0 z = 5 | y ; // result : 7 z = 5 ˆ 1; // result : 4</td>

   <td width="295">101 and 2 is                 10</td>

  </tr>

 </tbody>

</table>

1

2

3

4

An example using shifting:

<table width="633">

 <tbody>

  <tr>

   <td width="633">unsigned                short x = 5;printf (”%u
%u
” , x <em>&lt;&lt; </em>1 , x <em>&gt;&gt; </em>1) ;</td>

  </tr>

 </tbody>

</table>

1

2

<h1>First: Bit functions (35 Points)</h1>

You have to write a program that will read a number followed by a series of bit operations from a file and perform the given operations sequentially on the number. The operations are as follows:

<strong>set(x, n, v)       </strong>sets the <em>n</em>th bit of the number <em>x </em>to <em>v </em><strong>comp(x, n)      </strong>sets the value of the <em>n</em>th bit of <em>x </em>to its complement (1 if 0 and 0 otherwise) <strong>get(x, n)     </strong>returns the value of the <em>n</em>th bit of the number <em>x</em>

The least significant bit (LSB) is considered to be index 0.

<strong>Input format: </strong>Your program will take the file name as input. The first line in the file provides the value of the number <em>x </em>to be manipulated. This number should be considered an unsigned short. The following lines will contain the operations to manipulate the number. To simplify parsing, the format of the operations will always be the command name followed by 2 numbers, separated by tabs. For the set(x, n, v) command, the value of the second input number (<em>v</em>) will always be either 0 or 1. For the comp(x, n) and get(x, n) commands the value of the second input number will always be 0 and can be ignored. Note that the changes to <em>x </em>are cumulative, rather than each instruction operating independently on the original <em>x</em>.

<strong>Output format: </strong>Your output for comp and set commands will be the resulting value of the number <em>x </em>after each operation, each on a new line. For get commands, the output should be the requested bit’s value.

<strong>Example Execution:</strong>

For example, a sample input file “file1.txt” contains the following (except the annotation comments):

<table width="391">

 <tbody>

  <tr>

   <td width="119">5</td>

   <td width="272"># x = 5</td>

  </tr>

  <tr>

   <td width="119">get          0 0</td>

   <td width="272"># get(x, 0), ignoring second value (0)</td>

  </tr>

  <tr>

   <td width="119">comp 0 0</td>

   <td width="272"># comp(x, 0), ignoring second value (0)</td>

  </tr>

  <tr>

   <td width="119">set           1 1</td>

   <td width="272"># set(x, 1, 1)</td>

  </tr>

 </tbody>

</table>

The result of the sample run is:

$ ./first file1.txt

1

4

6

<h1>Second: Bit Count functions (35 points)</h1>

In this part, you have to determine the parity of a number and the number of 1-bit pairs present in the number. Parity refers to whether a number contains an even or odd number of 1-bits. 1-bit pairs are defined by two adjacent 1’s <em>without overlap </em>with other pairs.

For example:

Number     Binary sequence      Parity      Number of pairs

7                        111                   Odd                      1

15                     1111                 Even                      2

367              101101111            Odd                      3

<strong>Input format: </strong>This program takes a single number as an argument from the command line. This number should be considered as an unsigned short.

<strong>Output format: </strong>Your program should print either “Even-Parity” if the input has an even number of 1 bits and “Odd-Parity” otherwise, followed by a tab. Your program should then print the number of 1-bit pairs present in the number followed by a new line character.

<strong>Example Execution:</strong>

$ ./second 12

Even-Parity                1

$ ./second 31

Odd-Parity                 2

<h1>Third: Bit Pattern function (30 points)</h1>

In this part, you have to determine whether a number’s bit representation is a palindrome. A palindrome is defined as a sequence that is the same both forwards and backwards.

We will be working with unsigned shorts which are 2 bytes or 16 bits. For example the number 384 has the binary sequence 0000000110000000 and is thus a palindrome while the sequence 0100100010111011 is not. Note that all values should be considered 16-bit, so while 5 is 101 in binary and looks like a palindrome, in 16 bits it’d be 0000000000000101, which is not.

You can and should use the same <strong>get(x, n) </strong>function that you created in part 1.

<strong>Input format: </strong>This program takes a single number as an argument from the command line. This number should be considered as an unsigned short.

<strong>Output format: </strong>Your program should print either “Is-Palindrome” if the input is a palindrome and “Not-Palindrome” otherwise, followed by a new line character.

<strong>Example Execution:</strong>

Some sample runs and results are:

$ ./third 5

Not-Palindrome

$ ./third 384

Is-Palindrome

$ ./third 1001

Not-Palindrome

<h1>Structure of your submission folder</h1>

All files must be included in the pa2 folder. The pa2 directory in your tar file must contain 3 subdirectories, one each for each of the parts. The name of the directories should be named first through third (in lower case). Each directory should contain a c source file, a header file (if you use it) and a Makefile. For example, the subdirectory first will contain, first.c, first.h (if you create one) and Makefile (the names are case sensitive).

pa2 first

Makefile first.c first.h (if used)

second

Makefile second.c second.h (if used) third

Makefile third.c third.h (if used)

<h1>Submission</h1>

You have to submit the assignment using Sakai. Your submission should be a tar file named pa2.tar. To create this file, put everything that you are submitting into a directory (folder) named pa2. Then, cd into the directory containing pa2 (that is, pa2’s parent directory) and run the following command:

tar cvf pa2.tar pa2

To check that you have correctly created the tar file, you should copy it (pa2.tar) into an empty directory and run the following command:

tar xvf pa2.tar

This should create a directory named pa2 in the (previously) empty directory.

The pa2 directory in your tar file must contain 3 subdirectories, one each for each of the parts. The name of the directories should be named first through third (in lower case). Each directory should contain a C source file, a header file (if necessary) and a make file. For example, the subdirectory first will contain, first.c, first.h and Makefile (the names are case sensitive).

<h1>AutoGrader</h1>

We provide the AutoGrader to test your assignment. AutoGrader is provided as autograder.tar. Executing the following command will create the autograder folder.

tar xvf autograder.tar

There are two modes available for testing your assignment with the AutoGrader.

<h2>First mode</h2>

Testing when you are writing code with a pa2 folder

<ul>

 <li>Lets say you have a pa2 folder with the directory structure as described in the assignment.</li>

 <li>Copy the folder to the directory of the autograder (3) Run the autograder with the following command</li>

</ul>

python auto_grader.py

It will run your programs and print your scores.

<h2>Second mode</h2>

This mode is to test your final submission (i.e, pa2.tar)

<ul>

 <li>Copy tar to the auto grader directory</li>

 <li>Run the auto grader with tar as the argument. The command line is</li>

</ul>

python auto_grader.py pa2.tar

<h2>Scoring</h2>

The autograder will print out information about the compilation and the testing process. At the end, if your assignment is completely correct, the score will something similar to what is given below.

You scored

17.5 in second

15.0 in third

17.5 in first

Your TOTAL SCORE = 50.0 /50

Your assignment will be graded for another 50 points with test cases not given to you