Download Link: https://assignmentchef.com/product/solved-ee2703-tutorial-2-spice-part-2
<br>
In the last assignment, we have seen the basics of python. In this assignment, you will get introduced to scientific python. Make sure you have completed all the previous homework as well as the assignment before getting started with this assignment.

<h1>2        OOP and Python</h1>

Just like C++, classes help you implement OOP in Python. Classes are the blueprint of objects. They specify what the object can have. For example, say you have a class for Player. The class will tell you that your object has a property named “position”. But does not say what the “position” is. This is useful since a class can parent as many different objects as you want. Each object can have a different “position”.

<table width="642">

 <tbody>

  <tr>

   <td width="642">In [1]: class Player:…:                   position_x = 0…:                   position_y = 0…:…:                        def __init__(self, color):…:                                self.color = color…:…:                          def move(self, distance, direction):…:   if direction == ’right’: …:                self.position_x += distance …: elif ……:                                     …</td>

  </tr>

 </tbody>

</table>

Here, we defined a class Player. Let’s go line by line.

<ol>

 <li>The first line says the it’s a definition of a class and the name of the class is Player</li>

 <li>The next two lines define features of the class. The player has <em>x </em>and <em>y </em> These values are set to 0 by default.</li>

 <li>init () is the constructor. The first argument to it is always self. self refers to the object itself!</li>

 <li>The constructor takes in one extra argument color. The interesting thing here is that, the constructor is declaring a new feature for the class at run-time! In python, you can add features to an object dynamically!</li>

 <li>move() here is a member function of the class. Note that the first argument to a member function should be self.</li>

</ol>

<table width="642">

 <tbody>

  <tr>

   <td width="82">In [2]:</td>

   <td width="160">p1 = Player(’red’)</td>

   <td width="399"><em># Creating a player object</em></td>

  </tr>

  <tr>

   <td width="82">In [3]:</td>

   <td width="160">p1.position_x</td>

   <td width="399"></td>

  </tr>

  <tr>

   <td width="82">Out[3]:</td>

   <td width="160">0</td>

   <td width="399"></td>

  </tr>

  <tr>

   <td width="82">In [4]:</td>

   <td width="160">p1.move(2, ’right’)</td>

   <td width="399"><em># Calling a member function</em></td>

  </tr>

  <tr>

   <td width="82">In [5]:</td>

   <td width="160">p1.position_x</td>

   <td width="399"></td>

  </tr>

  <tr>

   <td width="82">Out[5]:</td>

   <td width="160">2</td>

   <td width="399"></td>

  </tr>

 </tbody>

</table>

Note that, we did not provide the parameter self here. Since first argument to member function is always self, Python passes it automatically.

Though we are seeing Python classes for the first time, you have been using the power of classes even without realizing it. For example, lists that you have been creating are actually objects of the class “List”.

In [6]: l = [1, 4, 5, 2, 3]

In [7]: l.sort()

Here, you are creating an object of the class list in the first line ([…] is the constructor here) and calling a member function of the object in the second line.

<h1>3       List unpacking</h1>

One peculiar thing about Python is that you can return multiple values from a function!

<table width="642">

 <tbody>

  <tr>

   <td width="642">In [8]: def f():…:                      return 1, 2, 3, 4</td>

  </tr>

 </tbody>

</table>

In [9]: r = f(); r

Out[9]: (1, 2, 3, 4)

In [10]: w, x, y, z = f()

f() is returning four values here. How the returned values get stored is heavily depended on the calling statement. In the first call to f(), Python will compile all the return values and give to us a tuple. But in the next call, return values are assigned to separate variables in the order mentioned. What will happen if you try x, y = f()? What about x, *y, z = f() ?

This is called extended unpacking. Python goes even further:

In [11]: a, b, c = [1, 2, 3]

In [12]: i = 1; j = 2

In [13]: i, j = j, i

What are the values of i and j now?

<h2>3.0.1     Homework</h2>

Given a list

l = [ [1, 2], ’hello’ ]

How can you extract the first character of ’hello’ only by using list unpacking? Do it in single statement.

<h1>4       Scientific Python</h1>

What makes python amazing is the huge collection of modules that come with it. For example, Modules like scipy, numpy, matplotlib, sympy and panda make it suitable for scientific computing. numpy helps with numerical computations, scipy provides special functions that will help you with scientific computing and also adds complex number support to all the functions. matplotlib provides sophisticated plotting capabilities.

Most of the underlying implementations of these libraries are in C. This ensures the efficiency of these implementations. But to make your life easy, these C implementations are wrapped in Python and given as python functions which you can directly call from python. Which means they are efficient at the same time easy to use.

<h2>4.1       Arrays vs Lists</h2>

While Python lists are amazing by themselves, they are not always the best data type to depend. The flexibility they provide makes them slow. To make things faster, numpy provides array data type. numpy arrays are lot similar to C arrays. As I already mentioned, the speed come from the fact that the underlying implementation is in C.

Let’s see some examples of arrays:

<table width="642">

 <tbody>

  <tr>

   <td width="642">In [14]: from numpy import *In [15]: array(range(10))Out[15]: array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9]) <em># Note the way it is printed. # The output is explicitly telling you that this is an array and not a list.</em>In [16]: A = array([[1,2,3],[4,5,6],[7,8,9]]); A Out[16]:array([[1, 2, 3], [4, 5, 6],[7, 8, 9]])In [17]: A * 10                                                     <em># Multiplication with a scalar</em>Out[17]:array([[10, 20, 30], [40, 50, 60],[70, 80, 90]])In [18]: A * A                                                      <em># Element by element multiplication</em>Out[18]:array([[ 1, 4, 9], [16, 25, 36],[49, 64, 81]])In [19]: A + 10                                                   <em># Addition with a scalar</em>Out[19]:array([[11, 12, 13], [14, 15, 16],[17, 18, 19]])In [20]: A + A                                                  <em># Addition with a vector</em>Out[20]:array([[ 2, 4, 6], [ 8, 10, 12],[14, 16, 18]])In [21]: ones(10)               <em># Try “ones?” and see what does it do </em>Out[21]: array([1., 1., 1., 1., 1., 1., 1., 1., 1., 1.])In [10]: B = array([ones(3) for i in range(3)]); B Out[10]:</td>

  </tr>

  <tr>

   <td width="642">array([[1., 1., 1.], [1., 1., 1.],[1., 1., 1.]])In [22]: dot(A,B) Out[22]:array([[ 6., 6., 6.], [15., 15., 15.],[24., 24., 24.]])</td>

  </tr>

 </tbody>

</table>

Now, try out the same operations with lists and see what happens. Here is an example:

In [23]: a = [list(i) for i in A]; a

Out[23]: [[1, 2, 3], [4, 5, 6], [7, 8, 9]]

In [24]: a + a

Out[24]: [[1, 2, 3], [4, 5, 6], [7, 8, 9], [1, 2, 3], [4, 5, 6], [7, 8, 9]]

arrays will give you what a mathematician would expect, while list is more for a general programming use. Arrays are quite fast compared to lists. Here are some important facts about arrays:

<ul>

 <li>Array elements are all of one type, unlike lists. This is precisely to improve the speed of computation.</li>

 <li>An array of integers is different from an array of reals or an array of doubles. So you can also use the second argument to create an array of the correct type. Eg:</li>

</ul>

x=array([[1,2],[3,4]], dtype=complex)

<ul>

 <li>Arrays are stored row wize by default. This can be changed by setting some arguments in numpy functions. This storage is consistent with C.</li>

 <li>The size and shape methods give information about arrays. In above examples,</li>

</ul>

<table width="603">

 <tbody>

  <tr>

   <td width="90">x.size</td>

   <td width="513"><em># returns 4</em></td>

  </tr>

  <tr>

   <td width="90">x.shape</td>

   <td width="513"><em># returns (2, 2)</em></td>

  </tr>

  <tr>

   <td width="90">len(x)</td>

   <td width="513"><em># returns 2</em></td>

  </tr>

 </tbody>

</table>

size gives the number of elements in the array. shape gives the dimensions while len gives only the number of rows.

<ul>

 <li>Arrays can be more than two dimensional. This is a big advantage over Matlab and its tribe. Scilab has hypermatrices, but those are slow. Here arrays are intrinsically multi-dimensional</li>

 <li>The dot operator does tensor contraction. The sum is over the last dimension of the first argument and the first dimension of the second argument. In the case of matrices and vectors, this is exactly matrix multiplication.</li>

</ul>

Note that numpy also has a matrix data type. But this is not recommended to use. In fact, the community is planning to remove it in future.

<h3><strong>4.2 </strong>where()</h3>

Sometimes we want to know the indices in a matrix that satisfy some condition. The method to do that in Python is to use the where command. To find the even elements in the above matrix we can do:

<table width="642">

 <tbody>

  <tr>

   <td width="642">In [25]: A=array([[1,2,3],[4,5,6],[7,8,9]]);A Out[25]:array([[1, 2, 3], [4, 5, 6],[7, 8, 9]])In [26]: coords = where(A%2==0) <em># Returns the coords of even elements</em>In [27]: coords                                                           <em># This is a tuple</em>Out[27]: (array([0, 1, 1, 2]), array([1, 0, 2, 1]))In [28]: i, j = where(A%2==0)In [29]: B=array([[6,6,6],[4,4,4],[2,2,2]])In [30]: i, j = where((A&gt;3)&amp;(B&lt;5)&gt;0)</td>

  </tr>

 </tbody>

</table>

What does the last line here do? Break it down to pieces and understand what each piece does. Can you replace the &amp; with and? Why not?

Here is another peculiar thing about arrays.

<table width="642">

 <tbody>

  <tr>

   <td width="642">In [31]: AOut[31]:array([[1, 2, 3], [4, 5, 6],[7, 8, 9]])In [32]: i, j = where(A%2==0); iOut[32]: array([0, 1, 1, 2])In [33]: jOut[33]: array([1, 0, 2, 1])</td>

  </tr>

 </tbody>

</table>

In [34]: A[i, j]

Out[34]: array([2, 4, 6, 8])

Notice what is happening in the last command. Can you do the same with lists?

<h4>4.2.1     Homework</h4>

<ul>

 <li>Explain what is happening in the last command here to your TA.</li>

</ul>

<table width="603">

 <tbody>

  <tr>

   <td width="603">In [35]: AOut[35]:array([[1, 2, 3], [4, 5, 6],[7, 8, 9]])In [36]: A[i][j] Out[36]:array([[4, 5, 6], [1, 2, 3],[4, 5, 6],[4, 5, 6]])</td>

  </tr>

 </tbody>

</table>

<ul>

 <li>Generate an array (of shape (3,3)) of random numbers.</li>

</ul>

<h1>5        Solving Linear Equations</h1>

Solving linear equations are quite simple using numpy. Let’s try and solve:

3<em>x</em><sub>0 </sub>+ <em>x</em><sub>1 </sub>= 9          (1) <em>x</em><sub>0 </sub>+ 2<em>x</em><sub>1 </sub>= 8            (2)

The above equation can be written as:

<em>Ax </em>= <em>b                                                                      </em>(3)

Where,

(4)

(5)

(6)

All you need to do is to create the matrices:

<table width="642">

 <tbody>

  <tr>

   <td width="642">In [37]: import numpy as npIn [38]: A = np.array([[3,1], [1,2]]); A Out[38]:array([[3, 1],[1, 2]])In [39]: b = np.array([9,8]); b Out[39]: array([9, 8])In [40]: x = np.linalg.solve(A, b); xOut[40]: array([2., 3.])</td>

  </tr>

 </tbody>

</table>

The numpy.linalg.solve() solved the set of equations for us.

Note that the first line is same as “import numpy”. But “as np” here allows you to write np.array() instead of numpy.array(). This is simply to save some typing efforts.

<h1>6       Spice – Part 2</h1>

In the last assignment, we read a netlist file and parsed it. In this assignment, we will solve the circuits. We have <em>n </em>node voltages (say <em>V<sub>i </sub></em>; <em>i </em>= 0 <em>to n </em>− 1) and <em>k </em>currents (say <em>I<sub>ij</sub></em>) (the currents through the <em>k </em>voltage sources). The system of equations are:

<ol>

 <li><em>n </em>KCL equations at the <em>n </em></li>

 <li><em>k </em>equations of the type for nodes connected by voltage sources.</li>

</ol>

As long as a loop consisting purely of voltage sources or a node connected purely to current sources does not exist, a unique solution is possible. Write the equations in the form

<em>A </em>· <em>V~ </em>+ <em>B </em>· <em>I~ </em>=<em><sup>~</sup>b                                                            </em>(7)

The node equations take the form

(8)

where the first sum is over the passive branches, the second sum over voltage sources and the third sum is over current sources.

The auxiliary equations take the form

<em>V<sub>i </sub></em>− <em>V<sub>j </sub></em>= <em>E<sub>ij                                                                                                                                     </sub></em>(9)

The dependent sources have similar equations that you can easily derive for yourself.

<ul>

 <li>Explain how a loop consisting purely of voltage sources will result in the system of equations becoming inconsistent.</li>

 <li>Explain how a node connected purely to current sources will result in the system of equations becoming inconsistent.</li>

</ul>

Now, write the equation 7 in the following form:

<table width="640">

 <tbody>

  <tr>

   <td width="195">i.e.,</td>

   <td width="26"></td>

   <td width="36"></td>

   <td width="33"></td>

   <td colspan="2" width="322"><em>Mx </em>= <em>b</em></td>

   <td width="28">(10)</td>

  </tr>

  <tr>

   <td width="195"> <em>a</em>11<sub> </sub><em>…</em> <em>a<sub>n</sub></em>1<sup> </sup><em>…</em><sub> </sub><em>… …</em></td>

   <td width="26"><em>…</em><em>…</em><em>…</em><em>…</em><em>…</em><em>…</em></td>

   <td width="36"><em>a</em>1<em>n</em><em>…</em><em>a</em><em>nn</em><em>…</em><em>…</em><em>…</em></td>

   <td width="33"><em>b</em>11<em>…</em><em>b</em><em>n</em>1000</td>

   <td width="26"><em>… … …</em>000</td>

   <td width="296"><em>b</em><sub>1<em>k </em></sub> <em>V</em><sub>1 </sub>  <em>I</em><sub>1 </sub><em>… </em> <em>… </em>  <em>… </em> <em>b<sub>nk </sub></em> <em>V<sub>n </sub></em>  <em>I<sub>n </sub></em> <em>I</em>1  =  <em>E</em>1 0 0  <em>… </em>  <em>… </em>0               <em>I</em><em>k                                   </em><em>E</em><em>k</em></td>

   <td width="28">(11)</td>

  </tr>

  <tr>

   <td width="195"></td>

   <td width="26"></td>

   <td width="36"></td>

   <td width="33"></td>

   <td width="26"></td>

   <td width="294"></td>

   <td width="30"></td>

  </tr>

 </tbody>

</table>

This matrix needs to be solved to obtain currents and voltages.

Note that this can be readily solved using the method specified in section 5.

<h1>7      Assignment</h1>

<ol>

 <li>Parse the netlist and create list(s) of different components. You may define class(es) for components and create objects for each component to store them nicely. Component name, connected nodes, value etc… can be the features of this(these) class(es). Remember that list elements can be class objects too.</li>

 <li>Create a table of distinct nodes present in the circuit. Assign numbers to the nodes so that they correspond to the rows (columns) of the incidence matrix. You may use a dictionary for doing this. You could then store the node number as the value with the node name as the key.</li>

</ol>

<strong>Note: </strong>You can assume that ground node is always named as GND. The ground node will add an extra equation:

<em>V<sub>k </sub></em>= 0                                                         (12)

where <em>k </em>is the node number of GND. You may keep it as <em>V</em><sub>0 </sub>always.

<ol start="3">

 <li>Construct matrices <em>M </em>and <em>b </em>using numpy arrays.</li>

 <li>Solve the equation <em>Mx </em>= <em>b</em>.</li>

 <li>Print all the unknowns. (All node volatges and current through voltage sources)</li>

 <li>Solve the following circuits with your program:</li>

</ol>

(a) A simple resistive circuit (use <em>R<sub>L </sub></em>= 1<em>,</em>10 and 100Ω)

Figure 1: Resistive circuit

<ol start="7">

 <li>Can you use the same techniques to solve for ac circuits? We only have to interpret the impedance as complex numbers and the solution will follow. We will only work with circuits with single frequency at steady state.</li>

</ol>

Till now, we only had a single command in the netlist (.circuit … .end). We now allow a new command .ac.

.ac V… frequency

This is a single line command. It will appear after the .circuit … .end block and specify the frequency of a voltage source.

We will also modify the way voltage source and current values are given. We will use the following representations:

<table width="603">

 <tbody>

  <tr>

   <td width="180">V… n1 n2 ac <em>V<sub>p</sub></em>−<em><sub>p</sub></em></td>

   <td width="423">phase # ac voltage source</td>

  </tr>

  <tr>

   <td width="180">V… n1 n2 dc v</td>

   <td width="423"># dc voltage source</td>

  </tr>

 </tbody>

</table>

Similar representations will follow for current sources.

Solve the following circuits:

<ul>

 <li>A band-pass filter for the current in the resistor</li>

</ul>

Figure 2: Band-pass filter

<ul>

 <li>A low-pass filter, for the voltage across the load resistor</li>

</ul>

Figure 3: Low-pass filter

Submit a single program on Moodle. It should be able to solve ac as well as dc circuits.