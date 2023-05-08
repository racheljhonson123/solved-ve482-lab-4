Download Link: https://assignmentchef.com/product/solved-ve482-lab-4
<br>
<h1>1         Database</h1>

This is the evening, you are exhausted after a long day of work on mumsh. So you decide to poke around and learn more about database, as unfortunately you never had to opportunity to select such course during your studies.

<h2>1.1        Database creation</h2>

As a first step you need to find a database, you fire-up your web-browser and try to connect to a proper search engine. Unfortunately you VPN takes ages to connect so need an alternative plan. After a bit of thinking you realise that you still have a git version of the Linux kernel, and as you know everything about git you can easily generate logs from the git commits. To ensure a proper formatting you refer to git <a href="https://git-scm.com/docs/pretty-formats">pretty format</a> documentation page.

So you open a terminal running mumsh and type a simple command line to test database generation.

The goal being to get a basic introduction to database you only want to focus on basic queries, in particular you do not need a very complicated database and in the end only generating two csv files<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a>containing the following fields is enough.

<table width="488">

 <tbody>

  <tr>

   <td width="328">Fields for timestamp.csv:•     Hash of the commit•     Author name•     Author date, strict ISO 8601 format•     Author date, UNIX timestamp</td>

   <td width="161">Fields for db.csv:•     Hash of the commit•     Author name•     Subject</td>

  </tr>

 </tbody>

</table>

<h2>1.2        Database system installation</h2>

As you want to ensure your understanding and guesses are correct you need to verify a few things online. Luckily your VPN is now working, so you can use a proper search engine and ensure the correctness of what you found.

<ul>

 <li>What are the most common database systems?</li>

 <li>Briefly list the pros and cons of the three most common ones.</li>

</ul>

After completing your reading you decide to install SQLite on your Linux system. The next step is now to import your git database into two tables.

<ul>

 <li>Create an empty SQLite database.</li>

 <li>Use the SQLite shell to prepare two empty tables for each of your .csv file.</li>

 <li>Import each .csv file in its corresponding SQLite table.</li>

</ul>

<h2>1.3        Database queries</h2>

At this stage you want to run basic queries to verify that the database has been imported correctly.

Therefore you spend the rest of the evening playing around the database and running queries.

<ul>

 <li>Who are the top five contributors to the Linux kernel since the beginning?</li>

 <li>Who are the top five contributors to the Linux kernel for each year over the past five years?</li>

 <li>What is the most common “commit subject”?</li>

 <li>On which day is the number of commits the highest?</li>

 <li>Determine the average time between two commits for the five main contributor.</li>

</ul>

<h1>2         Debugging</h1>

You are pretty happy and enjoying the database tasks when your mum pops in your room. She looks pretty upset that you are still not asleep as she thinks you were playing video games…

When you explain her to that you have terrible bugs in your shell and needed a bit of change, she asked you whether you had used GDB. As you replied “Can I eat it?” she realises you probably do not know much about it. She kindly tells you to have a quick try at it on your current mumsh version to preview it.

This should become very handy if you ever have to work on a large scale project.

<ol>

 <li>How to enable built-in debugging in gcc?</li>

 <li>What is the meaning of GDB?</li>

 <li>Compile the master branch of you mumsh with debugging enabled.</li>

</ol>

<h2>2.1        Basic GDB usage</h2>

<ol>

 <li>Find the homepage of the GDB project.</li>

 <li>What languages are supported by GDB?</li>

</ol>

Mum who is now fully awaken kindly guides you in your discovery of GDB. In a terminal navigate to the folder where the previously mentioned program is located. Enter gdb in the terminal. An interactive shell should open, under the condition that GDB has been installed. First note that this shell recalls history when using the arrow keys and auto-completes command using the TAB key.

At any stage help [command] can be typed to get general information or details on a specific command. To debug the program mumsh input file mumsh. The program is now loaded but not run. In order to run it, input the command run.

The command break mumsh.c:17 sets a breakpoint at line 17 in the file mumsh.c. Upon executing run, the program pauses each time it encounters a breakpoint. There is no restriction on the number of breakpoints added to a program.

An alternative strategy consists in breaking at a certain function. In that case input for instance break function_name, in order to stop each time the function function_name is called.

When blocked at a breakpoint computation can be resumed using the command continue but will stop at the next breakpoint. In order to progress line-by-line use the command step. If more than one instruction is written on a line input next to only run a single instruction at a time. Since typing in next or step many time can be tedious GDB offers the possibility the repeat the previous command by just pushing the ENTER key.

In order for debugging to be effective it is necessary to observe things at breakpoints: use print tmp to display the value of the variable tmp. Special breakpoints, called watchpoints, can be used to track a variable. This is achieved through the watchtmp command. Each time tmp is modified the program stops and display both its old and new values.

For a pointer p, print p prints the memory address of the pointer. Accessing each element of a structure is done in a similar way as in C, e.g. p-&gt;s displays the field s referenced by pointer p. Note that it is also possible to input print *p even if p is a pointer on a structure (this is not easily done in C).

<ol start="3">

 <li>What are the following GDB commands doing:

  <ul>

   <li>backtrace delete</li>

   <li>where info breakpoints</li>

   <li>finish</li>

  </ul></li>

 <li>Search the documentation and explain how to use conditional breakpoints.</li>

</ol>

Watch this <a href="https://www.youtube.com/watch?v=PorfLSr3DDI">youtube</a> video and answer the following questions.

<ol start="5">

 <li>What is -tui option for GDB?</li>

 <li>What is the “reverse step” in GDB and how to enable it. Provide the key steps and commands.</li>

</ol>

<a href="#_ftnref1" name="_ftn1">[1]</a> The db.csv and timestamp.csv can be found on the server in the directory ve482/l4.