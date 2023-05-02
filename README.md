Download Link: https://assignmentchef.com/product/solved-cmsc-430-project-4
<br>
The fourth project involves modifying the semantic analyzer for the attached compiler by adding checks for semantic errors. The static semantic rules of this language are the following:

Variables and parameter names have local scope. The scope rules require that all names be declared and prohibit duplicate names within the same scope. The type correspondence rules are as follows:

<ul>

 <li>Boolean expressions cannot be used with arithmetic or relational operators.</li>

 <li>Arithmetic expressions cannot be used with logical operators.</li>

 <li>Reductions can only contain numeric types.</li>

 <li>Only integer operands can be used with the remainder operator.</li>

 <li>The two statements in an <sub>if</sub> statement must match in type. No coercion is performed.</li>

 <li>All the statements in a <sub>case</sub> statement must match in type. No coercion is performed.  The type of the <sub>if</sub> expression must be Boolean.</li>

 <li>The type of the <sub>case</sub> expression must be Integer</li>

 <li>A narrowing variable initialization or function return occurs when a real value is being forced into integer. Widening is permitted.</li>

 <li>Boolean types cannot be mixed with numeric types in variable initializations or function returns.</li>

</ul>

Type coercion from an integer to a real type is performed within arithmetic expressions.

You must make the following semantic checks. Those highlighted in yellow are already performed by the code that you have been provided, although you are must make minor modifications to account for the addition of real types and the need to perform type coercion and to handle the additional arithmetic and logical operators.

<table width="365">

 <tbody>

  <tr>

   <td width="24"></td>

   <td colspan="2" width="341">Using Boolean Expressions with Arithmetic Operator</td>

  </tr>

  <tr>

   <td width="24"></td>

   <td colspan="2" width="341">Using Boolean Expressions with Relational Operator</td>

  </tr>

  <tr>

   <td width="24"></td>

   <td colspan="2" width="341">Using Arithmetic Expressions with Logical Operator</td>

  </tr>

  <tr>

   <td width="24"></td>

   <td width="262">Reductions containing nonnumeric types</td>

   <td width="80"></td>

  </tr>

 </tbody>

</table>

<ul>

 <li>Remainder Operator Requires Integer Operands</li>

 <li>If-Then Type Mismatch</li>

 <li>Case Types Mismatch</li>

 <li>If Condition Not Boolean</li>

 <li>Case Expression Not Integer</li>

 <li>Narrowing Variable Initialization</li>

</ul>

<table width="233">

 <tbody>

  <tr>

   <td width="24"></td>

   <td colspan="2" width="209">Variable Initialization Mismatch</td>

  </tr>

  <tr>

   <td width="24"></td>

   <td width="133">Undeclared Variable</td>

   <td width="76"></td>

  </tr>

 </tbody>

</table>

<ul>

 <li>Duplicate Variable</li>

 <li>Narrowing Function Return</li>

</ul>

This project requires modification to the bison input file, so that it defines the additional semantic checks necessary to produce these errors and addition of functions to the library of type checking functions already provided in <sub>types.cc</sub>. You must also make some modifications to the functions provided. You need to add a check to the <sub>checkAssignment</sub> function for mismatched types in the case that Boolean and numeric types are mixed. You need to also add code to the <sub>checkArithmetic</sub> function to coerce integers to reals when the types are mixed and the error message must be modified to indicate that numeric rather than only integer types are permitted.

The provided code includes a template class <sub>Symbols</sub> that defines the symbol table. It already includes a check for undeclared identifiers. You need to add a check for duplicate identifiers.

Like the lexical and syntax errors, the compiler should display the semantic errors in the compilation listing, after the line in which they occur. An example of compilation listing output containing semantic errors is shown below:

1  — Test of Multiple Semantic Errors

2

<ul>

 <li>function test a: integer returns integer;</li>

 <li>b: integer is</li>

 <li>if a + 5 then</li>

 <li>2;</li>

 <li>else</li>

 <li>5;</li>

 <li>endif;</li>

</ul>

Semantic Error, If Expression Must Be Boolean

<ul>

 <li>c: real is 9.8 – 2 + 8;</li>

 <li>d: boolean is 7 = f;</li>

</ul>

Semantic Error, Undeclared f

<ul>

 <li>begin</li>

 <li>case b is</li>

 <li>when 1 =&gt; 4.5 + c;</li>

 <li>when 2 =&gt; b;</li>

</ul>

Semantic Error, Case Types Mismatch

<ul>

 <li>others =&gt; c;</li>

 <li>endcase;</li>

 <li>end;</li>

</ul>




Lexical Errors 0

Syntax Errors 0

Semantic Errors 3




You are to submit two files.

<ol>

 <li>The first is a <sub>.zip</sub> file that contains all the source code for the project. The <sub>.zip</sub> file should contain the flex input file, which should be a <sub>.l</sub> file, the bison file, which should be a <sub>.y</sub> file, all <sub>.cc</sub> and <sub>.h</sub> files and a <sub>makefile</sub> that builds the project.</li>

 <li>The second is a Word document (PDF or RTF is also acceptable) that contains the documentation for the project, which should include the following:</li>

 <li>A discussion of how you approached the project</li>

 <li>A test plan that includes test cases that you have created indicating what aspects of the program each one is testing and a screen shot of your compiler run on that test case</li>

 <li>A discussion of lessons learned from the project and any improvements that could be made</li>

</ol>


