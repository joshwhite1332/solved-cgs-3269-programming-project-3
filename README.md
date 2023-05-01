Download Link: https://assignmentchef.com/product/solved-cgs-3269-programming-project-3
<br>



Using C programming language write a program that simulates the Tiny Machine Architecture. Your code must implement the basic instruction set that the Tiny Machine Architecture adheres to (LOAD[1], ADD[2], STORE[3], SUB[4], IN[5], OUT[6], END[7], JMP[8], SKIPZ[9]). Each piece of the architecture must be accurately represented in your code (Instruction Register, Program Counter, Memory Address Register, Data Memory, Memory Data Register, and Accumulator). Data Memory will be represented by a 0-9 array. Your Program Counter will begin at 10.




For the sake of simplicity Program Memory and Data Memory may be implemented as separate arrays.




Hint: Implementing a struct for your Instructions and an array of these structs as your Program Memory greatly simplifies this program.




Example:




typedef struct {

int opCode, deviceOrAddress;

} Instruction;




Instruction programMemory[MAXPROGRAMSIZE];







<strong><u>Input Specifications</u></strong>

<strong><u> </u></strong>

Your simulator must run from the command line with a single input file as a parameter to main. This file will contain a sequence of instructions for your simulator to assemble (store in “program memory”) and then run via the fetch/execute cycle.




Example:




5 5                   //IN 5

6 7                   //OUT 7

3 0                   //STORE 0

5 5                   //IN 5

6 7                   //OUT 7

3 1                   //STORE 1

1 0                   //LOAD 0

4 1                   //SUB 1

3 0                   //STORE 0

6 7                   //OUT 7

1 1                   //LOAD 1

6 7                   //OUT 7

7 0                   //END







<strong><u>Output Specifications</u></strong>

<strong><u> </u></strong>

Your simulator should provide output according to the input file. Along with this output your program should provide status messages identifying details on the workings of your simulator. Output text does not have to reflect my example word-for-word, but please provide detail on the program as it runs in a readable format that does not conflict with the actual output of your simulator. After each instruction print the current state of the Program Counter, Accumulator, and Data Memory. The INPUT instruction is the only one that should prompt an interaction from the user.




Example:




Assembling Program…

Program Assembled.




Run.




PC = 10 | A = NULL | MEM = [0, 0, 0, 0, 0, 0, 0, 0, 0, 0]




/* input value */

<em>X</em>

<em>            </em>

<em>            </em>PC = 11 | A = <em>X</em> | MEM = [0, 0, 0, 0, 0, 0, 0, 0, 0, 0]




/* outputting accumulator to screen */

<em>X</em>

<em>            </em>PC = 12 | A = <em>X </em>| MEM = [0, 0, 0, 0, 0, 0, 0, 0, 0, 0]




<em>            </em>/* storing accumulator to memory location <em>0</em> */

PC = 13 | A = <em>X </em>| MEM = [<em>X</em>, 0, 0, 0, 0, 0, 0, 0, 0, 0]




… etc

<em>            </em>

Program complete.







For instance, to implement FETCH and instruction LOAD you must implement each step:




<strong>FETCH  </strong>

MAR ß PC

PC ß PC + 1

MDR ß M [MAR]

IR ß MDR




<strong>LOAD (Execute cycle)</strong>

MAR ß IR.ADDR */

MDR ß MEM[MAR] */

A ß  MDR */




Note: Lecture 1 describes the instruction set architecture of the Tiny Machine.