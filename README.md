Download Link: https://assignmentchef.com/product/solved-ecse202-assignment-5-introduction-to-c-programming
<br>
This assignment introduces the concept of a command line program using the “C” programming language.  In contrast to Java, the “C” programming environent is somewhat primitive (despite the fact that you can still develop code in Eclipse).

In this assignment you will port (translate) the code you wrote for Assignment 1 from java to “C”.  There is no graphics support, so the program will simply print the values generated by the program (which can be compared to the output from Assignment 1).

Differences between “C” and Java (relative to Assignment 1)

<ol>

 <li>There is no import statement. The closest analog in “C” is the include statement which literally inserts the specified file before compilation.  For the purposes of this course, your program should include the following:</li>

</ol>

#include &lt;stdio.h&gt;

#include &lt;stdlib.h&gt;

When using Eclipse, these are added automatically.

<ol start="2">

 <li>Constants in “C” are not variables. The public static final expression in Java defined a static read-only variable that is used as a program constant.  In “C” one uses a define statement to define a quantity or expression which is subsequently inserted in the source code by the “C” pre-processor.   For example,</li>

</ol>

public static final int NumBalls = 100;

would be replaced in “C” by




#define NumBalls 100




<ol start="3">

 <li>Input/Output in “C” is best explained by example. Consider the following Java code to read a parameter from the user:</li>

</ol>




<strong>double</strong> Vo = readDouble (“Enter the initial velocity of the ball in meters/second [0,100]:

“);




In “C” this would be implemented as




printf((“Enter the initial velocity of the ball in meters/second [0,100]: “);

scanf(“%lf”,&amp;Vo);




Furthermore, Vo would have to be declared beforehand.  For now treat this as a pattern which will be explained in subsequent lectures.  Make sure you precede the variable name with an ampersand, &amp;, as shown in the example.




Unlike the println method in Java, printf uses substitution in place of concatenation.  For example, suppose you wanted to print the values of a, b, and c.  Here is how you would do this using printf:




int a, c; double b;




printf(“The value of a is %d, the value of b is %f, and the value of c is %d
”,a,b,c);




Whenever printf encounters %, it interprets the next character as a type specifier for the next variable to be printed.  In the above example, the first %d matches a, %f matches b, and the last %d matches c.  In fact, the token string can actually embed a more detailed format specification – which will be covered in lectures.  For now, here is a useful one for this assignment:




printf(“This double value, %.2f, is printed with 2 decimal places
”,3.14159);




A couple of observations: i) the integer value after %. Is the number of decimal places, ii) unlike println you need to explicitly add 
 to skip to a new line.




<ol start="4">

 <li>There is no boolean data type, integer values are used instead. It is often convenient to do the following:</li>

</ol>




#define false 0

#define true !false




while (true) {

}




Integer values are used in place of booleans with false corresponding to a zero value, and true <strong>any</strong> non-zero value.

Running your Program

This will be covered in the tutorials, but after you build your program you will need to run it.  It is possible to do so inside Eclipse, but difficult for user input.  The preferred method is to run your program inside a Command Line Interpreter:

<ol>

 <li>Windows:</li>

</ol>

Click the Windows icon at the lower left hand corner of the screen.  This brings up a panel with a search window at the bottom.  Type CMD to launch the Windows CLI.

Microsoft Windows [Version 10.0.10586]

(c) 2015 Microsoft Corporation. All rights reserved.




C:Windowssystem32&gt;




We’ll assume that you wrote a version of the Hello World program using the Eclipse IDE (Integrated Development Environment).  If you are new to programming, this is probably your safest bet.  Otherwise you can use whatever tools suit your needs.  In any case, to run your program from the CLI, you first need to know <em>where </em>your program resides in your computer’s file hierarchy (there is a way around this, but for now let’s assume not).  If you used eclipse, then each project (all the files comprising your computer program) is usually located in

C:Users&lt;your user name&gt;workspace&lt;project name&gt;.  Notice that when you start the CLI on Windows, it defaults to C:Windowssystem32.  In order to access our program we will have to change directories using the cd (change directory) command as follows:




C:Windowssystem32&gt; cd c:Usersferrieworkspace




C:Usersferrieworkspace&gt;dir  Volume in drive C has no label.

Volume Serial Number is 4841-8823




Directory of c:Usersferrieworkspace




2017-06-28  10:19 AM    &lt;DIR&gt;          .

2017-06-28  10:19 AM    &lt;DIR&gt;          ..

2016-07-07  10:40 AM    &lt;DIR&gt;          .metadata

2016-09-12  04:59 PM    &lt;DIR&gt;          argDemo

2016-09-12  11:44 AM    &lt;DIR&gt;          classDemo

2016-07-07  10:41 AM    &lt;DIR&gt;          Hello-C

2016-07-07  11:07 AM    &lt;DIR&gt;          HelloWorld

2017-02-28  11:16 PM    &lt;DIR&gt;          JCalcGUI

2017-06-28  10:19 AM    &lt;DIR&gt;          myHello

0 File(s)              0 bytes

9 Dir(s)  112,799,371,264 bytes free




C:Usersferrieworkspace&gt;




The default behavior of the windows CLI is to echo the current location before the command prompt.  To list the contents of the workspace directory, I followed with a dir (directory) command.  This lists all active projects in my directory.  The “C” program I want to run is in project myHello, so I have to change directories again.




C:Usersferrieworkspace&gt;cd myHello




C:UsersferrieworkspacemyHello&gt;dir  Volume in drive C has no label.

Volume Serial Number is 4841-8823




Directory of c:UsersferrieworkspacemyHello




2017-06-28  10:19 AM    &lt;DIR&gt;          .

2017-06-28  10:19 AM    &lt;DIR&gt;          ..

2017-06-28  10:19 AM            11,468 .cproject

2017-06-28  10:19 AM               785 .project

2017-06-28  10:19 AM    &lt;DIR&gt;          .settings

2017-06-28  10:19 AM    &lt;DIR&gt;          Debug

2017-06-28  10:19 AM    &lt;DIR&gt;          src

2 File(s)         12,253 bytes

5 Dir(s)  112,799,248,384 bytes free




C:UsersferrieworkspacemyHello&gt;




Again, I used the dir command to list the contents of the myHello project folder.  The actual program (executable) lives in the Debug directory, so we need to change directories one more time.




C:UsersferrieworkspacemyHello&gt;cd Debug




C:UsersferrieworkspacemyHelloDebug&gt;dir

Volume in drive C has no label.

Volume Serial Number is 4841-8823




Directory of c:UsersferrieworkspacemyHelloDebug




2017-06-28  10:19 AM    &lt;DIR&gt;          .

2017-06-28  10:19 AM    &lt;DIR&gt;          ..

2017-06-28  10:19 AM            82,300 myHello.exe

2017-06-28  10:19 AM    &lt;DIR&gt;          src

1 File(s)         82,300 bytes

3 Dir(s)  112,799,326,208 bytes free




The file containing the program is the one with the .exe extension, i.e., myHello.exe.




To run the program, simply type the name (no need to include the extension):




C:UsersferrieworkspacemyHelloDebug&gt;myHello

!!!Hello World!!!




C:UsersferrieworkspacemyHelloDebug&gt;  Of course we could have simply cut to the chase and run the program directly by specifying the complete path:




C:Windowssystem32&gt;c:UsersferrieworkspacemyHelloDebugmyHe llo

!!!Hello World!!!




C:Windowssystem32&gt;




The procedure is similar for Mac or Linux users.  In the OS X environment, run the Terminal or XQuartz applications.  For Linux, XTerm is the default application.  In both cases, the CLI (or shell in Linux parlance) will start off in your home directory, so all you need to do is use the cd command to change to the appropriate workspace location, e.g.,




<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="d0b6b5a2a2b9b590bcb9aab1a2b4">[email protected]</a>{myHello}: cd ~/Documents/workspace/myHello/Debug <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="71171403031814311d180b100315">[email protected]</a>{Debug}: ls

makefile        myHello         objects.mk      sources.mk      src <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="15737067677c7055797c6f746771">[email protected]</a>{Debug}:




Note a couple of subtle changes.   First, the workspace directory is usually placed under the Documents folder in the Mac environment and under the home directory in the Linux environment.  Instead of using the dir command, the ls (list) command is used.




Admittedly there are a lot of details here that can be somewhat overwhelming.  The trick is to take things one step at a time and make use of online resources (Google is your friend) when you hit a wall.  The first tutorial will help you to set things up on your own computer, so that your introduction to software development can be as painless as possible.




<strong>             </strong>




<h1>Instructions</h1>




<ol>

 <li>Starting with Bounce.java from Assignment 1, translate this code into a “C” source file (Bounce.c) that compiles into a program that can be run from the command line as shown in the example below:</li>

</ol>




<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="583e3d2a2a313d18143122392a3c">[email protected]</a>{Debug}: Bounce

Enter the initial velocity of the ball in meters/second [0,100]: 40

Enter the launch angle in degrees [0,90]: 85

Enter energy loss parameter [0,1]: .4

Enter the radius of the ball in meters [0.1,5.0]: 1.0 t: 0.00  X: 5.00  Y: 1.00  Vx: -50.00  Vy: 0.00 t: 0.10  X: 5.35  Y: 4.93  Vx: 3.48  Vy: 39.32 t: 0.20  X: 5.70  Y: 8.76  Vx: 3.48  Vy: 38.26 t: 0.30  X: 6.04  Y: 12.48  Vx: 3.47  Vy: 37.20 t: 0.40  X: 6.39  Y: 16.09  Vx: 3.46  Vy: 36.15 t: 0.50  X: 6.73  Y: 19.60  Vx: 3.45  Vy: 35.10 t: 0.60  X: 7.08  Y: 23.01  Vx: 3.45  Vy: 34.05 t: 0.70  X: 7.42  Y: 26.31  Vx: 3.44  Vy: 33.00 t: 0.80  X: 7.77  Y: 29.50  Vx: 3.43  Vy: 31.96 t: 0.90  X: 8.11  Y: 32.60  Vx: 3.43  Vy: 30.91 t: 1.00  X: 8.45  Y: 35.58  Vx: 3.42  Vy: 29.87 t: 1.10  X: 8.79  Y: 38.47  Vx: 3.41  Vy: 28.83 t: 1.20  X: 9.13  Y: 41.25  Vx: 3.41  Vy: 27.80 t: 1.30  X: 9.47  Y: 43.92  Vx: 3.40  Vy: 26.76 t: 1.40  X: 9.81  Y: 46.49  Vx: 3.39  Vy: 25.73 t: 1.50  X: 10.15  Y: 48.96  Vx: 3.39  Vy: 24.70 t: 1.60  X: 10.49  Y: 51.33  Vx: 3.38  Vy: 23.67 t: 1.70  X: 10.83  Y: 53.60  Vx: 3.37  Vy: 22.64 t: 1.80  X: 11.16  Y: 55.76  Vx: 3.37  Vy: 21.62




<ol start="2">

 <li>Run your program and save your output to file Bounce.txt.</li>

</ol>










<strong>To Hand In </strong>




<ol>

 <li>The source file, Bounce.c</li>

 <li>The program output, Bounce.txt</li>

</ol>




This is a relatively short assignment with a 1-week deadline on November 18<sup>th</sup> at 5:00 pm.










<strong> </strong>

<strong>             </strong>

<h1>About Coding Assignments</h1>




We encourage students to work together and exchange ideas.  However, when it comes to finally sitting down to write your code, this must be done <em>independently</em>.  Detecting software plagiarism is pretty much automated these days with systems such as MOSS.




<u>https://www.quora.com/How-does-MOSS-Measure-Of-Software-Similarity-Stanford-detectplagiarism</u>




Please make sure your work is your own.  If you are having trouble, the Faculty provides a free tutoring service to help you along.  You can also contact the course instructor or the tutor during office hours.  There are also numerous online resources – Google is your friend.  The point isn’t simply to get the assignment out of the way, but to actually learn something in doing.




fpf/Nov 10, 2019




<h1>Appendix – The Structure of a “C” Program (revisited)</h1>

<strong> </strong>

The “C” programming language was written originally for a UNIX (predecessor of Linux) environment where interactive programs are run by a shell (CLI) program such as sh.  A consequence of this is that a “C” program has the form of a <em>function</em>.  Notice the similarity to Java.




int main (int argc, char *argv[])

{

printf(“Hello World!
”);

}




You can literally take this code, build the code (it will generate warnings), and run it.  Let’s look at things in more detail.  This function, called main, takes 2 arguments.  The first, argc, is an integer variable, and the second, argv is an array of character strings.  We will go into more detail as to why this is so in future lectures.  These variables are filled in by the CLI when the program is run from the command line.  The function itself can return a value (it doesn’t return anything here), which is enables programs to be combined together in scripts (another topic).  For this assignment we need to figure out how to pass arguments from the command line to the program – time for another example.




1 #include &lt;stdio.h&gt;

2

<ul>

 <li>int main(int argc, char *argv[]) {</li>

 <li>int a, b;</li>

 <li>if (argc != 3) {</li>

 <li>printf(“wrong number of arguments
”);</li>

 <li>return(0);</li>

 <li>}</li>

 <li>sscanf(argv[1],”%d”,&amp;a);</li>

 <li>sscanf(argv[2],”%d”,&amp;b); 11 printf(“%d + %d = %d
”, a, b, a+b);</li>

</ul>

12   }




Let’s assume that I created a file called plus.c containing the above code (in a project called plus within Eclipse).  What will it do?  Let’s evaluate this bit of code line by line:




<ol>

 <li>Any time you use a function in a “C” program, you have to provide a definition that defines its parameters. These are usually contained in an include file.  The notation used above references a system include file for the functions used in this program, i.e., sscanf and</li>

 <li>Blank lines can increase the readability of a program.</li>

 <li>The CLI views each command line as a set of character strings separated by whitespace,</li>

</ol>

i.e., characters such as spaces and tabs.  For example if you entered




<a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="107675626279755056716364537164">[email protected]</a>{ferrie}: plus 3 5  the command line arguments would consist of 3 character strings, plus, 3 and 5  respectively.  In this case variable argc would have a value of 3.  The structure of the argv variable is a bit more complicated.  As we will see later in these lectures, character strings are represented by what is called a <em>pointer</em>, a variable that holds the memory address (i.e. points to) of the first character in the string.  This is not unlike Java

where argv would be a reference to a block of memory on the heap.  So argv corresponds to, in fact, an array of pointers, one for each character string in the command line.  In this example, argv[0] corresponds to the character string plus, argv[1] to the character string for 3 and argv[2] to 5.  The details of these representations will be discussed in more detail in the subsequent lectures.  For now all you need to know is how to gain access to the command line arguments.

<ol start="4">

 <li>Every piece of information that is explicitly represented in a computer program must have a corresponding variable with a data type that matches its usage. Since this program will compute the sum of two integers, they are explicitly represented by variables a and b.</li>

 <li>Any program that interacts with user input needs to do at least some rudimentary checking to make sure that sufficient data has been received for the program to produce the expected output. In this case, since we’re adding two integer values, we need to make sure that 2 arguments have been supplied.  In this case argc=3; recall that argc returns the total number of tokens on the command line, including the program name.</li>

 <li>If the number of arguments is wrong, we send a message to the user using the printf Without going into detail, printf displays anything between the double quotes literally, except for tokens indicated with the % character.  In the example above, the first instance of %d means convert the value of the first matching variable, i.e. a, into a string of numbers representing a decimal number, and substitute into the expression.  The next instance does the same for variable b, and the final one for the value of a+b.</li>

 <li>This causes the program to terminate and return to the CLI.</li>

 <li>Termination of the if</li>

 <li>Recall that argv[1] corresponds to the character string 3 (or whatever the user entered, e.g., 52764), that corresponds to a decimal number. Here the sscanf function is used to convert a string of characters, argv[1], that represent a decimal number, %d, into the computer’s internal binary representation, b.  The ampersand character, &amp;, passes the location of b in memory to sscanf so that the converted value can be returned directly.</li>

 <li>Do the same for the second argument and return the value to variable b.</li>

 <li>At this point we succeeded in reading two values from the command line and storing them as binary variables. Here we compute the sum, convert the result to a character string, and print out the result using the printf function as in Line 6.  Notice that the third instance of %d, which corresponds to the sum, operates on an expression (a+b) instead of a single variable.</li>

 <li>Close of program.</li>

</ol>





