Decision Tree Classifier
========================

Author: Farhang Zia  
Graduate Student  
*Department of Computer Science and Engineering,*  
*The Ohio State University, Columbus.*

Contact email: [farhang.bonzo@gmail.com](mailto:farhang.bonzo@gmail.com).

--------------------------------------------------------------------------------------------

Notes:
------

The program takes two files as input; a training file and a testing file. The output of the program is stored in a file named: `decisionTreeOutput.txt`.  
The current program only supports string attributes (the values of the attributes must be of string type. Numerical values are not currently supported. Any numerical values will be treated as strings.).

### Input file format:

* The input files describe a tabular format for the data.
* Values of the different attributes of a single instance/row are delimited by commas.
* The first line (row) of the input file (table) must contain the names of the columns/attributes. Each column name must be unique.
* The last column of the table must contain the class labels.
* Every consequent line (after the first one) corresponds to values of the attributes specified in the first line for a particular instance.

For example if we want to predict whether someone is cool or not, based on their choice of device, social network and laptop, we can have the following data table:

    --------------------------------------
    | Device | Network  | Laptop | Cool? |
    --------------------------------------
    | ipod   | twitter  | mac    | no    |
    | iphone | facebook | pc     | yes   |
    | ipod   | facebook | mac    | yes   |
    | iphone | facebook | mac    | yes   |
    | iphone | facebook | pc     | yes   |
    | iphone | twitter  | pc     | yes   |
    | ipod   | twitter  | mac    | no    |
    | iphone | twitter  | mac    | yes   |
    | none   | twitter  | mac    | no    |
    | none   | facebook | mac    | yes   |
    | ipod   | twitter  | mac    | no    |
    | iphone | facebook | pc     | yes   |
    | iphone | twitter  | mac    | yes   |
    | iphone | twitter  | mac    | yes   |
    | ipod   | twitter  | pc     | no    |
    | none   | twitter  | mac    | no    |
    --------------------------------------

This table will be represented in the training and testing files as:

    Device,Network,Laptop,Cool?
    ipod,twitter,mac,no
    iphone,facebook,pc,yes
    ipod,facebook,mac,yes
    iphone,facebook,mac,yes
    iphone,facebook,pc ,yes
    iphone,twitter,pc,yes
    ipod,twitter,mac,no
    iphone,twitter,mac,yes
    none,twitter,mac,no
    none,facebook,mac,yes
    ipod,twitter,mac,no
    iphone,facebook,pc,yes
    iphone,twitter,mac,yes
    iphone,twitter,mac,yes
    ipod,twitter,pc,no
    none,twitter,mac,no

Sample training (`train.dat`) and testing (`test.dat`) files have been included.  
In the sample files, we're trying to predict which restaurant (*Buck-I-Mart*/*Oxley's*/*Brennan's*/*Oxley's Cafe*) a customer will go to based on the following things:

* How quickly a customer wants the meal (Column name: *speed*. Values that *speed* can take: *quick*, *leisurely*, *medium*).
* Meal preference (Column name: *meal*. Values that *meal* can take: *soup*, *sandwich*, *other*).
* Whether the customer wants coffee or not (Column name: *coffee*. Values that *coffee* can take: *yes*, *no*).
* How many patrons are already eating at *Oxley's* (Column name: *oxley*. Values that *oxley* can take: *0*, *1-3*, *4-8*, *>8*).

And so on.

The column we want to predict is *restaurant*. The class labels are:   

* *Buck-I-Mart*
* *Oxley's*
* *Brennan's*
* *Oxley's Cafe*

### To run the program, execute the following commands in the terminal:

    make clean
    make
    ./dtree train.dat test.dat

After the program finishes execution, open `decisionTreeOutput.txt` to view the output.

### Technical Notes:

The algorithm that builds the decision tree is a recursive algorithm and is implemented in the function `buildDecisionTree()` which is defined in `functions.cpp`. The algorithm works as follows:

    if the sub-table passed to the algorithm is empty
        return NULL;    // since there is no data in the table
    if the sub-table passed to the algorithm is homogeneous (if all the rows have the same value for the last column)
        mark this node as a leaf node;
        label this node with the value of the last column
        return a pointer to this node
    else
        decide a column to split the table on based on information gain
        set the node's splitOn value to this column's name
        for all the values that the splitting column can take:
            create a new node
            set the new node as the current node's child node
            prune the sub-table so that all the rows with this value of the last column are removed
            recursively call the function by passing it the new pruned table and the new node

The splitting column is decided based on information gain. This information gain is calculated using entropy which is a measure of randomness of information. The less random a split leaves the table in, the more information we can gain from it. So we split the table on the column which gives us the most information gain (least entropy).

### Tags

`decision`, `tree`, `decision tree`, `decision tree code`, `decision tree C++`, `decision tree C`, `decision tree C++ code`.
