S-Box Analyser
=============
*S-Box Analyser*
is a toolkit to analyse and study the properties of **any** given substitution boxes.

Consider **Data Encryption Standard**, which was secure for around 18 years until [linear cryptanalysis](https://www.wikiwand.com/en/Linear_cryptanalysis) was developed  to break the cipher. The S-boxes of DES, however, haven't been released officially yet. Hence, a tool is needed to sudy and analyse substitution boxes. 

Using the look-up table of an S-Box, S-Box Analyser gets the following properties for every ***out***-bit boolean function:

- Alegbraic Normal Form
- Truth Table
- Sequence
- Walsh Hamadard Coefficients
- Non-linearity
- Degree
- Terms present in the boolean function

In the recent years, lightweight ciphers like PRESENT have emerged as trend, which focus on easy hardware implementation, beside the security aspects. A new technique to develop secure S-boxes is using Qausi-groups.

The update includes the crypt-analysis of Quasi-groups and results to verify the security of Q-S-boxes.

#### Table of Contents
  - main.py : Gateway to the toolkit.
  - qsbox_main.py: Q-S-box analyser.
  - properties.py : A place where all properties are being calculated. 
  - tables : Where one stores the look-up tables.
  - results: The analysis reports for every substitution box.

---
#### Setting up the thing
1. Place the S-Box look-up tables in *tables* named as sbox_*[number]*.txt as already done for DES.
2. Run ``` python main.py ```
3. The required results will be stored in *results* as sbox_*[number]*.txt

**Note**: 
* The files in *tables* might have different structure. Make sure to change line 132 of *properties.py* accordingly.
* The digits in each term denote the subscript of variable. Presence of '0' denotes 1 in the boolean function. Thus, Y<sub>i</sub> is denoted by i.
* The txt files already included here are for the DES S-Boxes. Make sure to delete the previous files before analysing new S-Boxes.

#### Using the Code
Using the script is pretty simple. 
User can use *main.py* to operate on the toolkit through shell. Alternatively, one can import the properties module to study specific properties.

```
import properties

with open("sbox_analyser/tables/sbox_1.txt", 'r') as table:
	look_up = table.read()
look_up = look_up.split()

rows = [ look_up[17:33], look_up[34:50], look_up[51:67], look_up[68:84] ] #Should be changed according to format of txt.

fn_map = properties.function_generate(rows)

for i in xrange(OUT):
    print 'X' + str(i) + '\n:'
    print fn_map[i]
```
##### Version: 1.1
To-DO:

* LFSR Analyser
* Q-S-box Generator

#### Contribution
Feel free to report errors and submit pull requests. Contributions are welcome.
