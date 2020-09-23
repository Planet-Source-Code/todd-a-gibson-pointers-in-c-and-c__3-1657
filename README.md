<div align="center">

## Pointers in C and C\+\+


</div>

### Description

Struggling with pointers in C or C++? This tutorial takes a unique approach to explaining pointers.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Todd A\. Gibson](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/todd-a-gibson.md)
**Level**          |Beginner
**User Rating**    |4.8 (24 globes from 5 users)
**Compatibility**  |C, C\+\+ \(general\), Microsoft Visual C\+\+, Borland C\+\+, UNIX C\+\+
**Category**       |[Miscellaneous](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/miscellaneous__3-1.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/todd-a-gibson-pointers-in-c-and-c__3-1657/archive/master.zip)





### Source Code

<hr>
<H2>Pointers</H2>
<i>The most up-to-date copy of this article can always be found at <a href="http://carbon.cudenver.edu/~tgibson/tutorial/">http://carbon.cudenver.edu/~tgibson/tutorial</a></i>
<BR>
<H3>Using Variables</H3>
<P>
Essentially, the computer's memory is made up of bytes. Each byte has
a number, <A HREF="http://carbon.cudenver.edu/~tgibson/tutorial/addressDef.html">an address</A>, associated with it.
The picture below represents several bytes of a computer's memory. In the picture, addresses 924 thru 940 are shown.
</P>
<P>
<IMG width="560" height="100" SRC="http://carbon.cudenver.edu/~tgibson/tutorial/ribbonAlone.jpg" ALT="Basic ribbon of memory">
</P>
Try:
<TABLE WIDTH="1"> <TR ALIGN="CENTER"> <TD> <B>C++</B> </TD> <TD> <B>C</B> </TD> </TR> <TR> <TD>
<PRE>
 1:#include &lt;iostream.h&gt;
 2:main&#40;&#41;
 3:&#123;
 4: float fl=3.14;
 5: cout &lt;&lt; fl &lt;&lt; endl;
 6:&#125;
</PRE>
</TD><TD>
<PRE>
 1:#include &lt;stdio.h&gt;
 2:main&#40;&#41;
 3:&#123;
 4: float fl=3.14;
 5: printf&#40;"%.2f\n", fl&#41;;
 6:&#125;
</PRE>
</TD></TR></TABLE>
At line &#40;4&#41; in the program above, the computer reserves
memory for <CODE>fl</CODE>. In our examples, we'll assume
that a <CODE>float</CODE> requires 4 bytes. Depending on the
computer's architecture, a <CODE>float</CODE> may require 2,
4, 8 or some other number of bytes.
<P>
<IMG width="560" height="129" SRC="http://carbon.cudenver.edu/~tgibson/tutorial/ribbonFl.jpg" ALT="Variable fl allocated">
</P>
When <CODE>fl</CODE> is used in line &#40;5&#41;, two distinct steps occur:
<OL>
 <LI>The program finds and <A HREF="http://carbon.cudenver.edu/~tgibson/tutorial/step1Info.html">grabs the address</A> reserved for
   <CODE>fl</CODE>--in this example 924.</li>
 <LI>The contents stored at that address are <A HREF="http://carbon.cudenver.edu/~tgibson/tutorial/step2Info.html">retrieved</A></li>
</OL>
<B>To generalize, whenever <I>any</I> variable is accessed,
the above two distinct steps occur to retrieve the contents
of the variable.</B>
<TABLE WIDTH="560"><TR BGCOLOR="#D3D3D3"><TD>
	 The illustration that shows 3.14 in the
	 computer's memory can be misleading.	Looking at
	 the diagram, it appears that "3" is stored in memory
	 location <CODE>924</CODE>, "." is stored in memory
	 location <CODE>925</CODE>, "1" in <CODE>926</CODE>,
	 and "4" in <CODE>927</CODE>.	Keep in mind that the
	 computer actually uses an algorithm to convert the
	 floating point number 3.14 into a set of ones and
	 zeros. Each byte holds 8 ones or zeros. So, our 4
	 byte <CODE>float</CODE> is stored as 32 ones and zeros
	 &#40;8 per byte times 4 bytes&#41;. Regardless of whether
	 the number is 3.14, or -273.15, the number is always
	 stored in 4 bytes as a series of 32 ones and zeros.
</TD></TR></TABLE>
<P>
<H3>Separating the Steps</H3>
Two operators are provided that, when used, cause these two steps to
occur separately.
</P>
<TABLE BORDER=1>
<TR>
 <TH>operator</TH><TH>meaning</TH><TH>example</TH>
</TR>
<TR>
<TD ALIGN="CENTER"><CODE>&</CODE></TD><TD>do only step 1 on a variable</TD>
	<TD><CODE>&fl</CODE></TD>
</TR>
<TR>
<TD ALIGN="CENTER"><CODE>*</CODE></TD><TD>do step 2 on a number&#40;address&#41;</TD>
	<TD><CODE>*some_num</CODE></TD>
</TR>
</TABLE>
<BR>
Try this code to see what prints out:
<TABLE WIDTH="1"> <TR ALIGN="CENTER"> <TD> <B>C++</B> </TD> <TD> <B>C</B> </TD> </TR> <TR> <TD>
<PRE>
1:#include &lt;iostream.h&gt;
2:main&#40;&#41;
3:&#123;
4: float fl=3.14;
5: cout &lt;&lt; "fl's address=" &lt;&lt; <FONT COLOR="GRAY">&#40;unsigned int&#41;</FONT> &fl &lt;&lt; endl;
6:&#125;
</PRE>
</TD><TD>
<PRE>
1:#include &lt;stdio.h&gt;
2:main&#40;&#41;
3:&#123;
4: float fl=3.14;
5: printf&#40;"fl's address=%u\n", <FONT COLOR="GRAY">&#40;unsigned int&#41;</FONT> &fl&#41;;
6:&#125;
</PRE>
</TD></TR></TABLE>
On line &#40;5&#41; of the example, The <CODE>&</CODE> operator is being used
on <CODE>fl</CODE>. On line &#40;5&#41;, only step 1 is being performed on
a variable:
<OL>
<LI>The program finds and grabs the address reserved for fl...</li>
</OL>
It is <CODE>fl</CODE>'s address that is printed to the screen.
If the <CODE>&</CODE> operator had not been placed in front
of <CODE>fl</CODE>, then step 2 would have occurred as well,
and 3.14 would have been printed to the screen.
<TABLE WIDTH="560"><TR BGCOLOR="#D3D3D3"><TD>
	 The <FONT COLOR="GRAY"><CODE>&#40;unsigned int&#41;</CODE></FONT> phrase
	 will be discussed later. It is there so that <CODE>&addr</CODE>
	 will print out as a non-negative number. It has been shown in
	 gray to indicate that you must include it for the program to
	 compile properly but that it is not relevant to this current
	 discussion.
</TD></TR></TABLE>
<P>
<HR>
Keep in mind that an address is really just a simple number. In fact, we can store an address in an integer variable. Try this:
</P>
<TABLE WIDTH="1"> <TR ALIGN="CENTER"> <TD> <B>C++</B> </TD> <TD> <B>C</B> </TD> </TR> <TR> <TD>
<PRE>
1:#include &lt;iostream.h&gt;
2:main&#40;&#41;
3:&#123;
4: float fl=3.14;
5: unsigned int addr=<FONT COLOR="GRAY">&#40;unsigned int&#41;</FONT> &fl;
6: cout &lt;&lt; "fl's address=" &lt;&lt; addr &lt;&lt; endl;
7:&#125;
</PRE>
</TD><TD>
<PRE>
1:#include &lt;stdio.h&gt;
2:main&#40;&#41;
3:&#123;
4: float fl=3.14;
5: unsigned int addr=<FONT COLOR="GRAY">&#40;unsigned int&#41;</FONT> &fl;
6: printf&#40;"fl's address=%u\n", addr&#41;;
7:&#125;
</PRE>
</TD></TR></TABLE>
<P>
<IMG width="560" height="210" SRC="http://carbon.cudenver.edu/~tgibson/tutorial/ribbonFlAddr1.jpg" ALT="The address of fl is stored in addr">
</P>
The above code shows that there is nothing magical about addresses.
They are just simple numbers that can be stored in integer variables.
<TABLE WIDTH="560"><TR BGCOLOR="#D3D3D3"><TD>
	 The <CODE>unsigned</CODE> keyword at the start of line
	 &#40;5&#41; simply means that the integer will not hold negative
	 numbers. As before, the <FONT COLOR="GRAY"><CODE>&#40;unsigned
	 int&#41;</CODE></FONT> phrase has been shown in gray. It must
	 be included for the code to compile, but is not relevant to
	 this discussion. It will be discussed later.
</TD></TR></TABLE>
<P>
<HR>
Now let's test the other operator, the <CODE>*</CODE> operator that
retrieves the contents stored at an address:
</P>
<TABLE WIDTH="1"> <TR ALIGN="CENTER"> <TD> <B>C++</B> </TD> <TD> <B>C</B> </TD> </TR> <TR> <TD>
<PRE>
1:#include &lt;iostream.h&gt;
2:main&#40;&#41;
3:&#123;
4: float fl=3.14;
5: unsigned int addr=<FONT COLOR="GRAY">&#40;unsigned int&#41;</FONT> &fl;
6: cout &lt;&lt; "fl's address=" &lt;&lt; addr &lt;&lt; endl;
7: cout &lt;&lt; "addr's contents=" &lt;&lt; * <FONT COLOR="GRAY">&#40;float*&#41;</FONT> addr &lt;&lt; endl;
8:&#125;
</PRE>
</TD><TD>
<PRE>
1:#include &lt;stdio.h&gt;
2:main&#40;&#41;
3:&#123;
4: float fl=3.14;
5: unsigned int addr=<FONT COLOR="GRAY">&#40;unsigned int&#41;</FONT> &fl;
6: printf&#40;"fl's address=%u\n", addr&#41;;
7: printf&#40;"addr's contents=%.2f\n", * <FONT COLOR="GRAY">&#40;float*&#41;</FONT> addr&#41;;
8:&#125;
</PRE>
</TD></TR></TABLE>
In line &#40;7&#41;, step 2 has been performed on a number:
<OL START="2">
<LI>The contents stored at that address [<CODE>addr</CODE>] are retrieved</li>
</OL>
<TABLE WIDTH="560"><TR BGCOLOR="#D3D3D3"><TD>
	In order to make line &#40;7&#41; work, a little "syntax sugar"
	had to be added for the program to compile. Like before,
	<FONT COLOR="GRAY"><CODE>&#40;float*&#41;</CODE></FONT> is shown in
	gray because it is not relevant to the current discussion.
	For the sake of this discussion, just read "<CODE>*<FONT
	COLOR="GRAY">&#40;float*&#41;</FONT>addr</CODE>" as "<CODE>*addr</CODE>"	&#40;that is, ignore the stuff in gray&#41;. The code shown in gray
	will be discussed later.
</TD></TR></TABLE>
<H3>OK, But why do we need & and *</H3>
<P>
We have shown that 2 distinct steps occur when accessing a variable, and
that we can make those steps occur separately. But why is this useful?
</P>
<P>
To see why, let's first look at how functions work in C/C++. Try this code:
</P>
<TABLE WIDTH="1"> <TR ALIGN="CENTER"> <TD> <B>C++</B> </TD> <TD> <B>C</B> </TD> </TR> <TR> <TD>
<PRE>
 1:#include &lt;iostream.h&gt;
 2:void somefunc&#40;float fvar&#41;
 3:&#123;
 4: fvar=99.9;
 5:&#125;
 6:main&#40;&#41;
 7:&#123;
 8: float fl=3.14;
 9: somefunc&#40;fl&#41;;
10: cout &lt;&lt; fl &lt;&lt; endl;
11:&#125;
</PRE>
</TD><TD>
<PRE>
 1:#include &lt;stdio.h&gt;
 2:void somefunc&#40;float fvar&#41;
 3:&#123;
 4: fvar=99.9;
 5:&#125;
 6:main&#40;&#41;
 7:&#123;
 8: float fl=3.14;
 9: somefunc&#40;fl&#41;;
10: printf&#40;"%.2f\n", fl&#41;;
11:&#125;
</PRE>
</TD></TR></TABLE>
What prints out? 3.14? 99.9? It turns out that 3.14 prints out. The general term used to describe this behavior is <i>pass by value</i>.
When <CODE>somefunc&#40;fl&#41;</CODE> is called at line 9:
<OL>
<LI>Execution jumps to line &#40;2&#41; to run the function</li>
<LI><CODE>fvar</CODE> is created as its own variable and <CODE>fl</CODE>'s value is copied into <CODE>fvar</CODE><br>
<IMG width="560" height="210" SRC="http://carbon.cudenver.edu/~tgibson/tutorial/ribbonFlFvar1.jpg" ALT="fvar stores value passed into function"></li>
<LI>On line &#40;4&#41;, 99.9 is assigned to fvar<br>
<IMG width="560" height="240" SRC="http://carbon.cudenver.edu/~tgibson/tutorial/ribbonFlFvar2.jpg" ALT="99.9 is assigned to fvar"></li>
<LI>Now that the function is finished, execution resumes in <CODE>main</CODE> where it left off &#40;line 10&#41;. The <CODE>fl</CODE> variable is unchanged, 3.14 prints out.</li>
</OL>
<HR>
We can circumvent this <i>pass by value</i> behavior and change values
passed into functions by using the <CODE>&</CODE> and <CODE>*</CODE>
operators.
<TABLE WIDTH="1"> <TR ALIGN="CENTER"> <TD> <B>C++</B> </TD> <TD> <B>C</B> </TD> </TR> <TR> <TD>
<PRE>
 1:#include &lt;iostream.h&gt;
 2:void somefunc&#40;unsigned int fptr&#41;
 3:&#123;
 4: *&#40;float*&#41;fptr=99.9;
 5:&#125;
 6:
 7:main&#40;&#41;
 8:&#123;
 9: float fl=3.14;
10: unsigned int addr=&#40;unsigned int&#41; &fl;
11: somefunc&#40;addr&#41;;
12: cout &lt;&lt; fl &lt;&lt; endl;
13:&#125;
</PRE>
</TD><TD>
<PRE>
 1:#include &lt;stdio.h&gt;
 2:void somefunc&#40;unsigned int fptr&#41;
 3:&#123;
 4: *&#40;float*&#41;fptr=99.9;
 5:&#125;
 6:
 7:main&#40;&#41;
 8:&#123;
 9: float fl=3.14;
10: unsigned int addr=&#40;unsigned int&#41; &fl;
11: somefunc&#40;addr&#41;;
12: printf&#40;"%.2f\n", fl&#41;;
13:&#125;
</PRE>
</TD></TR></TABLE>
Quite simply, the two steps that normally occur when accessing a variable
are being separated to allow us to change the variable's value in a
different function.
<OL>
<LI>The floating point variable fl is created at line &#40;9&#41; and given
the value 3.14<br>
<IMG SRC="http://carbon.cudenver.edu/~tgibson/tutorial/ribbonFl.jpg" ALT="Variable fl allocated"></li>
<LI>The <CODE>&</CODE> operator is used on fl at line &#40;10&#41; &#40;do only
step 1, get the address&#41;. The address is stored in the integer variable <CODE>addr</CODE>.<br>
<IMG width="560" height="210" SRC="http://carbon.cudenver.edu/~tgibson/tutorial/ribbonFlAddr1.jpg" ALT="The address of fl is stored in addr"></li>
<LI>The function <CODE>somefunc</CODE> is called at line &#40;at line 11&#41;
and <CODE>fl</CODE>'s address is passed as an argument.</li>
<LI>The function <CODE>somefunc</CODE> begins at line &#40;2&#41;,
<CODE>fptr</CODE> is created and <CODE>fl</CODE>'s address is copied
into fptr.<br>
<IMG width="560" height="210" SRC="http://carbon.cudenver.edu/~tgibson/tutorial/ribbonFlAddrFptr1.jpg" ALT="The argument addr is copied to fptr"></li>
<LI>The <CODE>*</CODE> operator is used on <CODE>fptr</CODE> at line &#40;4&#41; -- do step 2, the contents stored in an address are retrieved. In this example, the contents at address 924 are retrieved.</li>
<LI>The contents at address 924 are assigned the value <CODE>99.9</CODE>.<br>
<IMG width="560" height="230" SRC="http://carbon.cudenver.edu/~tgibson/tutorial/ribbonFlAddrFptr2.jpg" ALT="99.9 is assigned to fl"></li>
<LI>The function finishes. Control returns to line &#40;12&#41;.</li>
<LI>The contents of <CODE>fl</CODE> are printed to the screen.</li>
</OL>
<h3>Pointer Variables</h3>
Even though we have shown that an address is nothing more than a simple
integer, the creators of the language were afraid we might confuse
variables in our programs. We might confuse integers we intend to use
for program values &#40;e.g. variables storing ages, measurements, counters,
etc.&#41; with integers we intend to use for holding the addresses of our
variables.
<P>
The language creators decided the best way to <A HREF="http://carbon.cudenver.edu/~tgibson/tutorial/ptrWhy.html">eliminate confusion</A> was to create a different <i>type</i> of variable for holding addresses. A first attempt at this might have looked something like this:
</P>
<PRE>
1:...
2: float fl=3.14;
3: float PTR addr = &fl;
4:...
</PRE>
On line &#40;3&#41;, here is how to describe the addr variable:<br>
<IMG width="559" height="125" SRC="http://carbon.cudenver.edu/~tgibson/tutorial/ptrDesc1.jpg" ALT="addr is a pointer to a float">
<br>
<B>&#40;A&#41;</B> <CODE>addr</CODE> is an integer. <B>&#40;B&#41;</B> However, it is a special integer designed to hold the address of a
<B>&#40;C&#41;</B> <CODE>float</CODE>
<P>
In the code above, line &#40;3&#41; Is close to what the creators of the language
wanted except for one thing: using <CODE>PTR</CODE> would require
introducing another keyword into the language. If there is one thing
that all C instructors like to brag about, it is how there are only
a very small number of keywords in the language. Well, using line &#40;3&#41;
as shown above would mean adding <CODE>PTR</CODE> as another keyword to
the language.
</P>
<P>
To avoid this threat to the very fabric of the universe, the creators
cast about for something already being used in the language that could
do double duty as <CODE>PTR</CODE> shown above. What they came up with
was the following:
</P>
<PRE>
1:...
2: float fl=3.14;
3: float * addr = &fl;
4:...
</PRE>
Even with the <CODE>*</CODE> instead of <CODE>PTR</CODE>, <CODE>addr</CODE> is described the same way:<br>
<IMG width="559" height="125" SRC="http://carbon.cudenver.edu/~tgibson/tutorial/ptrDesc2.jpg" ALT="addr is a pointer to a float">
<br>
<B>&#40;A&#41;</B> <CODE>addr</CODE> is an integer. <B>&#40;B&#41;</B> However, it is a special integer designed to hold the address of a
<B>&#40;C&#41;</B> <CODE>float</CODE>
<P>
These variables are described this way, regardless of the type:
</P>
<IMG width="560" height="125" SRC="http://carbon.cudenver.edu/~tgibson/tutorial/ptrDesc3.jpg" ALT="addr is a pointer to a char">
<br>
<B>&#40;A&#41;</B> <CODE>addr</CODE> is an integer. <B>&#40;B&#41;</B> However, it is a special integer designed to hold the address of a
<B>&#40;C&#41;</B> <CODE>char</CODE>
<br>
<IMG width="560" height="126" SRC="http://carbon.cudenver.edu/~tgibson/tutorial/ptrDesc4.jpg" ALT="addr is a pointer to an int">
<br>
<B>&#40;A&#41;</B> <CODE>addr</CODE> is an integer. <B>&#40;B&#41;</B> However, it is a special integer designed to hold the address of an
<B>&#40;C&#41;</B> <CODE>int</CODE>
<P>
This "...special integer..." way of describing these variables is a
mouthful, so we shorten it and just say "addr is a float pointer" or
"addr is a pointer to a float" &#40;or char, or int, etc.&#41;.
</P>
<P>
Unfortunately, the language creators chose the <CODE>*</CODE> character
to replace PTR. The <CODE>*</CODE> character is confusing because the
<CODE>*</CODE> character is also used to get the contents at an address
&#40;"do step 2 on a number"&#41;. <B>These two uses of the <CODE>*</CODE>
character have <A HREF="http://carbon.cudenver.edu/~tgibson/tutorial/similarity.html">nothing</A> to do with each other.</B>
</P>
<H3>What is all that "syntax sugar" anyway? &#40;Casting&#41;</H3>
Let's take one last look at our original code that illustrates the
utility of separating out steps 1 & 2.
<TABLE WIDTH="1"> <TR ALIGN="CENTER"> <TD> <B>C++</B> </TD> <TD> <B>C</B> </TD> </TR> <TR> <TD>
<PRE>
 1:#include &lt;iostream.h&gt;
 2:void somefunc&#40;unsigned int fptr&#41;
 3:&#123;
 4: *&#40;float*&#41;fptr=99.9;
 5:&#125;
 6:
 7:main&#40;&#41;
 8:&#123;
 9: float fl=3.14;
10: unsigned int addr=&#40;unsigned int&#41; &fl;
11: somefunc&#40;addr&#41;;
12: cout &lt;&lt; fl &lt;&lt; endl;
13:&#125;
</PRE>
</TD><TD>
<PRE>
 1:#include &lt;stdio.h&gt;
 2:void somefunc&#40;unsigned int fptr&#41;
 3:&#123;
 4: *&#40;float*&#41;fptr=99.9;
 5:&#125;
 6:
 7:main&#40;&#41;
 8:&#123;
 9: float fl=3.14;
10: unsigned int addr=&#40;unsigned int&#41; &fl;
11: somefunc&#40;addr&#41;;
12: printf&#40;"%.2f\n", fl&#41;;
13:&#125;
</PRE>
</TD></TR></TABLE>
In nearly all of the code samples, you have been asked to
ignore certain bits of the code. These bits of code have
always appeared around those areas where we are either taking
the address of a variable or getting the contents at an address
&#40;doing step 1 or step 2 on a variable&#41;
<P>
Those bits of "syntax sugar" are there to keep the compiler
from complaining. The first example of this in the above
program is on line &#40;10&#41;.
</P>
<P>
On line &#40;10&#41; we are taking the address of the floating
point number <CODE>fl</CODE> &#40;"do only step 1 on a number"&#41;.
After we get that address, we store it in <CODE>addr</CODE>.
</P>
<P>
Why would the compiler complain? Because when we get assign the
address of <CODE>fl</CODE> to <CODE>addr</CODE>, the compiler
does not expect <CODE>addr</CODE> to be an <CODE>unsigned
int</CODE>. The compiler expects <CODE>addr</CODE> to be a
<CODE>float *</CODE>. That is, <i>a special integer designed
to hold the address of a float</i>. To keep the compiler from
complaining, we tell the compiler to treat <CODE>&fl</CODE> as
an <CODE>unsigned int</CODE> rather than a <CODE>float *</CODE>.
</P>
<P>
This "syntax sugar" that causes the compiler to treat
variables and expressions differently is called <I>casting</I>.
The way a programmer describes line &#40;10&#41; is: "The address of
<CODE>fl</CODE> is being <A HREF="http://carbon.cudenver.edu/~tgibson/tutorial/casting.html">cast</A> into
an <CODE>unsigned int</CODE> and assigned to <CODE>addr</CODE>"
</P>
<P>
The other place casting occurs is on line &#40;4&#41;. On line &#40;4&#41;,
we are getting the contents at an address &#40;"do step 2 on a
number/address"&#41;. Why would the compiler complain? Because the
compiler should get the contents of the address of a float.
The address of our float is in stored in <CODE>fptr</CODE>,
which is an <CODE>unsigned int</CODE>, not a <CODE>float
*</CODE>. We tell the compiler to treat <CODE>fptr</CODE>
as the address of a floating point number by casting it into a
<CODE>float *</CODE>. Once we tell the compiler this, we can
get the contents at the address without complaint.
</P>
<h3>Putting it all together</h3>
<P>
From the previous section, you might be left with the impression
that whenever you deal with addresses and pointers, there is
a lot of casting. Not so. The only reason our examples up
till now have required casting is because we were storing our
addresses in <CODE>unsigned int</CODE> variables. The language
designers want us to store addresses in the "special integer"
variables, that is, the pointer variables they designed for
just such a purpose.
</P>
<P>
Once we replace our <CODE>unsigned int</CODE> variables
with these pointer variables, none of the casting
is required:
</P>
<TABLE WIDTH="1"> <TR ALIGN="CENTER"> <TD> <B>C++</B> </TD> <TD> <B>C</B> </TD> </TR> <TR> <TD>
<PRE>
 1:#include &lt;iostream.h&gt;
 2:void somefunc&#40;float* fptr&#41;
 3:&#123;
 4: *fptr=99.9;
 5:&#125;
 6:
 7:main&#40;&#41;
 8:&#123;
 9: float fl=3.14;
10: float* addr = &fl;
11: somefunc&#40;addr&#41;;
12: cout &lt;&lt; fl &lt;&lt; endl;
13:&#125;
</PRE>
</TD><TD>
<PRE>
 1:#include &lt;stdio.h&gt;
 2:void somefunc&#40;float* fptr&#41;
 3:&#123;
 4: *fptr=99.9;
 5:&#125;
 6:
 7:main&#40;&#41;
 8:&#123;
 9: float fl=3.14;
10: float* addr = &fl;
11: somefunc&#40;addr&#41;;
12: printf&#40;"%.2f\n", fl&#41;;
13:&#125;
</PRE>
</TD></TR></TABLE>
<UL>
<LI>On line &#40;10&#41;, when we take the address of <CODE>fl</CODE>
the address is assigned to a variable designed to hold
it. No casting is required.</LI>
<LI>When <CODE>addr</CODE> is passed to the function in line &#40;11&#41;,
<CODE>addr</CODE> is copied to <CODE>fptr</CODE> on line
&#40;2&#41;.</LI>
<LI>Line &#40;2&#41; shows that <CODE>fptr</CODE> is created as a float
pointer, that is a variable designed to hold the address of
a floating point number. As a result, no casting is needed
on line &#40;4&#41; where the contents at the address are retrieved.</li>
</UL>
<HR>
<H3>Revision History</H3>
<TABLE>
<TR>
<TD>
1999 March 19
</TD>
<TD>
Added C version of code. Minor corrections to text.
</TD>
</TR>
<TR>
<TD>
2001 April 30
</TD>
<TD>
Some minor corrections.
</TD>
</TR>
</TABLE>
<HR>
<H3>Miscellaneous</H3>
<P>
The graphics in this tutorial were created using the freely
distributed image manipulation program The GIMP. Information on
The GIMP can be found at <a href="http://www.gimp.org">http://www.gimp.org/</a>
</P>
<P>
Please contact me with any errata, comments,
suggested changes, or improvements:
<a href="mailto:tgibson@dimensional.com"><CODE>tgibson@dimensional.com</CODE></a>
</P>
<P>
The code in this tutorial that stores addresses in
<CODE>unsigned int</CODE>'s may fail on a very few compilers,
particulary older compilers. If this is the case with your
compiler, try using <CODE>unsigned long</CODE> instead of
<CODE>unsigned int</CODE>.
</P>
<P><CODE>Copyright 2001 Todd A. Gibson. All Rights Reserved.</CODE></P>
    While this document is copyright by me with all rights
    reserved, permission is granted to freely distribute
    verbatim copies of this document provided that no
    modifications outside of formatting be made, and that
    this notice remain intact.

