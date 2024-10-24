# Asic-Design-Class
<details>
 
<summary> <h2>Task-1</h2> </summary>

## Task-1: Write a C code and compile it on gcc compiler.

This repository contains a simple C program that calculates the sum of n numbers.

File: Sum1tox.c
This is the main source file containing the C program.
Compilation: Compiled using gcc
`gcc -o sum1tox Sum1tox.c`

`-o sum1tox`: Specifies the output file name as sum1tox

Sum1tox.c: Input source file name

Execution: After compilation, execute the program with the command `./sum1tox.`


![Screenshot 2024-07-17 092149](https://github.com/user-attachments/assets/af84717b-b0c1-4f8a-9d30-8d80195b5b6d)




## Compile same code and run it onto RISC-V gcc compiler.

**Step:1**

Compiled the c code on RISC-V compiler using `cat Sum1tox.c`. 

![Screenshot 2024-07-18 195246](https://github.com/user-attachments/assets/6899beb4-d383-4b27-a502-3cd120e7b846)

**Step:2**

Then convert the C program to assembly code using `riscv64-unknown-elf-objdump -d sum1tox`
and after that use this command: `riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum1tox Sum1tox.c` to compile the program.

**Step:3**

Finally we use  `riscv64-unknown-elf-objdump -d sum1tox | less` to dump the assembly code in terminal.

![Screenshot 2024-07-18 192606](https://github.com/user-attachments/assets/94ad7db1-6a88-4d29-9afa-be0ba5166ffe)

Now we can see that our output is same at 1018c location using both gcc and RISCV compiler.

</details>

<details>
 
<summary> <h2>Task-2</h2> </summary>

## Task-2:To find the output of C program on the RISC V Compiler and debug each instruction using the Spike command.

**Step-1:** Firstly we verified that our c code result come from gcc and Risc-V compiler are equal and then we start debugging using `spike -d pk sum1tox` command.

![Screenshot 2024-07-21 142420](https://github.com/user-attachments/assets/d04d0992-002d-437e-98b4-f4af68473c0d)

**Step-2:** The Assembly code of our C program is:

![Screenshot 2024-07-21 104126](https://github.com/user-attachments/assets/832f190c-048a-46c8-91a8-3fc81b4e1869)



**Step-3:** From the assembly code we can see that the first address is at 100b0. To debug it we use the following command: `until pc 0 100b0`
Our first instruction is reg 0. To check it's content we use following code: `reg 0 a0`. Similarly we can get content of each and every line of our assembly code.

![Screenshot 2024-07-21 104507](https://github.com/user-attachments/assets/389df2cf-23ac-42f1-8ee6-cf2b2b22f17a)

</details>
 
<details>
 
<summary> <h2>Task-3</h2> </summary>

## Task-3: To run assembly instructions using a given verilog code for a risc-V processor.


| Operation         | RISC-V ISA      | Hardcoded ISA   | Instruction Format |
|-------------------|-----------------|-----------------|---------------------|
| ADD r8, r9, r10   | 32’h00A482B3    | 32'h02208300    | R-type              |
| SUB r10, r8, r9   | 32’h409482B3    | 32'h02209380    | R-type              |
| AND r9, r8, r10   | 32’h00A4C2B3    | 32'h0230A400    | R-type              |
| OR r8, r9, r5     | 32’h005482B3    | 32'h02513480    | R-type              |
| XOR r8, r8, r4    | 32’h004482B3    | 32'h0240C500    | R-type              |
| SLT r00, r1, r4   | 32’h004002B3    | 32'h02415580    | R-type              |
| ADDI r02, r2, 5   | 32’h00510113    | 32'h00520600    | I-type              |
| SW r2, r0, 4      | 32’h00412023    | 32'h00209181    | S-type              |
| SRL r06, r01, r1  | 32’h00119533    | 32'h00271803    | R-type              |
| BNE r0, r0, 20    | 32’h01400063    | 32'h01409002    | B-type              |
| BEQ r0, r0, 15    | 32’h00F00063    | 32'h00F00002    | B-type              |
| LW r03, r01, 2    | 32’h00210183    | 32'h00208681    | I-type              |
| SLL r05, r01, r1  | 32’h00109533    | 32’h00208783    | R-type              |

The following commands were used to run the verilog code:

![Screenshot 2024-07-28 144818](https://github.com/user-attachments/assets/60344dc3-8cee-4b74-9d50-9fba65bd99e1)

The given hardcoded instructions are:

![Screenshot 2024-07-28 115648](https://github.com/user-attachments/assets/2984cac6-79ba-4429-a171-baa32e2f4117)

Our verilog program instructions are:

![Screenshot 2024-07-28 125110](https://github.com/user-attachments/assets/a5c481a8-89f9-4d21-83bd-02b378466c7e)


Here in this code there are some mismatch in the below images because the code which we are using is already hardcoded:


`ADD R8, R9, R10`

This is the waveform of the given hardcoded verilog program:

![Screenshot 2024-07-28 115909](https://github.com/user-attachments/assets/a25b54d1-dc1d-4d60-8591-835493c83d55)

This is the waveform of our verilog program:

![Screenshot 2024-07-28 140238](https://github.com/user-attachments/assets/b3905a23-b725-4876-af62-8a26068ca64e)


`SUB R10, R8, R9`

This is the waveform of the given hardcoded verilog program:

![Screenshot 2024-07-28 115942](https://github.com/user-attachments/assets/3adb8b54-269f-4fae-a213-16f37cd9f701)

This is the waveform of our verilog program:

![Screenshot 2024-07-28 140315](https://github.com/user-attachments/assets/fbe28a5c-a1d7-471e-a477-2dd75a885a2d)

`AND R9, R8, R10`

 This is the waveform of the given hardcoded verilog program:

 ![Screenshot 2024-07-28 120013](https://github.com/user-attachments/assets/a7426e2c-fc90-4047-ad83-e081414119ec)

 This is the waveform of our verilog program:

 ![Screenshot 2024-07-28 140330](https://github.com/user-attachments/assets/fcbfebaa-0100-4f14-9a92-1c55127a898b)


 `OR R8, R9, R5`

  This is the waveform of the given hardcoded verilog program:

  ![Screenshot 2024-07-28 120035](https://github.com/user-attachments/assets/80f8c2a2-03b9-4c4b-8bd5-49101ffaaad3)

  This is the waveform of our verilog program:

  ![Screenshot 2024-07-28 140347](https://github.com/user-attachments/assets/4f63a635-3a6d-4f5f-909c-483181f553b3)

  `XOR r8, r8, r4`

  This is the waveform of the given hardcoded verilog program:

  ![Screenshot 2024-07-28 120128](https://github.com/user-attachments/assets/de4b3cf8-4eef-4868-b5ef-3d10d976c579)

  This is the waveform of our verilog program:

  ![Screenshot 2024-07-28 140403](https://github.com/user-attachments/assets/aefa8bf4-491e-42f4-a685-09576e3f7ff2)

  `SLT r00, r1, r4 `

  This is the waveform of the given hardcoded verilog program:

  ![Screenshot 2024-07-28 120156](https://github.com/user-attachments/assets/7c3b22f6-db6e-4aaf-9f55-b564e8c6f8ad)

  This is the waveform of our verilog program:

  ![Screenshot 2024-07-28 140426](https://github.com/user-attachments/assets/fa74712f-9fab-4c9b-939b-f091414b9859)

  `ADDI r02, r2, 5 `

  This is the waveform of the given hardcoded verilog program:

  ![Screenshot 2024-07-28 120220](https://github.com/user-attachments/assets/32fefec3-ba90-4f8d-bdd3-c453cdcfc516)

  This is the waveform of our verilog program:

  ![Screenshot 2024-07-28 140442](https://github.com/user-attachments/assets/5c2c48df-ea70-45ef-8f44-6238c33ff02c)

  `SW r2, r0, 4`

   This is the waveform of the given hardcoded verilog program:

   ![Screenshot 2024-07-28 120245](https://github.com/user-attachments/assets/71704811-25de-4352-a6b1-8472d0988329)

   This is the waveform of our verilog program:

   ![Screenshot 2024-07-28 140458](https://github.com/user-attachments/assets/5965733c-a2c4-435b-90a3-47caa206a3c7)

   `SRL r06, r01, r1`

   This is the waveform of our verilog program:

   ![Screenshot 2024-07-28 140514](https://github.com/user-attachments/assets/ef1666db-b95a-4452-b19d-763d206200fd)

   `BNE r0, r0, 20`

   This is the waveform of our verilog program:

   ![Screenshot 2024-07-28 184617](https://github.com/user-attachments/assets/69ce370e-a8cd-4f9e-b309-208f7ef74fed)

   `BEQ r0, r0, 15`

   This is the waveform of our verilog program:

   ![Screenshot 2024-07-28 184650](https://github.com/user-attachments/assets/0f774abb-2bb4-4771-8733-9a26d3261b87)

</details>
 

<details>
 
<summary> <h2>Task-4</h2> </summary>

## Task:4-->> To write an Application in C, compile it with gcc and Risc-v gcc
**Application:To design a Voting Machine which takes input from users and give final result according to inputs.** 

**Step:1-->> C code of the application**

> code

``` c
#include<stdio.h> 

int main() { 
    char n[10]; 
    int a[10], csp = 0, bjp = 0, bsp = 0, sp = 0, nota = 0, win = 0;

    again: 
    printf("\nPlease enter your name:"); 
    scanf("%s", n);

    printf("\nHello %s please enter your age:", n); 
    scanf("%d", &a[0]); // a[0] for age.

    if(a[0] >= 18) { 
        printf("\nYou are eligible for voting!\nLet's start the process."); 
        printf("\nEnter 1-CONGRESS\nEnter 2-BJP\nEnter 3-BAHUJAN SAMAJWADI PARTY\nEnter 4-SAMAJWADI PARTY\nEnter 5-NOTA\n:"); 
        scanf("%d", &a[1]); // a[1] for your vote.

        if(a[1] == 1) csp++; 
        if(a[1] == 2) bjp++; 
        if(a[1] == 3) bsp++; 
        if(a[1] == 4) sp++; 
        if(a[1] == 5) nota++;

        printf("\nAll process is completed! Here is your receipt."); 
        printf("\nReceipt:\nName: %s\nAge: %d", n, a[0]);

        if(a[1] == 1) printf("\nVote: CONGRESS"); 
        if(a[1] == 2) printf("\nVote: BJP"); 
        if(a[1] == 3) printf("\nVote: BAHUJAN SAMAJWADI PARTY"); 
        if(a[1] == 4) printf("\nVote: SAMAJWADI PARTY"); 
        if(a[1] == 5) printf("\nVote: NOTA");

        printf("\nThanks for visiting :)");

        nefv: 
        printf("\nEnter 0 for exit\nEnter 1 for allowing another person to vote:"); 
        scanf("%d", &a[2]);

        if(a[2] == 0) { 
            printf("\nResult of voting\nCONGRESS = %d\nBJP = %d\nBAHUJAN SAMAJWADI PARTY = %d\nSAMAJWADI PARTY = %d\nNOTA = %d", csp, bjp, bsp, sp, nota);
            win = ((csp > bjp) && (csp > bsp) && (csp > sp)) ? csp :
                  ((bjp > csp) && (bjp > bsp) && (bjp > sp)) ? bjp :
                  ((bsp > bjp) && (bsp > csp) && (bsp > sp)) ? bsp :
                  ((sp > bjp) && (sp > csp) && (sp > bsp)) ? sp : nota;

            if(win == bjp) printf("\nThe Winner is BJP!"); 
            if(win == csp) printf("\nThe Winner is CONGRESS!"); 
            if(win == bsp) printf("\nThe Winner is BAHUJAN SAMAJWADI PARTY!"); 
            if(win == sp) printf("\nThe Winner is SAMAJWADI PARTY!"); 
            if((win == nota) && (bjp == 0) && (csp == 0) && (bsp == 0) && (sp == 0)) 
                printf("\nNo one got any votes, that's why voting is postponed and voting dates will be available soon!"); 
            if(win < nota) printf(", but NOTA got more votes than the winner.");
        } 
        
        if(a[2] == 1) 
            goto again; 
    } else { 
        printf("\nYou are not eligible for voting.\nThanks for visiting!"); 
        goto nefv; 
    } // Not eligible for voting.

    return 0; 
}
```

**Step:2-->> Compilation using gcc compiler: For this we used command `gcc -o Asic_Application Application.c`**

file:///home/vsduser/Pictures/Screenshot%20from%202024-08-14%2018-37-17.png![image](https://github.com/user-attachments/assets/d8b7ada4-b82c-4cea-b70c-563c66c6be24)



**Step:3-->> Compilation using risc-v by O1 with `riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o Asic_Application Application.c` command**


``` c
vsduser@vsduser-VirtualBox:~/Downloads$ riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o Asic_Application Application.c 
vsduser@vsduser-VirtualBox:~/Downloads$ gcc Application.c 
vsduser@vsduser-VirtualBox:~/Downloads$ ./a.out

Please enter your name:Huzaifa

Hello Huzaifa please enter your age:23

You are eligible for voting!
Let's start the process.
Enter 1-CONGRESS
Enter 2-BJP
Enter 3-BAHUJAN SAMAJWADI PARTY
Enter 4-SAMAJWADI PARTY
Enter 5-NOTA
:5

All process is completed! Here is your receipt.
Receipt:
Name: Huzaifa
Age: 23
Vote: NOTA
Thanks for visiting :)
Enter 0 for exit
Enter 1 for allowing another person to vote:0

Result of voting
CONGRESS = 0
BJP = 0
BAHUJAN SAMAJWADI PARTY = 0
SAMAJWADI PARTY = 0
NOTA = 1
No one got any votes, that's why voting is postponed and voting dates will be available soon!
```

**Step:4-->> To debug each instruction using the O1 by `spike pk` command**

``` c
vsduser@vsduser-VirtualBox:~/Downloads$ riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o Asic_Application
vsduser@vsduser-VirtualBox:~/Downloads$ spike pk Asic_Application 
bbl loader

Please enter your name:Huzaifa

Hello Huzaifa please enter your age:23

You are eligible for voting!
Let's start the process.
Enter 1-CONGRESS
Enter 2-BJP
Enter 3-BAHUJAN SAMAJWADI PARTY
Enter 4-SAMAJWADI PARTY
Enter 5-NOTA
:5

All process is completed! Here is your receipt.
Receipt:
Name: Huzaifa
Age: 23
Vote: NOTA
Thanks for visiting :)
Enter 0 for exit
Enter 1 for allowing another person to vote:0

Result of voting
CONGRESS = 0
BJP = 0
BAHUJAN SAMAJWADI PARTY = 0
SAMAJWADI PARTY = 0
NOTA = 1
No one got any votes, that's why voting is postponed and voting dates will be available soon!

```

**We can see that output coming from gcc compilation, Risc-v compilation and after debugging by O1 using Spike command is same** 


**Step:5-->> Finally we use `riscv64-unknown-elf-objdump -d Asic_Application | less` to dump the assembly code in terminal.**

file:///home/vsduser/Pictures/Screenshot%20from%202024-08-14%2017-49-09.png![image](https://github.com/user-attachments/assets/c3f72645-4142-4bae-ae0f-0738cf214b18)

</details>

<details>
 
<summary> <h2>Task-5</h2> </summary>

## Task:5-->> To make a Risc-V processor core using TL-Verilog.

TL-Verilog (Transaction-Level Verilog) is an advanced hardware description language that builds upon traditional Verilog, aimed at enhancing productivity and abstraction in digital design. It's particularly suited for complex digital systems, such as processors, where managing and optimizing the design process can be challenging.

Key Concepts of TL-Verilog:

**Transaction-Level Abstraction:**

TL-Verilog focuses on modeling the movement of data at a higher level of abstraction, known as transaction-level modeling. Unlike traditional Verilog, which often emphasizes individual signals and their timing, TL-Verilog deals with transactions—units of data movement between different parts of a digital system. This abstraction simplifies design by allowing engineers to think about the overall data flow rather than individual signal toggles.

**Pipeline Constructs:**

One of the major innovations in TL-Verilog is its approach to pipelining. Pipelines are fundamental in digital systems, particularly in CPUs and other processors, where multiple instructions or operations are processed in parallel. In TL-Verilog, pipelines are explicitly defined and managed, making it easier to visualize, implement, and optimize complex pipelines, reducing the chances of errors that might occur with manual pipeline management in traditional Verilog.

**Implicit Register Management:**

In traditional Verilog, designers must explicitly declare and manage registers—storage elements that hold data. TL-Verilog, however, introduces the concept of implicit registers, where the language automatically handles register allocation based on the designer’s high-level description. This reduces the amount of code that needs to be written and makes the design cleaner and easier to understand.

**Cleaner and Simplified Syntax:**

TL-Verilog offers a more streamlined syntax compared to traditional Verilog, which can be verbose and prone to errors. This simplification not only makes the code easier to write and read but also helps in reducing bugs and speeding up the overall development process.

**Scalability:**

The language is designed with scalability in mind. As digital designs grow in complexity, managing them in traditional Verilog can become increasingly difficult. TL-Verilog’s higher-level constructs and abstractions allow for more efficient management of large-scale designs, making it easier to scale up projects.

**Compatibility with Verilog:**

TL-Verilog is fully compatible with traditional Verilog. This means that designers can integrate TL-Verilog into their existing Verilog-based workflows without needing to completely overhaul their current design processes. This compatibility also allows for gradual adoption, where designers can start using TL-Verilog in parts of their design while still relying on traditional Verilog where necessary.

## Risc-V Architecture:

![Screenshot 2024-08-21 121029](https://github.com/user-attachments/assets/143cee21-5214-4f33-a7dc-cb82efe8ff0e)

> Code
``` c

\m4_TLV_version 1d: tl-x.org
\SV
   // This code can be found in: https://github.com/stevehoover/RISC-V_MYTH_Workshop
   
   m4_include_lib(['https://raw.githubusercontent.com/BalaDhinesh/RISC-V_MYTH_Workshop/master/tlv_lib/risc-v_shell_lib.tlv'])

\SV
   m4_makerchip_module   // (Expanded in Nav-TLV pane.)
\TLV

   // /====================\
   // | Sum 1 to 9 Program |
   // \====================/
   //
   // Program for MYTH Workshop to test RV32I
   // Add 1,2,3,...,9 (in that order).
   //
   // Regs:
   //  r10 (a0): In: 0, Out: final sum
   //  r12 (a2): 10
   //  r13 (a3): 1..10
   //  r14 (a4): Sum
   // 
   // External to function:
   m4_asm(ADD, r10, r0, r0)             // Initialize r10 (a0) to 0.
   // Function:
   m4_asm(ADD, r14, r10, r0)            // Initialize sum register a4 with 0x0
   m4_asm(ADDI, r12, r10, 1010)         // Store count of 10 in register a2.
   m4_asm(ADD, r13, r10, r0)            // Initialize intermediate sum register a3 with 0
   // Loop:
   m4_asm(ADD, r14, r13, r14)           // Incremental addition
   m4_asm(ADDI, r13, r13, 1)            // Increment intermediate register by 1
   m4_asm(BLT, r13, r12, 1111111111000) // If a3 is less than a2, branch to label named <loop>
   m4_asm(ADD, r10, r14, r0)            // Store final result to register a0 so that it can be read by main program
   
   m4_asm(SW, r0, r10, 100)             //Command to check for Load instruction
   m4_asm(LW, r15, r0, 100)             // Command to check for the Store Instruction
   
   
   // Optional:
   // m4_asm(JAL, r7, 00000000000000000000) // Done. Jump to itself (infinite loop). (Up to 20-bit signed immediate plus implicit 0 bit (unlike JALR) provides byte address; last immediate bit should also be 0)
   m4_define_hier(['M4_IMEM'], M4_NUM_INSTRS)

   |cpu
      @0
         $reset = *reset;
         $clk_Abu = *clk;



      // YOUR CODE HERE
      @0
         $pc[31:0] = >>1$reset ? 0 
                    : >>3$valid_taken_br ? >>3$br_target_pc
                    : >>3$valid_load ? >>3$pc_inc
                    : >>1$pc_inc;
         
         $start = !$reset && >>1$reset;
     
         
      @1
         $pc_inc[31:0] = $pc + 32'd4;
         //Fetch logic
         
         $imem_rd_addr[M4_IMEM_INDEX_CNT -1 : 0] = $pc[M4_IMEM_INDEX_CNT +1 : 2];
         $imem_rd_en = !$reset;
         $instr[31:0] = $imem_rd_data[31:0];
         
         // Instruction type 

         $is_i_instr = $instr[6:2] ==? 5'b0000x ||
                       $instr[6:2] ==? 5'b001x0 ||
                       $instr[6:2] ==? 5'b11100 ;

         $is_r_instr = $instr[6:2] ==? 5'b01011 ||
                       $instr[6:2] ==? 5'b01100 ||
                       $instr[6:2] ==? 5'b01110 ||
                       $instr[6:2] ==? 5'b10100 ;
         
         $is_u_instr = $instr[6:2] ==? 5'b0x101;
     
         $is_j_instr = $instr[6:2] ==? 5'b11011;

         $is_b_instr = $instr[6:2] ==? 5'b11000;
         
         $is_s_instr = $instr[6:2] ==? 5'b0100x;
         
                  
         
         
         //decode logic for immediate values
         
         $imm[31:0] = $is_i_instr ? { {21{$instr[31]}}, $instr[30:20]}:
                      $is_s_instr ? { {21{$instr[31]}}, $instr[30:25], $instr[11:7]} :
                      $is_b_instr ? { {20{$instr[31]}}, $instr[7], $instr[30:25], $instr[11:8], 1'b0} :
                      $is_u_instr ? {$instr[31:12], 12'b0} :
                      $is_j_instr ? { {12{$instr[31]}}, $instr[19:12], $instr[20], $instr[30:21], 1'b0} :
                      32'b0;         
                
         //decoding other instruction elements
         
         $opcode[6:0] = $instr[6:0] ;
         
         $rd_valid = $is_r_instr || $is_j_instr || $is_i_instr || $is_u_instr;
         $rs2_valid = $is_r_instr || $is_s_instr || $is_b_instr;
         $rs1_valid = $is_r_instr || $is_i_instr || $is_b_instr || $is_s_instr;
         $funct3_valid = $is_r_instr || $is_i_instr || $is_b_instr || $is_s_instr;
         $funct7_valid = $is_r_instr;
         
         ?$rd_valid
            $rd[4:0] = $instr[11:7];
         
         ?$rs2_valid
            $rs2[4:0] = $instr[24:20];
         ?$rs1_valid
            $rs1[4:0] = $instr[19:15];
         ?$funct3_valid
            $funct3[2:0] = $instr[14:12];
         ?$funct7_valid
            $funct7[6:0] = $instr[31:25];
            
         //decoding instructions

         $dec_bits[10:0] = {$funct7[5],$funct3,$opcode};

         //ADD Instructions 
         $is_addi = $dec_bits ==? 11'bx_000_0010011;
         $is_add  = $dec_bits ==? 11'b0_000_0110011;

         //Subtract Instructions
         $is_sltiu  = $dec_bits ==? 11'bx_011_0010011;
         $is_xori   = $dec_bits ==? 11'bx_100_0010011;
         $is_ori    = $dec_bits ==? 11'bx_110_0010011;
         $is_andi   = $dec_bits ==? 11'bx_111_0010011;
         $is_slli   = $dec_bits ==? 11'b0_001_0010011;
         $is_srli   = $dec_bits ==? 11'b0_101_0010011;
         $is_sral   = $dec_bits ==? 11'b1_101_0010011;
         $is_sub    = $dec_bits ==? 11'b1_000_0110011;
         $is_sll    = $dec_bits ==? 11'b0_001_0110011;
         $is_slt    = $dec_bits ==? 11'b0_010_0110011;
         $is_sltu   = $dec_bits ==? 11'b0_011_0110011;
         $is_xor    = $dec_bits ==? 11'b0_100_0110011;
         $is_srl    = $dec_bits ==? 11'b0_101_0110011;
         $is_sra    = $dec_bits ==? 11'b1_101_0110011;
         $is_or     = $dec_bits ==? 11'b0_110_0110011;
         $is_and    = $dec_bits ==? 11'b0_111_0110011;
         
         //Branch Instructions 
         //BEQ - Branch on equal 
         $is_beq = $dec_bits ==? 11'bx_000_1100011;
         //BNE - Branch not equal
         $is_bne = $dec_bits ==? 11'bx_001_1100011;
         //BLT - Branch on less than
         $is_blt = $dec_bits ==? 11'bx_100_1100011;
         //BGE - Branch on greater than
         $is_bge = $dec_bits ==? 11'bx_101_1100011;
         //BLTU - Branch on less than equal
         $is_bltu = $dec_bits ==? 11'bx_110_1100011;
         //BGEU - Branch on greater than equal
         $is_bgeu = $dec_bits ==? 11'bx_111_1100011;
         
         //LOAD INSTRUCTION
         $is_load   = $dec_bits ==? 11'bx_010_0000011;

         //Miscellaneous Instructions 
         $is_lui    = $dec_bits ==? 11'bx_xxx_0110111;
         $is_auipc  = $dec_bits ==? 11'bx_xxx_0010111;
         $is_jal    = $dec_bits ==? 11'bx_xxx_1101111;
         $is_jalb   = $dec_bits ==? 11'bx_000_1100111;
         $is_sb     = $dec_bits ==? 11'bx_000_0100011;
         $is_sh     = $dec_bits ==? 11'bx_001_0100011;
         $is_sw     = $dec_bits ==? 11'bx_010_0100011;
         $is_slti   = $dec_bits ==? 11'bx_010_0010011;

         
                  
      @2
         
         
         $rf_rd_en1 = $rs1_valid;
         $rf_rd_index1[4:0] = $rs1;
         
         $rf_rd_en2 = $rs2_valid;
         $rf_rd_index2[4:0] = $rs2;
         
         //operating on the read values
         
         $src1_value[31:0] = (>>1$rf_wr_index == $rf_rd_index1) && >>1$rf_wr_en
                             ? >>1$result :
                             $rf_rd_data1;
          
         $src2_value[31:0] = (>>1$rf_wr_index == $rf_rd_index2) && >>1$rf_wr_en
                             ? >>1$result :
                             $rf_rd_data2;
         
         $taken_br = $is_beq ? ($src1_value == $src2_value) :
                     $is_bne ?($src1_value != $src2_value) :
                     $is_bltu ? ($src1_value <  $src2_value) :
                     $is_bgeu ? ($src1_value >= $src2_value) :
                     $is_blt ? (($src1_value < $src2_value) ^ ($src1_value[31] != $src2_value[31])) :
                     $is_bgeu ? (($src1_value >= $src2_value) ^ ($src1_value[31] != $src2_value[31])) :
                            1'b0;
         
         
         $br_target_pc[31:0] = $taken_br? $pc + $imm : 0;
         
         
         
      @3
         
         

         $result[31:0] = $is_add ?
                         $src1_value[31:0] + $src2_value[31:0] :
                         $is_sub ?
                         $src1_value[31:0] - $src2_value[31:0] :
                         $is_and ?
                         $src1_value[31:0] & $src2_value[31:0] :
                         $is_or ?
                         $src1_value[31:0] | $src2_value[31:0] :
                         $is_xor ?
                         $src1_value[31:0] ^ $src2_value[31:0] :
                         $is_addi ? 
                         $src1_value[31:0] + $imm[31:0] :
                         $is_andi ?
                         $src1_value[31:0] & $imm[31:0] :
                         $is_ori ?
                         $src1_value[31:0] | $imm[31:0] :
                         $is_xori ?
                         $src1_value[31:0] ^ $imm[31:0] :

                         //Load and store 
                         $is_load ?
                         $src1_value[31:0] + $imm[31:0] :
                         $is_s_instr ?
                         $src1_value[31:0] + $imm[31:0] :

                         //ALU for some shift operations
                         $is_slli ?
                         $src1_value[31:0] << $imm[5:0] :
                         $is_srli ?
                         $src1_value[31:0] >> $imm[5:0] :
                         $is_sll ?
                         $src1_value[31:0] << $src2_value[4:0] :
                         $is_srl ?
                         $src1_value[31:0] >> $src2_value[4:0] :

                         //ALU for some other operations
                         $is_sltu ? $sltu_rslt :
                         $is_sltiu ? $sltiu_rslt :
                         $is_lui ?
                         {$imm[31:12], 12'b0} :
                         $is_auipc ?
                         $pc + $imm :
                         $is_jal ?
                         $pc + 32'd4 :
                         $is_jalr ?
                         $pc + 32'd4 :
                         $is_srai ?
                         { {32{$src1_value[31]}}, $src1_value} >> $imm[4:0] :
                         $is_slt ?
                         ($src1_value[31] == $src2_value[31]) ? $sltu_rslt : {31'b0, $src1_value[31]} :
                         $is_slti ?
                         ($src1_value[31] == $imm[31]) ? $sltu_rslt : {31'b0, $src1_value[31]} :
                         $is_sra ?
                         { {32{$src1_value[31]}}, $src1_value} >> $src2_value[4:0] :
                         32'bx;
         
         $sltu_rslt[31:0]  = $src1_value[31:0] < $src2_value[31:0];
         $sltiu_rslt[31:0] = $src1_value[31:0] < $imm;
         
         //writing ALU result into register file
         $rf_wr_en = ($rd_valid && $rd!=0 && $valid) || >>2$valid_load ;  //writing only when rd is valid and rd is not equal to x0 register
         $rf_wr_index[4:0] = >>2$valid_load ? >>2$rd : $rd;
         
         $rf_wr_data[31:0] = >>2$valid_load ? >>2$ld_data[31:0] : $result;

         
         //To check branch condition
         
       
         $valid = !((>>1$valid_taken_br) || (>>2$valid_taken_br) || (>>1$valid_load) || (>>2$valid_load));
         
         $valid_taken_br = $valid && $taken_br;
         
         
         $valid_load = $valid && $is_load;
      
      @4
         //Data to memory interface
         $dmem_rd_en = $is_load;
         $dmem_wr_en = $is_s_instr && $valid;
         
         $dmem_addr[3:0] = $result[5:2];
         $dmem_wr_data[31:0] = $src2_value;
           
      @5
         $ld_data[31:0] = $dmem_rd_data;
         
         
         
         
         
            
         
         // Testbench
         *passed = |cpu/xreg[15]>>5$value == (1+2+3+4+5+6+7+8+9);
         
         
                                    
         
  

      // Note: Because of the magic we are using for visualisation, if visualisation is enabled below,
      //       be sure to avoid having unassigned signals (which you might be using for random inputs)
      //       other than those specifically expected in the labs. You'll get strange errors for these.

   
   // Assert these to end simulation (before Makerchip cycle limit).
   *passed = *cyc_cnt > 40;
   *failed = 1'b0;
   
   // Macro instantiations for:
   //  o instruction memory
   //  o register file
   //  o data memory
   //  o CPU visualization
   |cpu
      m4+imem(@1)    // Args: (read stage)
      m4+rf(@2, @3)  // Args: (read stage, write stage) - if equal, no register bypass is required
      m4+dmem(@4)    // Args: (read/write stage)

   m4+cpu_viz(@4)    // For visualisation, argument should be at least equal to the last stage of CPU logic. @4 would work for all labs.
\SV
   endmodule

```

**Generated Diagram from the makerchip of the above code is as shown below:**

![Screenshot 2024-08-21 133937](https://github.com/user-attachments/assets/33a30061-1f7b-4e79-a95b-6e9598cac133)


> Viz


![Screenshot 2024-08-21 134026](https://github.com/user-attachments/assets/5992d910-2d47-4bf0-9f70-8d44808b2919)


> Simulation Output


![Screenshot 2024-08-21 134331](https://github.com/user-attachments/assets/5c618912-b854-41e1-ac75-49545ab4d80a)


**The waveforms generated including my clock name $clk_Abu is shown below:**


![Screenshot 2024-08-21 133809](https://github.com/user-attachments/assets/4be5000f-c5cb-40aa-b97b-cd7626e67139)


**The waveform for the `/xreg[14]` where the sum of this program is store:**


![Screenshot 2024-08-21 133854](https://github.com/user-attachments/assets/87f0d3bb-dbbc-4367-a154-5e004c76cf8f)

</details>
 
<details>
 
<summary> <h2>Task-6</h2> </summary>

## Task:6-->> To convert the TL Verilog code to verilog code using Sandpiper and then use GTKWave for pre-synthesis simulation to verify the design.

**Step:1-->> Install Required Packages:**
``` c

python3-pip git iverilog gtkwave

cd ~

sudo apt-get install python3-venv

python3 -m venv .venv

source ~/.venv/bin/activate

pip3 install pyyaml click sandpiper-saas

```

![Screenshot 2024-08-26 170747](https://github.com/user-attachments/assets/db66297b-4faa-4412-98df-d8887d541b3c)

**Step:2-->> Clone this repo containing VSDBabySoC design files and testbench by command  `git clone https://github.com/manili/VSDBabySoC.git`.**

**Step:3-->> Replace the rvmyth.tlv file in the VSDBabySoC directory to src/module with the rvmth.tlv using command `cd /home/subhasis/VSDBabySoC`.**

![Screenshot 2024-08-26 171241](https://github.com/user-attachments/assets/be677722-d34f-457d-bbd1-0b22f6861849)

**Step:4-->> Convert .tlv to .v using this converter command `sandpiper-saas -i ./src/module/*.tlv -o rvmyth.v --bestsv --noline -p verilog --outdir ./src/module/`**

**Generated Verilog code with clk_Abu is as shown below:**

![Screenshot 2024-08-26 173556](https://github.com/user-attachments/assets/0aaf57ca-cef1-4816-934b-005c72796a90)

**Step:5-->> Make the pre_synth_sim.vcd using command `make pre_synth_sim`**

**Step:6-->> To compile and simulate RISC-V design run the following code `iverilog -o output/pre_synth_sim.out -DPRE_SYNTH_SIM src/module/testbench.v -I src/include -I src/module`**

**Step:7-->> To open the Simulation file in gtkwave tool use the following command `gtkwave pre_synth_sim.vcd`**


![Screenshot 2024-08-26 175726](https://github.com/user-attachments/assets/a030945e-954b-45c2-9ebb-62018d5e5819)

**The below diagram contains my clk signal `clk_Abu` , `reset` signal and `Out[9:0]` of Risc-v Core.**

![Screenshot 2024-08-26 173640](https://github.com/user-attachments/assets/e79b02e4-fb1a-4688-9730-d948bb8254ff)


</details>   

   
    
<details>
 
<summary> <h2>Task-7</h2> </summary>

## Task-7: To convert a digital output from a Verilog file into an analog signal using a DAC and PLL for Risc-V processor. 
    
**The following commands were used to run out Risc-V core inside the BabySoc:**
```c
$ sudo apt-get update
$ git clone https://github.com/YosysHQ/yosys.git
$ cd yosys
$ sudo apt install make (If make is not installed please install it) 
$ sudo apt-get install build-essential clang bison flex \
    libreadline-dev gawk tcl-dev libffi-dev git \
    graphviz xdot pkg-config python3 libboost-system-dev \
    libboost-python-dev libboost-filesystem-dev zlib1g-dev
$ make config-gcc
$ make 
$ sudo make install


```

**Use these commands to install iverilog:**

```c

sudo apt-get update
sudo apt-get install iverilog


```

 **Use these commands to install Gtkwave:**

```c

sudo apt-get update
sudo apt install gtkwave

```

**After that to clone the BabySoc use this command `git clone https://github.com/Subhasis-Sahu/BabySoC_Simulation/`**

**In final step for functional verification we use these commands:**

```c

cd BabySoC_Simulation
iverilog -o ./pre_synth_sim.out -DPRE_SYNTH_SIM src/module/testbench.v -I src/include -I src/module/
./pre_synth_sim.out
gtkwave pre_synth_sim.vcd

```

**These are the snapshots of my terminal window:**

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-09-02%2023-00-10.png![image](https://github.com/user-attachments/assets/9ad567eb-4cb1-40c9-b0df-5a54c781759a)


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-09-02%2023-01-25.png![image](https://github.com/user-attachments/assets/cff605fe-a0fd-4fff-bcd3-887f2ad705de)

**Below is the output waveforms: We can clearly observe that VCO_IN is the input clk for the PLL and CLK is the clk output from the PLL. clk_Abu is the clock used inside the Risc-V core and OUT is the analog signal coming out of the DAC unit.**


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-09-02%2022-58-24.png![image](https://github.com/user-attachments/assets/4db83136-2bcd-436a-ba91-6a3413e128a9)


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-09-02%2022-58-48.png![image](https://github.com/user-attachments/assets/c8972622-fc91-43cc-8282-5b6e5482d885)


 </details>


  <details>
 
<summary> <h2>Task-8</h2> </summary>



<details>
    <summary>Day-1:</summary>

## Task-8: Verilog RTL Design and Synthesis.

### Lab: Installation of the files and Repository

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-17%2019-08-13.png![image](https://github.com/user-attachments/assets/6fc3ebcb-8251-4d8d-bf65-1ecc111dce86)


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-17%2019-12-23.png![image](https://github.com/user-attachments/assets/ef6137a2-6ecd-4b62-a353-af32339d6195)


## Lab: Simulation by iverilog and Gtkwave

**In this lab we have implemented the 2*1 mux using it's verilog code and test bench which is already present in the file that we have clone from the github in lab-1**

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-17%2019-29-00.png![image](https://github.com/user-attachments/assets/f5817a28-e5bf-49a9-95a1-fb8916ff4c16)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-17%2019-31-24.png![image](https://github.com/user-attachments/assets/7355f574-1d3e-4df3-a0f7-f23e3c492c5d)

**We can see the verilog code and test bench by this command**

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-17%2019-46-35.png![image](https://github.com/user-attachments/assets/3af042d9-423b-4fcc-a83c-bcfdb4c190e3)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-17%2019-46-16.png![image](https://github.com/user-attachments/assets/28cf989a-8e62-4f5b-8866-200f9c54ca9a)

## Synthesizer:

**A synthesizer is a crucial tool in the digital design process, responsible for converting RTL (Register Transfer Level) code into a gate-level netlist. The netlist is a detailed representation of the circuit, consisting of logical gates and their connections, ready for physical design stages like place and route. In this flow, Yosys is the synthesizer tool being used, which is an open-source framework for Verilog HDL synthesis. Yosys performs various optimization techniques to produce an efficient gate-level implementation from the RTL code.**

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-17%2019-57-47.png![image](https://github.com/user-attachments/assets/419fada9-c527-431e-89e5-6ee0208bd62c)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-17%2019-58-22.png![image](https://github.com/user-attachments/assets/fab22c0d-9c48-4995-9477-d8f358370245)


## Logic Synthesis:

**So, we have an RTL code that describes the design in terms of data flow and operations. To turn this into an actual circuit, we use a process called synthesis. During synthesis, the RTL code is translated into basic logic gates like AND, OR, and NOT, and the connections between these gates are established. This final representation is called a netlist, which defines the structure of the circuit at the gate level.**

**We need synthesis because RTL is more abstract and easier for humans to write and understand, but we need something that can be physically built on a chip. The netlist generated after synthesis can then be used for place and route, where the gates are laid out on a chip and connected. After synthesis, tools can check if the design meets timing requirements, area constraints, and power limits. Without synthesis, we wouldn’t be able to move from high-level design to an actual, manufacturable circuit.**

## Why we need faster cells?

**The combinational delay limits the maximum speed of a digital logic circuit. To minimize this delay, faster cells are needed so the logic can be computed quickly. This ensures that the required logic is generated before the next clock cycle arrives, allowing the circuit to operate efficiently at higher speeds. So we need a setup time for this:**

## Setup Time:

**Setup time is the minimum amount of time before the clock edge during which the input signal (data) to a flip-flop or latch must remain stable. If the data changes within this period, the flip-flop might not capture the correct value, leading to timing violations. Essentially, the data needs to be ready and stable for a certain time before the clock triggers the flip-flop.**

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-17%2020-24-18.png![image](https://github.com/user-attachments/assets/efe113f7-2ae2-4265-b85b-37a9d85496f6)

## Why we need slower cells?

**Slow cells are needed to prevent hold time violations, ensuring the logic is captured correctly after the clock edge. The logic must remain stable for a certain time (hold time), and if faster gates are used, it can lead to hold time violations by changing the data too quickly after the clock signal.**

## Hold Time:

**Hold time is the minimum amount of time after the clock edge during which the input signal (data) must remain stable. If the data changes too soon after the clock edge, the flip-flop may not correctly latch the data. This ensures that the data isn't altered prematurely right after the clock edge has triggered the latch or flip-flop.**

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-17%2020-22-13.png![image](https://github.com/user-attachments/assets/f78b4f9f-5ff0-4f70-b86b-f8ee3b3f5134)


## Lab: Introduction to Yosys:


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-17%2023-00-51.png![image](https://github.com/user-attachments/assets/75ebf729-110f-4309-9d95-e5ddcdc54244)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-17%2023-01-08.png![image](https://github.com/user-attachments/assets/ba8699a5-eb65-41c2-a72c-3bf81d4786b2)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-17%2023-01-17.png![image](https://github.com/user-attachments/assets/504f505f-f1d0-451a-bb9c-c03224b2e2de)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-17%2023-01-54.png![image](https://github.com/user-attachments/assets/713b579d-c686-4a10-8aa2-e9637fc7338b)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-17%2023-02-07.png![image](https://github.com/user-attachments/assets/6a210209-16a8-445b-a1cc-a47358717518)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-17%2023-02-17.png![image](https://github.com/user-attachments/assets/b7652e2a-3d28-4813-bc34-a85fe92285eb)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-17%2023-02-29.png![image](https://github.com/user-attachments/assets/9b4101c2-5f7e-4197-8d44-f26a0ca9e427)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-17%2023-02-39.png![image](https://github.com/user-attachments/assets/80b301c6-ef0d-4b76-b0f5-83357c267bf9)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-17%2023-02-47.png![image](https://github.com/user-attachments/assets/54e9232e-a745-4aca-b1ac-ee0ab289f74e)


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-17%2023-03-07.png![image](https://github.com/user-attachments/assets/25b3ec34-7f11-41df-95b9-d36e44dae03e)


**Convert RTL to netlist using command `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`**

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-17%2023-12-15.png![image](https://github.com/user-attachments/assets/5098bbb7-9f61-4667-949e-7e27aabd3e23)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-17%2023-12-41.png![image](https://github.com/user-attachments/assets/b0ef1411-8fe9-4038-81d8-3d3fa58937ae)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-17%2023-12-48.png![image](https://github.com/user-attachments/assets/a388b8e6-b4a9-42f2-a06c-af654e94eec7)

**Then to see the netlist we use command `show`**

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-17%2023-18-32.png![image](https://github.com/user-attachments/assets/b3c8d961-ac4b-4795-bfa1-199121b0d59d)


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-17%2023-17-37.png![image](https://github.com/user-attachments/assets/9121ddb0-da25-475d-bc0b-6e72c1ca3558)


**Observe netlist using command `write_verilog good_mux_netlist.v`**

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-17%2023-28-09.png![image](https://github.com/user-attachments/assets/6b376987-befe-414e-82ba-0adfc8bfe5b5)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-17%2023-27-09.png![image](https://github.com/user-attachments/assets/f5ebe6e8-ec95-440e-bfb9-f44c65f3b3e9)


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-17%2023-34-31.png![image](https://github.com/user-attachments/assets/a825c1b9-329e-4b1f-aace-e5fcf30814ee)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-17%2023-34-08.png![image](https://github.com/user-attachments/assets/efec039d-3f65-4a61-8e59-d5306acbd976)

</details>
	
<details>
    <summary>Day-2:</summary>

## Lab- Hier synthesis flat synthesis:


**Yosys Synthesis for Multiple Modules:**


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-18%2020-09-03.png![image](https://github.com/user-attachments/assets/63f7cb9d-038b-4e46-bfd8-bdc65436ed2e)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-18%2019-47-45.png![image](https://github.com/user-attachments/assets/2577aa69-d458-4433-86e4-21e1e1f655f9)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-18%2020-20-46.png![image](https://github.com/user-attachments/assets/3804f68f-b45d-456f-9917-67fe35d45d07)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-18%2020-21-00.png![image](https://github.com/user-attachments/assets/50b63cfb-1131-463b-a61d-c6f5e9d4ef36)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-18%2020-21-15.png![image](https://github.com/user-attachments/assets/45110cd8-bdb0-44c6-a8b0-7498c3125470)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-18%2020-21-25.png![image](https://github.com/user-attachments/assets/0b7f2cc3-ea96-4ff8-afcf-3174edeb7e1e)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-18%2020-21-34.png![image](https://github.com/user-attachments/assets/7d54c8f9-2600-4865-9a85-55d5343dcb76)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-18%2020-22-33.png![image](https://github.com/user-attachments/assets/d9e1295f-750d-4eac-9d0a-54b9165d29e8)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-18%2020-22-42.png![image](https://github.com/user-attachments/assets/f0996480-b04f-45e4-ac83-9531d3035e9d)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-18%2020-22-57.png![image](https://github.com/user-attachments/assets/e10076ae-77ef-4b65-972d-f7abc3402720)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-18%2020-23-15.png![image](https://github.com/user-attachments/assets/70671083-a19b-40a4-afec-c87b0035dd8f)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-18%2020-23-31.png![image](https://github.com/user-attachments/assets/14465d3a-26be-4a11-9a87-50cc9e666f39)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-18%2020-23-41.png![image](https://github.com/user-attachments/assets/f8eea0bc-71a9-4b0c-a10e-f56a4596b63b)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-18%2020-23-48.png![image](https://github.com/user-attachments/assets/df08b86a-b58c-4b6c-81ef-a6ca65fdc525)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-18%2020-24-02.png![image](https://github.com/user-attachments/assets/ab272892-d87c-4fa3-a1ce-52a9557dff5d)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-18%2020-26-28.png![image](https://github.com/user-attachments/assets/9eccc801-778b-4c8b-b48b-68b409c024a8)


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-19%2000-15-36.png![image](https://github.com/user-attachments/assets/4370fabc-884e-412b-91d9-fd10ddf9a7d3)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-19%2000-15-52.png![image](https://github.com/user-attachments/assets/29b35246-88c5-44ff-a9a9-4fdf50c376c5)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-19%2000-16-12.png![image](https://github.com/user-attachments/assets/801a8e42-9f7d-4a79-8d5e-cb5f8188bfa3)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-19%2000-16-26.png![image](https://github.com/user-attachments/assets/0755cecf-a53e-4c7c-bb5e-552183e16a01)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-19%2000-16-36.png![image](https://github.com/user-attachments/assets/e6d9847b-c1ca-4bdd-be96-973d1b285458)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-19%2000-16-44.png![image](https://github.com/user-attachments/assets/39139612-f7f1-4576-9382-27e9e6a3ddc3)


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-19%2000-17-15.png![image](https://github.com/user-attachments/assets/a6c2432c-9e92-4718-89c9-666973d4c291)


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-18%2020-36-21.png![image](https://github.com/user-attachments/assets/36bc6ff4-5578-421d-b0a0-4a110610e055)


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-18%2020-37-02.png![image](https://github.com/user-attachments/assets/548efeb2-f143-4884-8656-485a640001d4)

##Flattening:

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-19%2020-29-55.png![image](https://github.com/user-attachments/assets/68d6cd5e-20f3-445d-9303-3160ccb87acb)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-19%2020-27-17.png![image](https://github.com/user-attachments/assets/29756deb-7ac6-45cf-a210-ac4ac04f0f7e)

**Generated Netlist:**

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-19%2020-28-57.png![image](https://github.com/user-attachments/assets/f3c0f438-4948-44d2-b331-ee0d5004fb0f)


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-19%2020-29-19.png![image](https://github.com/user-attachments/assets/4ccf6a6e-5bd2-46b7-9c39-4cde5a8ef887)



## Labs of Synchronous and Asynchronous D_FFs:

## Asynchronous Reset:

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-19%2018-02-38.png![image](https://github.com/user-attachments/assets/40729c1e-3549-4ace-9dc6-09400f8b90a8)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-19%2018-03-06.png![image](https://github.com/user-attachments/assets/38787308-7943-4136-8942-7d65f2031c50)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-19%2017-59-08.png![image](https://github.com/user-attachments/assets/075362af-5d2e-4595-bcc3-b5c9477d5998)


## Asynchronous Set:

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-19%2018-03-32.png![image](https://github.com/user-attachments/assets/42f0f693-0f68-4dce-b9f2-00ba791fb6ce)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-19%2018-02-10.png![image](https://github.com/user-attachments/assets/9dbe839f-96f2-4cd7-b2ed-51e39c5ba330)


## Synchronous Reset:

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-19%2018-17-49.png![image](https://github.com/user-attachments/assets/ed19a918-19d7-46e3-8e04-6c9a4936b5b2)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-19%2018-17-27.png![image](https://github.com/user-attachments/assets/b2807b9f-a3ae-48c2-9892-9e54aeb691b5)



## Synthesis using Yosys:

## Asynchronous Reset:

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-19%2019-12-13.png![image](https://github.com/user-attachments/assets/f9b139cd-2ec0-4e4f-9358-9ccc495e255e)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-19%2019-12-29.png![image](https://github.com/user-attachments/assets/4da24ec0-9fbd-4167-be73-3bbadb01adc4)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-19%2019-12-40.png![image](https://github.com/user-attachments/assets/39ee460b-817a-4d55-96f1-b025b7431362)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-19%2019-12-48.png![image](https://github.com/user-attachments/assets/908ae8ae-d90f-4bff-8a02-e011453ac5df)


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-19%2019-12-55.png![image](https://github.com/user-attachments/assets/79725d12-9d3f-4b92-8bd6-43a378331da8)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-19%2019-13-07.png![image](https://github.com/user-attachments/assets/6c4f2385-9e3d-4f84-b593-618d11efc6f1)


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-19%2019-13-15.png![image](https://github.com/user-attachments/assets/d028a389-2847-4240-9e93-2029d4c15a0a)


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-19%2019-13-24.png![image](https://github.com/user-attachments/assets/fa72df71-4c4e-4594-81a9-e68d8c65588a)



file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-19%2019-13-31.png![image](https://github.com/user-attachments/assets/600d5b0e-8e1f-47bc-b7f9-c20e9aed0b80)



file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-19%2019-13-46.png![image](https://github.com/user-attachments/assets/f42c8436-44d0-49fb-91a1-3ded3a6acc19)



file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-19%2019-13-52.png![image](https://github.com/user-attachments/assets/d8c8a1d4-cddd-4165-b753-b740b25e6c05)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-19%2018-40-32.png![image](https://github.com/user-attachments/assets/4a7d0085-2312-4e25-878b-e8f990c54b7a)



## Asynchronous Set:



```c

yosys
read_verilog dff_async_set.v
synth -top dff_async_set
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show




```

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-19%2019-44-54.png![image](https://github.com/user-attachments/assets/410d8e01-bf1d-4f34-9c67-13e2f6c8f463)


## Synchronous Reset:

```c
yosys
read_verilog dff_syncres.v
synth -top dff_syncres
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show

```

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-19%2019-50-51.png![image](https://github.com/user-attachments/assets/13aae006-bde4-41c1-b8ff-1171ea4b9f05)




## Multiplication by 2:

```c
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog mult_2.v
synth -top mul2
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
write_verilog -noattr mul2_net.v
!gvim mul2_net.v



```

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-19%2020-05-14.png![image](https://github.com/user-attachments/assets/3ad2b5e6-602d-4dfd-ba03-53dc482ca289)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-19%2019-55-24.png![image](https://github.com/user-attachments/assets/d5ab9255-4def-40e4-9954-3e5cd1469e94)


**Generated Netlist:**

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-19%2020-01-04.png![image](https://github.com/user-attachments/assets/8b82b500-4003-4a3a-b097-f94f6f23c099)


## Multiplication with 9:

```c

yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog mult_8.v
synth -top mult8
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
write_verilog -noattr mul8_net.v
gvim mul8_net.v

```

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-19%2020-16-46.png![image](https://github.com/user-attachments/assets/2b3267ff-3d8f-47af-9321-f1e54387c3fe)


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-19%2020-13-57.png![image](https://github.com/user-attachments/assets/e885a0a6-3151-4266-a9fa-009664982c1f)


**Generated Netlist:**

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-19%2020-16-23.png![image](https://github.com/user-attachments/assets/8fa69059-bab9-4d2e-ba11-e5f3ede4f8b7)

</details>



<details>
    <summary>Day-3:</summary>

## Introduction to optimizations:

## Combinational Logic Optimization

## Lab:

## 2 inp and gate

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2012-16-35.png![image](https://github.com/user-attachments/assets/001375bc-017e-4b5d-b2fa-d64f979838c1)

**Commands**
```c
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog opt_check.v
synth -top opt_check
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
opt_clean -purge
show


```

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2012-09-39.png![image](https://github.com/user-attachments/assets/66661dcf-2180-4b17-811d-a4f805c5e3b8)


**After removing unused logic, optimized logic of the circuit is:**

**Commands**
```c
//Design
module opt_check(input a, input b, output y);
	assign y = a?b:0;
endmodule

```

## 2-inp OR gate:

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2012-27-56.png![image](https://github.com/user-attachments/assets/8bcde222-39cb-44c2-ae4f-e46fe3be0122)


```c
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog opt_check2.v
synth -top opt_check2
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
opt_clean -purge
show

```

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2012-25-52.png![image](https://github.com/user-attachments/assets/8280b859-19e3-47c3-8585-f5867aec8bf2)


**After removing unused logic, optimized logic of the circuit is:**

```c
//Design
module opt_check2(input a, input b, output y);
	assign y = a?1:b;
endmodule

```


## 3-inp and gate:

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2012-30-12.png![image](https://github.com/user-attachments/assets/2fc6cd1a-6b1f-4f61-9aaf-d27980e2af51)

**Commands**

```c
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog opt_check3.v
synth -top opt_check3
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
opt_clean -purge
show

```
file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2012-29-52.png![image](https://github.com/user-attachments/assets/f376fb7c-a9eb-4d52-8438-db3dd49e0e4e)


**After removing unused logic, optimized logic of the circuit is:**

```c
//Design
module opt_check2(input a, input b, input c, output y);
	assign y = a?(b?c:0):0;
endmodule

```

## 2-inp xnor gate:

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2012-32-04.png![image](https://github.com/user-attachments/assets/e96817bb-6e2c-4d12-81a6-f2a7a9bc7809)

**Commands**

```c

yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog opt_check4.v
synth -top opt_check4
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
opt_clean -purge
show
```
file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2012-31-48.png![image](https://github.com/user-attachments/assets/d136433a-4039-454a-8b57-357e4940a5f4)

**After removing unused logic, optimized logic of the circuit is:**

```c
//Design
module opt_check2(input a, input b, input c, output y);
	assign y = a ? (b ? ~c : c) : ~c;
endmodule
```

## D-Flipflop Constant 1 with Asynchronous active low Reset:

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2018-10-02.png![image](https://github.com/user-attachments/assets/49dd3519-2cd7-4696-9f11-3f0dba3a1cec)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2018-19-42.png![image](https://github.com/user-attachments/assets/32f539bd-53fb-4a99-b08b-6e336a6306d7)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2018-09-22.png![image](https://github.com/user-attachments/assets/e09d2068-3ec7-47e7-a38b-a2126e76ef2b)

**Commands**

```c
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog dff_const1.v
synth -top dff_const1
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show

```
file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2018-12-23.png![image](https://github.com/user-attachments/assets/1c83f234-5285-4330-a628-1cee7300aa83)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2018-12-29.png![image](https://github.com/user-attachments/assets/e992b6e2-5d79-46fd-b841-a48b5edcd9a8)



file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2018-11-39.png![image](https://github.com/user-attachments/assets/f109a7b2-87eb-4328-8804-b265105575fd)


## D-Flipflop Constant 2 with Asynchronous active high Reset:

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2018-16-16.png![image](https://github.com/user-attachments/assets/150491c6-ea01-4984-8736-2a825ee63bf5)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2018-15-22.png![image](https://github.com/user-attachments/assets/fd61f6fd-418d-465c-a1ae-9550dd654130)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2018-13-45.png![image](https://github.com/user-attachments/assets/bdead2b0-a923-42f2-948f-9736910b1866)

**Commands**
```c
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog dff_const2.v
synth -top dff_const2
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show

```
file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2018-40-48.png![image](https://github.com/user-attachments/assets/0aab8804-a98c-4a77-bb72-fce2c2cbeab8)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2018-41-00.png![image](https://github.com/user-attachments/assets/c330db36-16b0-452d-b448-0b3bb79d0e62)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2018-40-32.png![image](https://github.com/user-attachments/assets/c981f279-ed0e-4be6-981c-305705f4f6ae)



## D-Flipflop Constant 3 with Asynchronous active low Reset:

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2019-28-20.png![image](https://github.com/user-attachments/assets/3ea05cac-f344-49ac-970b-8438f617c373)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2019-24-47.png![image](https://github.com/user-attachments/assets/a98bb658-3a4c-4466-a047-a661b045aa80)


**Commands**

```c
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog dff_const3.v
synth -top dff_const3
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show

```

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2019-27-35.png![image](https://github.com/user-attachments/assets/a0cbca78-4080-4357-b603-1adc19a2f7ee)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2019-27-40.png![image](https://github.com/user-attachments/assets/efe89cc4-52a0-405b-b6f9-3e9169ce542b)


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2019-27-03.png![image](https://github.com/user-attachments/assets/41a4766a-547b-48e7-a775-4132415af794)


## D-Flipflop Constant 4 with Asynchronous active high Reset:

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2019-37-17.png![image](https://github.com/user-attachments/assets/6fb75965-dcab-44b5-906a-bef67f0c369b)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2019-36-59.png![image](https://github.com/user-attachments/assets/d2a17df9-7693-4536-8982-01c04a86a66d)

**Commands**

```c

yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog dff_const4.v
synth -top dff_const4
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show

```

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2019-38-37.png![image](https://github.com/user-attachments/assets/2109c62e-3d23-4757-9daf-c1b01a454ae9)


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2019-38-45.png![image](https://github.com/user-attachments/assets/32e3826c-9082-406f-89ee-9eafef7d2ba7)


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2019-38-15.png![image](https://github.com/user-attachments/assets/7c5e5062-412d-423c-a962-ee8e304c20d1)


## D-Flipflop Constant-5 with Asynchronous Reset:

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2019-43-29.png![image](https://github.com/user-attachments/assets/f785d8f5-82cf-4d0f-8e05-539499c880a3)


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2019-43-17.png![image](https://github.com/user-attachments/assets/d510711c-96b7-42d8-bade-65e0447a0205)

**Commands**

```c

yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog dff_const5.v
synth -top dff_const5
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show


```

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2019-44-55.png![image](https://github.com/user-attachments/assets/8da4633d-5656-4d7b-b498-c1b5a5975238)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2019-45-00.png![image](https://github.com/user-attachments/assets/e239d2a2-a00a-4c2f-8e40-ed968da826b9)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2019-44-33.png![image](https://github.com/user-attachments/assets/0148bfc7-a234-4a38-9442-5a0feb70c747)


## Counter_Optimization-1:

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2019-50-01.png![image](https://github.com/user-attachments/assets/698002f1-a689-4760-b42c-5be10624d2a1)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2019-49-48.png![image](https://github.com/user-attachments/assets/13bee093-cd4e-4016-b23c-e4452becb29c)

```c
yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog counter_opt.v
synth -top counter_opt
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show

```

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2019-51-44.png![image](https://github.com/user-attachments/assets/73f5559d-6d56-482e-af85-47e6711b06ad)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2019-51-52.png![image](https://github.com/user-attachments/assets/766d9acb-e165-4f5e-8497-defaf16cc4c5)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2019-51-20.png![image](https://github.com/user-attachments/assets/83523b3b-1bbd-496b-9d5c-cf11bfc6a794)


## Counter_Optimization-2:

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2020-01-07.png![image](https://github.com/user-attachments/assets/bc325c2f-fc2c-4e92-93e4-a338e32c7a4f)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2020-00-56.png![image](https://github.com/user-attachments/assets/cff8349b-03a0-467a-bd03-0f26692fe799)

**Commands**

```c

yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog counter_opt2.v
synth -top counter_opt2
dfflibmap -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
show
```

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2020-03-27.png![image](https://github.com/user-attachments/assets/cba53845-ab06-4fdd-ae3d-78994a028f81)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2020-03-36.png![image](https://github.com/user-attachments/assets/000a3a5f-786b-4a0a-b68e-55fa7717b337)


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2020-02-45.png![image](https://github.com/user-attachments/assets/1dc3a0b9-64a8-4199-82a6-cebf6fee742a)


</details>

<details>
    <summary>Day-4:</summary>
	


## 2x1 mux design using Ternary Operator:

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2022-18-09.png![image](https://github.com/user-attachments/assets/5fd9a9e9-8e32-4aa7-926a-f95777e936db)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2022-14-20.png![image](https://github.com/user-attachments/assets/e0115898-33b8-4f83-93fc-50b88735512e)




file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2022-03-52.png![image](https://github.com/user-attachments/assets/fbe5935d-25ac-40d3-8451-6f619b6c2154)


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2022-03-18.png![image](https://github.com/user-attachments/assets/16b8a172-f92f-4d89-8799-75d98de3c237)

**Commands**

```c

yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog ternary_operator_mux.v
synth -top ternary_operator_mux
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
opt_clean -purge
write_verilog -noattr ternary_operator_mux_net.v
!gvim ternary_operator_mux_net.v
show

```

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2022-09-02.png![image](https://github.com/user-attachments/assets/cb9e7962-0596-4aac-b5f7-72ba643616ab)


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2022-09-16.png![image](https://github.com/user-attachments/assets/70eaa25f-5a54-4112-9008-14bbb82427f5)


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2022-06-00.png![image](https://github.com/user-attachments/assets/266f458a-070e-4ffc-ad8f-0eddadb34dd5)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2022-06-20.png![image](https://github.com/user-attachments/assets/7547d69d-99ef-49ef-a345-2350bbfbc26c)


**Ternary Operator mux gate level synthesis**

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2022-18-09.png![image](https://github.com/user-attachments/assets/006fec0c-1f70-4ad9-bc8a-93501206aca5)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2022-12-33.png![image](https://github.com/user-attachments/assets/d7011382-5480-4f32-8204-106595dcccbd)


## Bad 2*1 mux:

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2022-30-52.png![image](https://github.com/user-attachments/assets/da292824-eaed-4eb8-9f4c-5d51ecb5e400)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2022-30-37.png![image](https://github.com/user-attachments/assets/60261d57-d7dc-42ef-8534-2c1e80d71a6e)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2022-37-57.png![image](https://github.com/user-attachments/assets/7f8cd5b0-7243-4fd6-9fa6-fd93f7c5d240)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2022-36-36.png![image](https://github.com/user-attachments/assets/5717bc3b-bb93-40ce-8cad-28439da8e27f)


**We can observe that the output y is changing only when select line is changing, here we can see that when select line is 1 then y should follow input i1, here in this region i1 is changing from 1 to 0 but y is giving only 1 in this region, so it is a bad buffer.**

**Commands**

```c

yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog bad_mux.v
synth -top bad_mux
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
opt_clean -purge
write_verilog -noattr bad_mux_net.v
!gvim bad_mux_net.v
show

```

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2022-52-44.png![image](https://github.com/user-attachments/assets/cbd96518-c594-479c-b347-5a4448e3c712)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2022-52-52.png![image](https://github.com/user-attachments/assets/dab543e4-06f5-4018-96a9-85e9e9eb0846)


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2022-51-35.png![image](https://github.com/user-attachments/assets/6ac858d1-ceed-4d0f-85da-e382e94fb175)


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2022-52-01.png![image](https://github.com/user-attachments/assets/800f62dc-964c-43ea-899d-13d680acc604)


**Bad mux gate level synthesis.**

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2022-54-34.png![image](https://github.com/user-attachments/assets/4134bae6-7f99-4650-9fcc-ff4626c9fc38)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2022-54-17.png![image](https://github.com/user-attachments/assets/f5db3f61-abc7-4a24-8655-11cf0baa69b7)

## Blocking Caveat:

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2023-03-56.png![image](https://github.com/user-attachments/assets/6d72233d-b92c-45f4-99ff-c66d5ed08552)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2023-03-42.png![image](https://github.com/user-attachments/assets/d09170bd-777f-4f83-aa0a-a0349c272a35)


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2023-13-31.png![image](https://github.com/user-attachments/assets/14ea4fe6-eae7-46a6-9769-9cad88e01a2a)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2023-11-57.png![image](https://github.com/user-attachments/assets/0a28d8b4-61a9-42df-8d7e-f8e668aca332)


**Commands**

```c

yosys
read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog blocking_caveat.v
synth -top blocking_caveat
abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib
opt_clean -purge
write_verilog -noattr blocking_caveat_net.v
!gvim blocking_caveat_net.v
show

```

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2023-19-26.png![image](https://github.com/user-attachments/assets/91e52a1e-0686-4d4d-b20e-5fde84225b1b)


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2023-19-34.png![image](https://github.com/user-attachments/assets/2a5d7326-9ab3-40f6-9ac4-17e7e9514dc6)


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2023-18-10.png![image](https://github.com/user-attachments/assets/f216ec85-c005-48f2-815f-d4547043d21a)


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2023-18-53.png![image](https://github.com/user-attachments/assets/8e37868c-8f94-4277-b1e5-ebe0dcd1a4e4)


**Blocking Caveat gate level synthesis.**


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2023-28-07.png![image](https://github.com/user-attachments/assets/bfe71280-0d25-4556-b186-54d21a49cfd6)



file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-20%2023-27-49.png![image](https://github.com/user-attachments/assets/f2358979-b524-47a6-af0c-5a4f7613f182)

</details>



</details>



<details>
 
<summary> <h2>Task-9</h2> </summary>

## Task-9: Synthesize RISC-V and compare output with functional simulations.


**The following was the digital and its corresponding analog output on the RISC V processor are as follows:**

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-24%2002-00-09.png![image](https://github.com/user-attachments/assets/133ea712-5b9e-4fbc-bb75-a4d03bbe265a)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-24%2001-59-25.png![image](https://github.com/user-attachments/assets/3ad172d7-03f6-4f38-a25c-4a42458dd5f1)

**We now need to synthesize the RTL and find out the corresponding output. We will use yosys to synthesize the output.**


**The following commands were used to generate the netlist, it is given in the snapshots:** 

   
file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-24%2000-18-20.png![image](https://github.com/user-attachments/assets/e1798d2e-4859-468b-b142-6e6b01f1c61a)

 file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-24%2000-18-40.png![image](https://github.com/user-attachments/assets/bc94036f-ae18-4dc0-8ec1-537d87e068f9)
   
file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-24%2000-19-04.png![image](https://github.com/user-attachments/assets/0a73a173-4442-4f17-ad10-a696f256a782)

 file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-24%2000-20-55.png![image](https://github.com/user-attachments/assets/2ba77a80-1b78-4d12-a756-2abc6c1a70ce)
  
file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-24%2000-21-04.png![image](https://github.com/user-attachments/assets/3f441d69-5979-4865-8ece-6874386048b4)

  file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-24%2000-21-10.png![image](https://github.com/user-attachments/assets/6e9993da-b9ba-4252-9f2b-64bce6a32498)
 

The generated netlist verilog is shown below :

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-24%2001-07-15.png![image](https://github.com/user-attachments/assets/eff3cf95-e192-49d3-9b5b-3545e691d309)

  


**Top Module "vsdbabysoc" was edited to integrated the generated netlist verilog:** 
  

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-24%2001-03-58.png![image](https://github.com/user-attachments/assets/864c4311-2feb-4593-b251-5e8f62be15d1)
  

**Now change the testbench to:**
  

 file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-24%2001-03-49.png![image](https://github.com/user-attachments/assets/a0a59655-63a3-4f9b-874e-2787f3906b2f)
 


**To run new SOC, following commands are used which includes the synthesized RVMYTH core:**


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-24%2001-43-10.png![image](https://github.com/user-attachments/assets/e98f6611-433c-4227-b022-cae7078be22e)


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-24%2001-43-44.png![image](https://github.com/user-attachments/assets/572991db-427b-4ad9-9016-4f5ea109504c)

  


  

**The Gtkwave is as shown below:**


file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-24%2001-28-55.png![image](https://github.com/user-attachments/assets/175648ac-f3d6-4e8c-b768-77b3a7567281)



**The standard cell highlighted in the image is "09330" the same cell is available in the code as shown in the code:**

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-24%2000-42-33.png![image](https://github.com/user-attachments/assets/79162f80-560d-48b1-839d-bd12b767122d)

**Conclusion:- From the above output we can observe a sawtooth waveform and thus we can say that the output which we get from GLS is same as that of the functional simulation.**



