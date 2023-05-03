Download Link: https://assignmentchef.com/product/solved-cs302-assignment-5-balance
<br>
<h1>Description</h1>

Before being an ubiquous communications gadget, a mobile was just a structure made of strings and wires suspending colorful things. This kind of mobile is usually found hanging over cradles of small babies. The figure below illustrates a simple mobile.

It is just a wire, suspended by a string, with an object on each side. It can also be seen as a kind of lever with the fulcrum on the point where the string ties the wire. From the lever principle we know that to balance a simple mobile the product of the weight of the objects by their distance to the fulcrum must be equal. That is <em>W<sub>l </sub></em>×<em>D<sub>l </sub></em>= <em>W<sub>r </sub></em>×<em>D<sub>r </sub></em>where <em>D<sub>l </sub></em>is the left distance, <em>D<sub>r </sub></em>is the right distance, <em>W<sub>l </sub></em>is the left weight and <em>W<sub>r </sub></em>is the right weight. In a more complex mobile the object may be replaced by a sub-mobile, as shown in the next figure. In this case it is not so straightforward to check if the mobile is balanced so we need you to write a program that, given a description of a mobile as input, checks whether the mobile is in equilibrium or not.

<h1>Input</h1>

The input is composed of several lines, each containing 4 integers separated by a single space. The 4 integers represent the distances of each object to the fulcrum and their weights, in the format: <em>W<sub>l </sub>D<sub>l </sub>W<sub>r </sub>D<sub>r </sub></em>If <em>W<sub>l </sub></em>or <em>W<sub>r </sub></em>is zero then there is a sub-mobile hanging from that end and the following lines define the the sub-mobile. In this case we compute the weight of the sub-mobile as the sum of weights of all its objects, disregarding the weight of the wires and strings. If both <em>W<sub>l </sub></em>and <em>W<sub>r </sub></em>are zero then the following lines define two sub-mobiles: first the left then the right one.

<h1>Output</h1>

For each test case, the output must follow the description below. The outputs of two consecutive cases will be separated by a blank line. Write ‘YES’ if the mobile is in equilibrium, write ‘NO’ otherwise.

<h1>Specifications</h1>

<ul>

 <li>Comment your code and your functions</li>

 <li>Make sure your code is memory leak free</li>

 <li>Store your binary tree using the Nodes/reference format (not using an array)</li>

 <li>Use a recursive function to traverse the binary tree to determine if the tree/mobile is balanced</li>

</ul>

<h1>Some More Helpful Details</h1>

You will have the following custom type, each node in the tree will a binTreeNode&lt;int&gt;*, that contains its left and right weight and diameter

template &lt;class Type&gt; struct binTreeNode

{

Type wL, dL, wR, dR; binTreeNode&lt;Type&gt; * left; binTreeNode&lt;Type&gt; * right;

};

You might want to have the following functions (this is up to you, this is just the way I approached this problem)

<ul>

 <li>template &lt;class Type&gt; void buildMobile(binTreeNode&lt;Type&gt; * r, ifstream&amp; infile);</li>

</ul>

This function will recursively build your mobile (tree), this uses a variation of preorder to build the tree, you read in one line of input, allocate a node, assign the values read from the line into the correct fields of this node, and then insert into the tree and recursively continue this until the left or right weight is not 0

<ul>

 <li>template &lt;class Type&gt; int getWeight(binTreeNode&lt;Type&gt; * r);</li>

</ul>

This function compares r’s left side combined weight ×r-&gt;dL with r’s right side combined weight × r-&gt;dR, if they are equal then it returns the sum of r’s left side combined weight with r’s right side weight, otherwise it returns some special value to its parent to denote the r points to a node that does not form a balanced mobile

<strong>Hint: </strong>r’s left or right side combined weight could be r-&gt;wL or r-&gt;wR, but if either one is 0, then you may have to recursively compute the left or right side weight

<ul>

 <li>template &lt;class Type&gt; void destroyTree(binTreeNode&lt;Type&gt; * r);</li>

</ul>

Deallocates the tree, uses a postorder traversal to do this

<h1>Example Output</h1>

$ cat MobileInput01.txt

0 2 0 4

<ul>

 <li>3 0 1</li>

 <li>1 1 1</li>

 <li>4 4 2</li>

</ul>

1 6 3 2

$ cat MobileInput02.txt

0 8 0 5

0 11 0 6

4 1 2 2

8 3 3 8

<ul>

 <li>2 0 1</li>

 <li>8 8 16 5 10 3</li>

</ul>

$ g++ balance.cpp

$ ./a.out

Enter mobile data file: MobileInput01.txt

YES

$ ./a.out

Enter mobile data file: MobileInput02.txt

NO

<h1>Submission</h1>

Upload your source file using the following naming convention LastName_FirstName_A5.cpp by the deadline