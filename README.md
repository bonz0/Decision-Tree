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
The current program only supports string attributes (the values of the attributes must be string. Numerical values are not currently supported).

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
In the sample files, we're trying to predict which restaurant (*Buck-I-Mart*/*Oxley's*/*Brennan's*/*Oxley's Cafe*) a customer will go to based on:

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

### Tags

`decision`, `tree`, `decision tree`, `decision tree code`, `decision tree C++`, `decision tree C`, `decision tree C++ code`.