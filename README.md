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

</details>

<details>
 
<summary> <h2>Task-10</h2> </summary>

## Task-10: Static Timing Analysis for a RISC-V Core with OpenSTA

### Given:

```c
Clock period = 9.4 ns
Setup uncertainty and clock transition will be 5% of clock
Hold uncertainty and data transition will be 8% of clock.
```

### In this task Static timing analysis was performed on the RV core netlist. We run the following commands to perform the analysis: 

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-28%2023-26-43.png![image](https://github.com/user-attachments/assets/d9e1ee62-8aa9-48c7-a984-a74b06f9b2c6)

### Maximum delay(Setup report)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-28%2023-27-05.png![image](https://github.com/user-attachments/assets/660118ee-3d6f-4cf6-99dc-7f4447ffd5a0)


### Minimum delay(Hold report)

file:///home/abu-huzaifa/Pictures/Screenshots/Screenshot%20from%202024-10-28%2023-27-20.png![image](https://github.com/user-attachments/assets/f8c60531-59ae-4fb3-9878-8ed0c1bae986)



</details>


<details>
 
<summary> <h2>Task-11</h2> </summary>

## Task-11: PVT Corner Analysis using OpenSTA

**Contents of tickle script for automating STA procedure:**

```c
set list_of_lib_files(1) "sky130_fd_sc_hd__ff_100C_1v65.lib"
set list_of_lib_files(2) "sky130_fd_sc_hd__ff_100C_1v95.lib"
set list_of_lib_files(3) "sky130_fd_sc_hd__ff_n40C_1v56.lib"
set list_of_lib_files(4) "sky130_fd_sc_hd__ff_n40C_1v65.lib"
set list_of_lib_files(5) "sky130_fd_sc_hd__ff_n40C_1v76.lib"
set list_of_lib_files(6) "sky130_fd_sc_hd__ff_n40C_1v95.lib"
set list_of_lib_files(7) "sky130_fd_sc_hd__ss_100C_1v40.lib"
set list_of_lib_files(8) "sky130_fd_sc_hd__ss_100C_1v60.lib"
set list_of_lib_files(9) "sky130_fd_sc_hd__ss_n40C_1v28.lib"
set list_of_lib_files(10) "sky130_fd_sc_hd__ss_n40C_1v35.lib"
set list_of_lib_files(11) "sky130_fd_sc_hd__ss_n40C_1v40.lib"
set list_of_lib_files(12) "sky130_fd_sc_hd__ss_n40C_1v44.lib"
set list_of_lib_files(13) "sky130_fd_sc_hd__ss_n40C_1v60.lib"
set list_of_lib_files(14) "sky130_fd_sc_hd__ss_n40C_1v76.lib"
set list_of_lib_files(15) "sky130_fd_sc_hd__tt_025C_1v80.lib"
set list_of_lib_files(16) "sky130_fd_sc_hd__tt_100C_1v80.lib"

for {set i 1} {$i <= [array size list_of_lib_files]} {incr i} {
read_liberty /home/abu-huzaifa/BabySoC_Simulation/lib/$list_of_lib_files($i)
read_verilog /home/abu-huzaifa/BabySoC_Simulation/
link_design rvmyth
read_sdc /home/abu-huzaifa/VSDBabySoC/src/sdc/vsdbabysoc_synthesis.sdc
check_setup -verbose
report_checks -path_delay min_max -fields {nets cap slew input_pins fanout} -digits {4} > /home/abu-huzaifa/VSDBabySoC/src/sta_output/min_max_$list_of_lib_files($i).txt

exec echo "$list_of_lib_files($i)" >> /home/abu-huzaifa/VSDBabySoC/src/sta_output/sta_worst_max_slack.txt
report_worst_slack -max -digits {4} >> /home/abu-huzaifa/VSDBabySoC/src/sta_output/sta_worst_max_slack.txt

exec echo "$list_of_lib_files($i)" >> /home/abu-huzaifa/VSDBabySoC/src/sta_output/sta_worst_min_slack.txt
report_worst_slack -min -digits {4} >> /home/abu-huzaifa/VSDBabySoC/src/sta_output/sta_worst_min_slack.txt

exec echo "$list_of_lib_files($i)" >> /home/abu-huzaifa/VSDBabySoC/src/sta_output/sta_tns.txt
report_tns -digits {4} >> /home/abu-huzaifa/VSDBabySoC/src/sta_output/sta_tns.txt

exec echo "$list_of_lib_files($i)" >> /home/abu-huzaifa/VSDBabySoC/src/sta_output/sta_wns.txt
report_wns -digits {4} >> /home/abu-huzaifa/VSDBabySoC/src/sta_output/sta_wns.txt
}
```

**Constraint file:**

```c
create_clock -name CLK -period 9.4 [get_ports CLK]
set_clock_uncertainty [expr 0.05 * 9.4] -setup [get_clocks CLK]
set_clock_uncertainty [expr 0.08 * 9.4] -hold [get_clocks CLK]
set_clock_transition [expr 0.05 * 9.4] [get_clocks CLK]
set_input_transition [expr 0.08 * 9.4] [all_inputs]

set_input_transition [expr $PERIOD * 0.08] [get_ports ENB_CP]
set_input_transition [expr $PERIOD * 0.08] [get_ports ENB_VCO]
set_input_transition [expr $PERIOD * 0.08] [get_ports REF]
set_input_transition [expr $PERIOD * 0.08] [get_ports VCO_IN]
set_input_transition [expr $PERIOD * 0.08] [get_ports VREFH]

```
## Output for different library files



![Screenshot 2024-11-04 221136](https://github.com/user-attachments/assets/68129df1-c363-4e1e-bad7-31b6c6580801)

## Total Negative Slack

![Screenshot 2024-11-05 020245](https://github.com/user-attachments/assets/ca14a96b-19cb-4f03-b942-fce342281b19)

## Worst Negative Slack (WNS)

![WhatsApp Image 2024-11-04 at 19 47 57_8683ce16](https://github.com/user-attachments/assets/27e6574d-dd4b-41b6-a641-22c9592cafab)

## Worst Setup(max) Slack

![WhatsApp Image 2024-11-04 at 19 47 57_90deec03](https://github.com/user-attachments/assets/385d7a05-f561-4a74-ae65-bfc3a7e65837)


## Worst Hold(min) Slack

![WhatsApp Image 2024-11-04 at 19 47 58_14070cb5](https://github.com/user-attachments/assets/f6cf68e3-b71e-4744-96f8-e13f008881a5)





</details>




<details>
 
<summary> <h2>Task-12</h2> </summary>

## Task-12:  Complete the Advanced Physical Design using OpenLane workshop on VSDIAT platform, and create an inverter with your name in it. Document all labs.

<details>
    <summary>Day-1:</summary>

## Inception of open-source EDA, OpenLANE and Sky130 PDK.

```c
# Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

# alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
# Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
docker

# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis

```


file:///home/vsduser/Pictures/Screenshot%20from%202024-11-12%2023-57-54.png![image](https://github.com/user-attachments/assets/49a4ae9e-d151-44ce-a3bb-a2c2bc597c97)

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-13%2000-00-33.png![image](https://github.com/user-attachments/assets/8ecb5c5a-1971-40f6-b858-652eda110a95)

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-13%2000-11-35.png![image](https://github.com/user-attachments/assets/650dd359-088e-4fa8-90a8-c23f5f74e43e)


### Calculate flop ratio:

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-13%2000-08-27.png![image](https://github.com/user-attachments/assets/e65a531c-4d15-4793-b1a9-88988c9fb448)

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-13%2000-08-45.png![image](https://github.com/user-attachments/assets/af017c9e-086f-46af-8fe2-66e4922f6b61)

```c

Flop Ratio = 1613/14876 = 0.108429685
Percentage of Flip Flops = 0.108429685 ∗ 100 = 10.84296854%

```
</details>

<details>
    <summary>Day-2:</summary>

## Good Floorpan vs Bad Floorplan and Introduction to Library Cell

### Tasks: 
    1. Run 'picorv32a' design floorplan using OpenLANE flow and generate necessary outputs.
    2. Calculate the die area in microns from the values in floorplan def.
    3. Load generated floorplan def in magic tool and explore the floorplan.
    4. Run 'picorv32a' design congestion aware placement using OpenLANE flow and generate necessary outputs.
    5. Load generated placement def in magic tool and explore the placement.

Area of die in microns = Die width in microns * Die height in microns

### 1. Run 'picorv32a' design floorplan using OpenLANE flow and generate necessary outputs.

```c

cd Desktop/work/tools/openlane_working_dir/openlane
docker
./flow.tcl -interactive
package require openlane 0.9
prep -design picorv32a
run_synthesis
run_floorplan

```

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-13%2000-31-59.png![image](https://github.com/user-attachments/assets/e77ba02e-d2fe-4ce7-af43-5a1da816129c)

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-13%2000-32-06.png![image](https://github.com/user-attachments/assets/958fb543-e9be-46d8-96ad-4475357d15d3)


**2. Calculate the die area in microns from the values in floorplan def.**


file:///home/vsduser/Pictures/Screenshot%20from%202024-11-13%2000-37-11.png![image](https://github.com/user-attachments/assets/bc1e314b-1826-4060-afb3-b013ba89be2b)

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-13%2000-37-21.png![image](https://github.com/user-attachments/assets/3df5d3e8-414b-4336-baa8-41c23475e7a3)

According to floorplan def 1000 Unit Distance = 1 micron Die width in unit distance = 660685 − 0 = 660685 Die height in unit distance = 671405 − 0 = 671405 Distance in microns = Value in unit distance / 1000 Die width in microns = 660685/1000 = 660.685 microns Die height in microns = 671405/1000 = 671.405 microns Are os die in microns = 660.685 ∗ 671.405 = 443587.212425 square microns.

3. Load generated floorplan def in magic tool and explore the floorplan. Commands to load floorplan def in magic in another terminal.

```c
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/12-11_18-26/results/floorplan/
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
```

### Screenshots of floorplan def in magic.

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-13%2013-37-21.png![image](https://github.com/user-attachments/assets/1c45e9c0-bcce-409b-9389-088a16717bdb)

### Equidistant placement of ports.

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-13%2013-29-37.png![image](https://github.com/user-attachments/assets/258b655d-9c21-4000-a187-aaaae12f88a6)

### Port layer as set through config.tcl

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-13%2013-30-42.png![image](https://github.com/user-attachments/assets/625c6558-f07e-459a-8a06-3169d9330b1b)

### Decap Cells and Tap Cells

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-13%2013-32-25.png![image](https://github.com/user-attachments/assets/a92e1408-cca3-44d4-975f-9ea9e193085c)

### Diagonally equidistant Tap cells

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-13%2013-32-54.png![image](https://github.com/user-attachments/assets/a67d9850-5d97-4381-8d33-c392053c33e2)

### Unplaced standard cells at the origin

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-13%2013-34-56.png![image](https://github.com/user-attachments/assets/f1ae7ac7-dab9-4f83-9575-e5b8b4995bdd)


### 4. Run 'picorv32a' design congestion aware placement using OpenLANE flow and generate necessary outputs. Command to run placement

```c
run_placement
```

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-13%2016-42-17.png![image](https://github.com/user-attachments/assets/cc1cfd76-24a0-4723-8547-7dc1e10abd3c)


### 5. Load generated placement def in magic tool and explore the placement. Commands to load placement def in magic in another terminal

```c
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/13-11_11-08/results/placement/
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-13%2016-59-11.png![image](https://github.com/user-attachments/assets/990b51f9-db77-4781-87e6-9a7b8ac9c0c2)

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-13%2017-00-56.png![image](https://github.com/user-attachments/assets/7c256f7e-1ea8-405c-b63e-f63c4181a016)


**Commands to exit from current run**

```c
# Exit from OpenLANE flow
exit

# Exit from docker sub-system
exit
```

</details>

<details>
    <summary>Day-3:</summary>

## Design Library Cell Using Magic Layout and Cell characterization.

### Tasks:
1. Clone custom inverter standard cell design from github repository: 2. Load the custom inverter layout in magic and explore. 3. Spice extraction of inverter in magic. 4. Editing the spice model file for analysis through simulation. 5. Post-layout ngspice simulations. 6. Find problem in the DRC section of the old magic tech file for the skywater process and fix them.

Section 3 - Tasks 1 to 5 files, reports and logs can be found in the following folder:

Section 3 - Task 6 files, reports and logs can be found in the following folder:

1. Clone custom inverter standard cell design from github repository

```c
cd Desktop/work/tools/openlane_working_dir/openlane
git clone https://github.com/nickson-jose/vsdstdcelldesign
cd vsdstdcelldesign
cp /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech .
ls
magic -T sky130A.tech sky130_inv.mag &

```
file:///home/vsduser/Pictures/Screenshot%20from%202024-11-13%2018-29-51.png![image](https://github.com/user-attachments/assets/2ce66007-742c-4dbe-8c3a-1e78f3a6584a)


2. Load the custom inverter layout in magic and explore.

Screenshot of custom inverter layout in magic

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-13%2018-31-00.png![image](https://github.com/user-attachments/assets/41dfb118-e128-4778-883e-61b81f4a6ce1)

### NMOS and PMOS identified


file:///home/vsduser/Pictures/Screenshot%20from%202024-11-13%2018-35-49.png![image](https://github.com/user-attachments/assets/d2b487d3-7158-4cdc-bfd0-95f631084b91)

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-13%2018-37-16.png![image](https://github.com/user-attachments/assets/8f175109-d275-4a41-91ad-5a5b6fef4249)


### Output Y connectivity to PMOS and NMOS drain verified

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-13%2018-38-14.png![image](https://github.com/user-attachments/assets/4024fedc-3ab6-4ac9-a310-d081d506e630)


### PMOS source connectivity to VDD (VPWR) verified

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-13%2018-47-43.png![image](https://github.com/user-attachments/assets/0b4e94a3-440b-4edd-a883-5b3143968e5e)

### NMOS source connectivity to VSS (here VGND) verified

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-13%2018-49-50.png![image](https://github.com/user-attachments/assets/a6caa6f3-5f6b-4566-a45e-e542678f1a53)

### Deleting necessary layout part to see DRC error

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-13%2022-24-56.png![image](https://github.com/user-attachments/assets/a4eb410a-f3f4-4214-a902-5e26a7dd1ab7)


**3. Spice extraction of inverter in magic. Commands for spice extraction of the custom inverter layout to be used in tkcon window of magic**

```c
pwd
extract all
ext2spice cthresh 0 rthresh 0
ext2spice

```
**Screenshot of tkcon window after running above commands**

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-13%2019-44-28.png![image](https://github.com/user-attachments/assets/09aec8c6-4cb7-4c22-8795-2a2fd1342698)


**Screenshot of created spice file**

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-13%2020-32-21.png![image](https://github.com/user-attachments/assets/cdd73e13-c665-4eb8-b80b-b04e744d654b)


4. Editing the spice model file for analysis through simulation. Measuring unit distance in layout grid

5. Post-layout ngspice simulations. Commands for ngspice simulation

```c
# Command to directly load spice file for simulation to ngspice
ngspice sky130_inv.spice

# Now that we have entered ngspice with the simulation spice file loaded we just have to load the plot
plot y vs time a
```

**Ngspice run snapshot**


file:///home/vsduser/Pictures/Screenshot%20from%202024-11-13%2020-39-42.png![image](https://github.com/user-attachments/assets/5654eb99-43f6-4b93-8bc1-f392f9f9fc5f)

 **Generated plot snapshot**

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-13%2020-40-34.png![image](https://github.com/user-attachments/assets/79c82151-011a-47a7-a5ee-0a6b8bc84980)


Rise transition time calculation

Rise transition time = Time taken for output to rise to 80% - Time taken for output to rise to 20%

20% of output = 660 mV 80% of output = 2.64 V

**20% Screenshots**


file:///home/vsduser/Pictures/Screenshot%20from%202024-11-13%2020-51-53.png![image](https://github.com/user-attachments/assets/bd0e10e3-1c21-4579-b972-2d7dabeb969c)


**80% screenshot**

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-13%2020-54-42.png![image](https://github.com/user-attachments/assets/199bf18f-8761-41af-b205-1c7e52e0c09f)

 Rise transition time = 2.24690 − 2.18042 = 0.06648 ns = 66.48 ps

Fall transition time calculation
Fall transition time = Time taken for output to fall to 20% − Time taken for output to fall to 80% 
20% of output = 660 mV
80% of output = 2.64 V 

**50% screenshot**

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-13%2021-04-22.png![image](https://github.com/user-attachments/assets/adbfd76f-ac7a-41a0-92df-dc612e4d6524)

 Fall Transition time = 4.02720 - 4.01995 = 0.00725 ns = 7.25 ps

Rise Cell Delay Calculation
Rise Cell Delay = Time taken for output to rise to 50% − Time taken for input to fall to 50%
50 % of 3.3 V= 1.65 V 


6. Find problem in the DRC section of the old magic tech file for the skywater process and fix them.

Link to Sky130 Periphery rules: https://skywater-pdk.readthedocs.io/en/main/rules/periphery.html

Commands to download and view the corrupted skywater process magic tech file and associated files to perform drc corrections

```c
# Change to home directory
cd

# Command to download the lab files
wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz

# Since lab file is compressed command to extract it
tar xfz drc_tests.tgz

# Change directory into the lab folder
cd drc_tests

# List all files and directories present in the current directory
ls -al

# Command to view .magicrc file
gvim .magicrc

# Command to open magic tool in better graphics
magic -d XR &
```
Screenshots of commands run

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-15%2001-48-35.png![image](https://github.com/user-attachments/assets/0080cdb2-88f6-46aa-b186-a697050b8fb0)


Screenshot of .magicrc file

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-15%2001-54-34.png![image](https://github.com/user-attachments/assets/e8958b38-6843-4522-a57a-7869616d8fcd)


### Incorrectly implemented poly.9 simple rule correction

Screenshot of poly rules

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-15%2001-55-40.png![image](https://github.com/user-attachments/assets/f8129e39-15c5-48f8-9787-70c806b28bdc)


Incorrectly implemented poly.9 rule no drc violation even though spacing < 0.48u

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-15%2001-58-30.png![image](https://github.com/user-attachments/assets/75822978-4762-4a28-89f5-3df4af3c4370)


New commands inserted in sky130A.tech file to update drc

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-15%2002-06-40.png![image](https://github.com/user-attachments/assets/c485efb9-5fe8-46a9-a316-e798df9710ee)


file:///home/vsduser/Pictures/Screenshot%20from%202024-11-15%2002-08-19.png![image](https://github.com/user-attachments/assets/6d01f347-eb54-47a4-b4a9-0ff4f1c9cc6b)

Commands to run in tkcon window

```c
# Loading updated tech file
tech load sky130A.tech

# Must re-run drc check to see updated drc errors
drc check

# Selecting region displaying the new errors and getting the error messages 
drc why
```

Screenshot of magic window with rule implemented

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-15%2002-14-14.png![image](https://github.com/user-attachments/assets/95de67e9-f709-4def-ae81-9fdde304dcce)


Incorrectly implemented difftap.2 simple rule correction

Screenshot of difftap rules 

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-15%2002-18-08.png![image](https://github.com/user-attachments/assets/072d5cd7-dd7b-4df2-8bdf-929f6e5a8c23)


Screenshot of difftap rules

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-15%2002-14-14.png![image](https://github.com/user-attachments/assets/6876c783-21bc-4318-9327-e081072c9673)

Commands to run in tkcon window
```c
# Loading updated tech file
tech load sky130A.tech

# Change drc style to drc full
drc style drc(full)

# Must re-run drc check to see updated drc errors
drc check

# Selecting region displaying the new errors and getting the error messages 
drc why
```

Screenshot of magic window with rule implemented showing no errors found 

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-15%2002-11-28.png![image](https://github.com/user-attachments/assets/7b6ad811-c293-40d6-bf6a-6dcde8aee31a)



  </details>  


<details>
    <summary>Day-4:</summary>
	
## Pre-layout timing analysis and importance of good clock tree 


### 1. Fix up small DRC errors and verify the design is ready to be inserted into our flow.
 2. Save the finalized layout with custom name and open it.
 3. Generate lef from the layout.
 4. Copy the newly generated lef and associated required lib files to 'picorv32a' design 'src' directory.
 5. Edit 'config.tcl' to change lib file and add the new extra lef into the openlane flow.
 6. Run openlane flow synthesis with newly inserted custom inverter cell.
 7. Remove/reduce the newly introduced violations with the introduction of custom inverter cell by modifying design parameters.
 8. Once synthesis has accepted our custom inverter we can now run floorplan and placement and verify the cell is accepted in PnR flow.
 9. Do Post-Synthesis timing analysis with OpenSTA tool.
10. Make timing ECO fixes to remove all violations.
11. Replace the old netlist with the new netlist generated after timing ECO fix and implement the floorplan, placement and cts.
12. Post-CTS OpenROAD timing analysis.
13. Explore post-CTS OpenROAD timing analysis by removing 'sky130_fd_sc_hd__clkbuf_1' cell from clock buffer list variable 'CTS_CLK_BUFFER_LIST'.
14. Fix up small DRC errors and verify the design is ready to be inserted into our flow. Conditions to be verified before moving forward with custom designed cell layout:

Condition 1: The input and output ports of the standard cell should lie on the intersection of the vertical and horizontal tracks. Condition 2: Width of the standard cell should be odd multiples of the horizontal track pitch. Condition 3: Height of the standard cell should be even multiples of the vertical track pitch. Commands to open the custom inverter layout.

```c
cd Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign
magic -T sky130A.tech sky130_abuinv.mag &

```

Snapshots of sky130_fd_sc_hd

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-14%2019-13-43.png![image](https://github.com/user-attachments/assets/4de32aaf-18f8-48d1-a6ff-f3060016ce8f)



Commands for tkcon window to set grid as tracks of locali layer

```c
help grid
grid 0.46um 0.34um 0.23um 0.17um
```
Snapshots of commands run

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-14%2019-11-55.png![image](https://github.com/user-attachments/assets/ed51b364-7c6a-42de-8dc4-7b824b17e122)


condition 1 verified

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-14%2001-06-48.png![image](https://github.com/user-attachments/assets/ba0938cf-6ee7-40b3-ad55-768a5a40351a)

condition 2 verified

Horizontal track pitch = 0.58 um 

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-14%2001-05-45.png![image](https://github.com/user-attachments/assets/e30bc19d-9047-4141-a0e5-5e36988915d5)

Width of standard cell = 1.77 um = 0.58 ∗ 3 

### 2. Save the finalized layout with custom name and open it. Command for tkcon window to save the layout with custom name.

```c
save sky130_abuinv.mag
magic -T sky130A.tech sky130_abuinv.mag &

```
### 3. Generate lef from the layout.
Command for tkcon window to write lef:

```c
lef write
```
Edited config.tcl to include the added lef and change library to ones we added in src directory

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-14%2002-17-35.png![image](https://github.com/user-attachments/assets/6c022fb1-cc53-4930-a625-9ba07cdfef22)

### 4. Copy the newly generated lef and associated required lib files to 'picorv32a' design 'src' directory.

Commands to copy necessary files to 'picorv32a' design 'src' directory:

```c
cp sky130_vsdinv.lef ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/
ls ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/
cp libs/sky130_fd_sc_hd__* ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/
ls ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/

```

Snapshot of commands:

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-14%2019-11-55.png![image](https://github.com/user-attachments/assets/d0912c52-f772-4a36-8261-17c6886cf35a)


### 5. Edit 'config.tcl' to change lib file and add the new extra lef into the openlane flow.
Commands to be added to config.tcl to include our custom cell in the openlane flow.

```c
set ::env(LIB_SYNTH) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"
set ::env(LIB_FASTEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__fast.lib"
set ::env(LIB_SLOWEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__slow.lib"
set ::env(LIB_TYPICAL) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"
set ::env(EXTRA_LEFS) [glob $::env(OPENLANE_ROOT)/designs/$::env(DESIGN_NAME)/src/*.lef]

```

Edit to config.tcl config.tcl to include the added lef and change library to ones we added in src directory.

### 6. Run openlane flow synthesis with newly inserted custom inverter cell.

Commands to invoke the OpenLANE flow include new lef and perform synthesis.

```c
cd Desktop/work/tools/openlane_working_dir/openlane
-u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
docker

```
```c
./flow.tcl -interactive
package require openlane 0.9
prep -design picorv32a
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs
run_synthesis
```
Snapshots of commands:

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-14%2021-46-01.png![image](https://github.com/user-attachments/assets/2f219011-433c-4df7-90a6-db41e451fb30)


    
file:///home/vsduser/Pictures/Screenshot%20from%202024-11-14%2021-50-39.png![image](https://github.com/user-attachments/assets/e36f462c-e009-4330-8c8d-f01ced363872)

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-14%2021-52-26.png![image](https://github.com/user-attachments/assets/fb132f06-c009-46da-b50a-a3f65eb1ff06)


file:///home/vsduser/Pictures/Screenshot%20from%202024-11-14%2021-52-20.png![image](https://github.com/user-attachments/assets/0487c576-dde3-4635-b70f-ba05ae909794)

   
### 7. Remove/reduce the newly introduced violations with the introduction of custom inverter cell by modifying design parameters.

Noting down current design values generated before modifying parameters to improve timing.

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-14%2022-02-10.png![image](https://github.com/user-attachments/assets/8e2dd904-2bc1-41f3-93cd-421d6d55dfb9)


file:///home/vsduser/Pictures/Screenshot%20from%202024-11-14%2022-03-33.png![image](https://github.com/user-attachments/assets/e20ea831-1506-4475-866f-2fc1bce383c7)

   
Commands to view and change parameters to improve timing and run synthesis

```c
prep -design picorv32a -tag 24-03_10-03 -overwrite
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs
echo $::env(SYNTH_STRATEGY)
set ::env(SYNTH_STRATEGY) "DELAY 3"
echo $::env(SYNTH_BUFFERING)
echo $::env(SYNTH_SIZING)

set ::env(SYNTH_SIZING) 1

echo $::env(SYNTH_DRIVING_CELL)
run_synthesis

```
 Screenshot of merged.lef in tmp directory with our custom inverter as macro
 
file:///home/vsduser/Pictures/Screenshot%20from%202024-11-14%2004-25-49.png![image](https://github.com/user-attachments/assets/3343c555-c80a-45b0-b24c-7ac6fb386967)


Screenshots of commands run:

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-14%2022-02-10.png![image](https://github.com/user-attachments/assets/21c5fbe7-d14d-4acb-ae35-b7f36449fcde)


file:///home/vsduser/Pictures/Screenshot%20from%202024-11-14%2022-03-33.png![image](https://github.com/user-attachments/assets/b817c14b-030c-40f5-b669-2d1b6176999a)

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-14%2022-04-03.png![image](https://github.com/user-attachments/assets/2c2577b6-d2ad-4f00-a456-7937d54b91b2)


### 8. Once synthesis has accepted our custom inverter we can now run floorplan and placement and verify the cell is accepted in PnR flow.

Now that our custom inverter is properly accepted in synthesis we can now run floorplan using following command
```c
# Now we can run floorplan
run_floorplan
```

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-14%2022-05-00.png![image](https://github.com/user-attachments/assets/be03f8ce-d283-4ebe-9d9c-959089a71d88)


Since we are facing unexpected un-explainable error while using run_floorplan command, we can instead use the following set of commands available based on information from Desktop/work/tools/openlane_working_dir/openlane/scripts/tcl_commands/floorplan.tcl and also based on Floorplan Commands section in Desktop/work/tools/openlane_working_dir/openlane/docs/source/OpenLANE_commands.md

# Follwing commands are alltogather sourced in "run_floorplan" command
init_floorplan
place_io
tap_decap_or

Screenshots of commands run

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-14%2022-06-09.png![image](https://github.com/user-attachments/assets/0ad1733e-dda8-4671-869f-bed1e99b0aa3)

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-14%2022-06-16.png![image](https://github.com/user-attachments/assets/1a10aae3-ffd1-44f4-9126-ba916466b19d)


Now that floorplan is done we can do placement using following command

# Now we are ready to run placement
```c
run_placement
```
Screenshots of command run

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-14%2022-07-59.png![image](https://github.com/user-attachments/assets/7e6abcd1-a39c-4f1f-9ac2-52c40fc0d6ea)


Commands to load placement def in magic in another terminal
```c
# Change directory to path containing generated placement def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/14-11_16-15/results/placement/

# Command to load the placement def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```
Screenshot of placement def in magic

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-14%2022-07-59.png![image](https://github.com/user-attachments/assets/5eeb2fe5-937d-4ecd-9387-c64e968fcbb8)

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-14%2002-31-45.png![image](https://github.com/user-attachments/assets/1ea5a997-c72c-41f5-a7c1-e2e738159c87)

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-14%2002-40-14.png![image](https://github.com/user-attachments/assets/5b3477e4-6df3-45ba-b59e-8862d8a138aa)



### 9. Do Post-Synthesis timing analysis with OpenSTA tool.

Since we are having 0 wns after improved timing run we are going to do timing analysis on initial run of synthesis which has lots of violations and no parameters were added to improve timing

Commands to invoke the OpenLANE flow include new lef and perform synthesis

```c
# Change directory to openlane flow directory
cdccd
# alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
# Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
docker
# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

# Adiitional commands to include newly added lef to openlane flow
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis
```
Commands screenshot:

![image](https://github.com/user-attachments/assets/bec5cc0c-e7c3-4f84-b0d1-1fe1b4070638)

![image](https://github.com/user-attachments/assets/46d3ee81-1686-4af2-8469-e6ef4c3026a0)

**Newly created `pre_sta.conf` for STA analysis in openlane directory**

![image](https://github.com/user-attachments/assets/e28115e6-f06a-4ef9-a56d-96dc120d16d1)

Newly created `my_base.sdc` for STA analysis in `openlane/designs/picorv32a/src` directory based on the file `openlane/scripts/base.sdc`

![image](https://github.com/user-attachments/assets/9048298d-639d-4de2-8aa0-749ce74ad9d1)

Commands to run STA in another terminal
```c
# Change directory to openlane
cd Desktop/work/tools/openlane_working_dir/openlane

# Command to invoke OpenSTA tool with script
sta pre_sta.conf
```

Screenshots of commands run:

![image](https://github.com/user-attachments/assets/a9c15020-351f-4662-adbc-f0b97f757b79)

![image](https://github.com/user-attachments/assets/cc27fc0f-bb32-4c8a-addb-0fcfa4005bbb)

Since more fanout is causing more delay we can add parameter to reduce fanout and do synthesis again

Commands to include new lef and perform synthesis:

```c
# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a -tag 14-11_18-38 -overwrite

# Adiitional commands to include newly added lef to openlane flow
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Command to set new value for SYNTH_MAX_FANOUT
set ::env(SYNTH_MAX_FANOUT) 4

# Command to display current value of variable SYNTH_DRIVING_CELL to check whether it's the proper cell or not
echo $::env(SYNTH_DRIVING_CELL)

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis
```

Commands run final screenshot:

![image](https://github.com/user-attachments/assets/200a62ec-e03a-441f-96cf-c86028d9909c)

Commands to run STA in another terminal:

```c

# Change directory to openlane
cd Desktop/work/tools/openlane_working_dir/openlane

# Command to invoke OpenSTA tool with script
sta pre_sta.conf
```

Screenshots of commands run:

![image](https://github.com/user-attachments/assets/e31e7899-8461-4a22-a461-a7014acd8d3e)

### 10. Make timing ECO fixes to remove all violations.

OR gate of drive strength 2 is driving 4 fanouts

![image](https://github.com/user-attachments/assets/a591dec6-ae13-4cdf-a3a8-a3588ca57737)

Commands to perform analysis and optimize timing by replacing with OR gate of drive strength 4
```c
# Reports all the connections to a net
report_net -connections _11672_

# Checking command syntax
help replace_cell

# Replacing cell
replace_cell _14510_ sky130_fd_sc_hd__or3_4

# Generating custom timing report
report_checks -fields {net cap slew input_pins} -digits 4
```

Result - slack reduced

![image](https://github.com/user-attachments/assets/d675442e-2026-4033-9370-6b4d1270db4f)

Commands to perform analysis and optimize timing by replacing with OR gate of drive strength 4
```c
# Reports all the connections to a net
report_net -connections _11675_

# Replacing cell
replace_cell _14514_ sky130_fd_sc_hd__or3_4

# Generating custom timing report
report_checks -fields {net cap slew input_pins} -digits 4
```

Result - slack reduced

![image](https://github.com/user-attachments/assets/2c56f29f-c8b1-4ded-84b3-c806a95aaa6a)

OR gate of drive strength 2 driving OA gate has more delay

![image](https://github.com/user-attachments/assets/07728640-dbd0-4b3f-b73a-fffd4ab1aa57)

Commands to perform analysis and optimize timing by replacing with OR gate of drive strength 4
```c
# Reports all the connections to a net
report_net -connections _11668_

# Replacing cell
replace_cell _14506_ sky130_fd_sc_hd__or4_4

# Generating custom timing report
report_checks -fields {net cap slew input_pins} -digits 4
```
Result - slack reduced

![image](https://github.com/user-attachments/assets/2632bcea-c3b3-4e97-a52d-10572ca81085)

Commands to verify instance 14506 is replaced with sky130_fd_sc_hd__or4_4
```c
# Generating custom timing report
report_checks -from _29043_ -to _30440_ -through _14506_
```
Screenshot of replaced instance

![image](https://github.com/user-attachments/assets/2d1929c7-76dc-4dd2-8fac-f74f6adeb6e9)


### 11. Replace the old netlist with the new netlist generated after timing ECO fix and implement the floorplan, placement and cts.

Now to insert this updated netlist to PnR flow and we can use write_verilog and overwrite the synthesis netlist but before that we are going to make a copy of the old old netlist

Commands to make copy of netlist
```c
# Change from home directory to synthesis results directory
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/14-11_18-38 /results/synthesis/

# List contents of the directory
ls

# Copy and rename the netlist
cp picorv32a.synthesis.v picorv32a.synthesis_old.v

# List contents of the directory
ls
```

Screenshot of commands run

![image](https://github.com/user-attachments/assets/69912856-f7c2-4496-8c9b-8ac0860fb8a4)

Commands to write verilog
```c
# Check syntax
help write_verilog

# Overwriting current synthesis netlist
write_verilog /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/14-11_18-38/results/synthesis/picorv32a.synthesis.v

# Exit from OpenSTA since timing analysis is done
exit
```

Screenshot of commands run:

![image](https://github.com/user-attachments/assets/0638e49f-e4bb-431e-9da4-cc5749ea5f89)

Verified that the netlist is overwritten by checking that instance 14506 is replaced with `sky130_fd_sc_hd__or4_4`

![image](https://github.com/user-attachments/assets/0cba80f6-2b37-4fef-9f2d-0e5b1aec704a)

Since we confirmed that netlist is replaced and will be loaded in PnR but since we want to follow up on the earlier 0 violation design we are continuing with the clean design to further stages

Commands load the design and run necessary stages
```c
# Now once again we have to prep design so as to update variables
prep -design picorv32a -tag 14-11_18-38 -overwrite

# Addiitional commands to include newly added lef to openlane flow merged.lef
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to set new value for SYNTH_STRATEGY
set ::env(SYNTH_STRATEGY) "DELAY 3"

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis

# Follwing commands are alltogather sourced in "run_floorplan" command
init_floorplan
place_io
tap_decap_or

# Now we are ready to run placement
run_placement

# Incase getting error
unset ::env(LIB_CTS)

# With placement done we are now ready to run CTS
run_cts
```
![image](https://github.com/user-attachments/assets/d1b946a9-728c-43ef-9922-e8f194bf1ee0)

![image](https://github.com/user-attachments/assets/e9a759a5-5827-4462-b139-a8ea74c5a0f7)

![image](https://github.com/user-attachments/assets/3d979b59-6a1d-4658-913d-52472779f4ad)

![image](https://github.com/user-attachments/assets/517d2e69-a788-4f52-a3e8-17e3f649737b)

![image](https://github.com/user-attachments/assets/e2ee5951-f32b-4b03-80ae-af548d7ff507)

### 12. Post-CTS OpenROAD timing analysis.
Commands to be run in OpenLANE flow to do OpenROAD timing analysis with integrated OpenSTA in OpenROAD
```c
# Command to run OpenROAD tool
openroad

# Reading lef file
read_lef /openLANE_flow/designs/picorv32a/runs/14-11_18-38/tmp/merged.lef

# Reading def file
read_def /openLANE_flow/designs/picorv32a/runs/14-11_18-38/results/cts/picorv32a.cts.def

# Creating an OpenROAD database to work with
write_db pico_cts.db

# Loading the created database in OpenROAD
read_db pico_cts.db

# Read netlist post CTS
read_verilog /openLANE_flow/designs/picorv32a/runs/14-11_18-38/results/synthesis/picorv32a.synthesis_cts.v

# Read library for design
read_liberty $::env(LIB_SYNTH_COMPLETE)

# Link design and library
link_design picorv32a

# Read in the custom sdc we created
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

# Setting all cloks as propagated clocks
set_propagated_clock [all_clocks]

# Check syntax of 'report_checks' command
help report_checks

# Generating custom timing report
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

# Exit to OpenLANE flow
exit
```

Screenshots of commands run and timing report generated

![image](https://github.com/user-attachments/assets/573afa8e-bc3b-46b5-934e-6a683cb52f8d)

![image](https://github.com/user-attachments/assets/8feeef04-1620-4838-a0b8-334d0902216f)

![image](https://github.com/user-attachments/assets/e10bf969-2d5c-4835-ac8d-21bd1266b32c)


### 13. Explore post-CTS OpenROAD timing analysis by removing 'sky130_fd_sc_hd__clkbuf_1' cell from clock buffer list variable 'CTS_CLK_BUFFER_LIST'.
Commands to be run in OpenLANE flow to do OpenROAD timing analysis after changing CTS_CLK_BUFFER_LIST
```c
# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Removing 'sky130_fd_sc_hd__clkbuf_1' from the list
set ::env(CTS_CLK_BUFFER_LIST) [lreplace $::env(CTS_CLK_BUFFER_LIST) 0 0]

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Checking current value of 'CURRENT_DEF'
echo $::env(CURRENT_DEF)

# Setting def as placement def
set ::env(CURRENT_DEF) /openLANE_flow/designs/picorv32a/runs/14-11_18-38/results/placement/picorv32a.placement.def

# Run CTS again
run_cts

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Command to run OpenROAD tool
openroad

# Reading lef file
read_lef /openLANE_flow/designs/picorv32a/runs/14-11_18-38/tmp/merged.lef

# Reading def file
read_def /openLANE_flow/designs/picorv32a/runs/14-11_18-38/results/cts/picorv32a.cts.def

# Creating an OpenROAD database to work with
write_db pico_cts1.db

# Loading the created database in OpenROAD
read_db pico_cts.db

# Read netlist post CTS
read_verilog /openLANE_flow/designs/picorv32a/runs/14-11_18-38/results/synthesis/picorv32a.synthesis_cts.v

# Read library for design
read_liberty $::env(LIB_SYNTH_COMPLETE)

# Link design and library
link_design picorv32a

# Read in the custom sdc we created
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

# Setting all cloks as propagated clocks
set_propagated_clock [all_clocks]

# Generating custom timing report
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

# Report hold skew
report_clock_skew -hold

# Report setup skew
report_clock_skew -setup

# Exit to OpenLANE flow
exit

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)

# Inserting 'sky130_fd_sc_hd__clkbuf_1' to first index of list
set ::env(CTS_CLK_BUFFER_LIST) [linsert $::env(CTS_CLK_BUFFER_LIST) 0 sky130_fd_sc_hd__clkbuf_1]

# Checking current value of 'CTS_CLK_BUFFER_LIST'
echo $::env(CTS_CLK_BUFFER_LIST)
```

Screenshots of commands run and timing report generated:

![image](https://github.com/user-attachments/assets/63ee644c-a071-44a1-9e4a-74b7e048b5be)

![image](https://github.com/user-attachments/assets/521f5485-48b2-47b4-a9c4-79e1edf03a1d)

![image](https://github.com/user-attachments/assets/7da3baed-b0a3-42e2-b97f-010b71be9699)


</details> 





<details>
    <summary>Day-5:</summary>

## Final steps for RTL2GDS using tritonRoute and openSTA

1. Perform generation of Power Distribution Network (PDN) and explore the PDN layout.

Commands to perform all necessary stages up until now
```c
# Change directory to openlane flow directory
cd Desktop/work/tools/openlane_working_dir/openlane

# alias docker='docker run -it -v $(pwd):/openLANE_flow -v $PDK_ROOT:$PDK_ROOT -e PDK_ROOT=$PDK_ROOT -u $(id -u $USER):$(id -g $USER) efabless/openlane:v0.21'
# Since we have aliased the long command to 'docker' we can invoke the OpenLANE flow docker sub-system by just running this command
docker

# Now that we have entered the OpenLANE flow contained docker sub-system we can invoke the OpenLANE flow in the Interactive mode using the following command
./flow.tcl -interactive

# Now that OpenLANE flow is open we have to input the required packages for proper functionality of the OpenLANE flow
package require openlane 0.9

# Now the OpenLANE flow is ready to run any design and initially we have to prep the design creating some necessary files and directories for running a specific design which in our case is 'picorv32a'
prep -design picorv32a

# Addiitional commands to include newly added lef to openlane flow merged.lef
set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
add_lefs -src $lefs

# Command to set new value for SYNTH_STRATEGY
set ::env(SYNTH_STRATEGY) "DELAY 3"

# Command to set new value for SYNTH_SIZING
set ::env(SYNTH_SIZING) 1

# Now that the design is prepped and ready, we can run synthesis using following command
run_synthesis

# Following commands are alltogather sourced in "run_floorplan" command
init_floorplan
place_io
tap_decap_or

# Now we are ready to run placement
run_placement

# Incase getting error
unset ::env(LIB_CTS)

# With placement done we are now ready to run CTS
run_cts

# Now that CTS is done we can do power distribution network
gen_pdn 
```

Screenshots of power distribution network run 

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-15%2000-33-13.png![image](https://github.com/user-attachments/assets/97bc9df3-1220-4e8f-8147-fa2c05438b8e)

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-15%2000-34-43.png![image](https://github.com/user-attachments/assets/522637b2-7512-4e20-9200-269ec6cdb672)

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-15%2000-35-50.png![image](https://github.com/user-attachments/assets/6e89a146-573a-4ee9-95bd-c05c3ce2bb5e)

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-15%2000-35-54.png![image](https://github.com/user-attachments/assets/c814e19b-a4ef-4fc9-86cb-85f2ad8cc89b)


file:///home/vsduser/Pictures/Screenshot%20from%202024-11-15%2000-36-49.png![image](https://github.com/user-attachments/assets/7272a6fa-1e47-4423-ad63-fc1b0184c732)

Commands to load PDN def in magic in another terminal
```c
# Change directory to path containing generated PDN def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/14-11_19-02/tmp/floorplan/

# Command to load the PDN def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read 14-pdn.def &
```

Screenshots of PDN def 

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-15%2000-43-42.png![image](https://github.com/user-attachments/assets/6073c103-a95f-4766-9246-e6e06c296894)

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-15%2000-45-30.png![image](https://github.com/user-attachments/assets/09c7a9a2-3ee1-4cb4-830b-b4513f878706)

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-15%2000-47-26.png![image](https://github.com/user-attachments/assets/d6e15549-d845-4bb0-8f2e-80126a992d94)



2. Perfrom detailed routing using TritonRoute and explore the routed layout.

Command to perform routing
```c
# Check value of 'CURRENT_DEF'
echo $::env(CURRENT_DEF)

# Check value of 'ROUTING_STRATEGY'
echo $::env(ROUTING_STRATEGY)

# Command for detailed route using TritonRoute
run_routing
```
Screenshots of routing run

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-15%2001-12-30.png![image](https://github.com/user-attachments/assets/46bf90c6-2fc9-40e0-9717-290821c2182e)


file:///home/vsduser/Pictures/Screenshot%20from%202024-11-15%2001-12-37.png![image](https://github.com/user-attachments/assets/3ed3afe1-0d96-450d-8656-39d8c224b077)

Commands to load routed def in magic in another terminal
```c
# Change directory to path containing routed def
cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/14-11_19-02/results/routing/

# Command to load the routed def in magic tool
magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.def &
```
Screenshots of routed def 

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-15%2001-15-55.png![image](https://github.com/user-attachments/assets/9c9f8451-e8d6-4b6c-9ec9-883ab1a5337d)


file:///home/vsduser/Pictures/Screenshot%20from%202024-11-15%2001-17-03.png![image](https://github.com/user-attachments/assets/6bc3d116-8557-4f26-9602-0cb8d6d50845)


file:///home/vsduser/Pictures/Screenshot%20from%202024-11-15%2001-17-55.png![image](https://github.com/user-attachments/assets/4d065a60-c09d-48e3-8337-9ef09a988d88)


file:///home/vsduser/Pictures/Screenshot%20from%202024-11-15%2001-19-29.png![image](https://github.com/user-attachments/assets/d5906358-9720-450a-96ff-e66fa823c1f3)


Screenshot of fast route guide present in openlane/designs/picorv32a/runs/14-11_19-02/tmp/routing directory 

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-15%2001-21-57.png![image](https://github.com/user-attachments/assets/eea70011-7ea5-42b5-8a1d-a489686d2c8d)



3. Post-Route OpenSTA timing analysis with the extracted parasitics of the route.

Commands to be run in OpenLANE flow to do OpenROAD timing analysis with integrated OpenSTA in OpenROAD
```c
# Command to run OpenROAD tool
openroad

# Reading lef file
read_lef /openLANE_flow/designs/picorv32a/runs/14-11_19-02/tmp/merged.lef

# Reading def file
read_def /openLANE_flow/designs/picorv32a/runs/14-11_19-02/results/routing/picorv32a.def

# Creating an OpenROAD database to work with
write_db pico_route.db

# Loading the created database in OpenROAD
read_db pico_route.db

# Read netlist post CTS
read_verilog /openLANE_flow/designs/picorv32a/runs/14-11_19-02/results/synthesis/picorv32a.synthesis_preroute.v

# Read library for design
read_liberty $::env(LIB_SYNTH_COMPLETE)

# Link design and library
link_design picorv32a

# Read in the custom sdc we created
read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc

# Setting all cloks as propagated clocks
set_propagated_clock [all_clocks]

# Read SPEF
read_spef /openLANE_flow/designs/picorv32a/runs/14-11_19-02/results/routing/picorv32a.spef

# Generating custom timing report
report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4

# Exit to OpenLANE flow
exit
```
Screenshots of commands run and timing report generated

file:///home/vsduser/Pictures/Screenshot%20from%202024-11-15%2001-34-53.png![image](https://github.com/user-attachments/assets/7d4d5945-1796-4c04-818d-c3a09b82ab61)


file:///home/vsduser/Pictures/Screenshot%20from%202024-11-15%2001-35-21.png![image](https://github.com/user-attachments/assets/cbe9af8c-62a9-4986-bff9-96f4d9fab708)


</details>  



<details>
 
<summary> <h2>Task-13</h2> </summary>

## Task-13: OpenROAD Physical Design

### OpenRoad:

OpenROAD is a powerful, open-source tool designed for integrated circuit (IC) physical design, providing a comprehensive suite of features that spans the entire chip design flow. From RTL (Register Transfer Level) to GDSII (Graphic Data System II) generation, OpenROAD ensures an efficient, streamlined transition between design stages.

### Key Features:

**1. Synthesis:** OpenROAD integrates synthesis tools to convert RTL descriptions into gate-level netlists, which serve as the foundation for the subsequent design stages.

**2. Floorplanning:** It offers advanced floorplanning capabilities, enabling efficient area utilization, power distribution, and placement of functional blocks within the chip.

**3. Placement:** OpenROAD employs hierarchical placement algorithms that focus on minimizing wire length and congestion while improving performance.

**4. Routing:** The tool provides optimized routing solutions for signal and power paths, balancing performance with manufacturing constraints.

**5. Parasitic Extraction:** OpenROAD includes robust parasitic extraction features, allowing designers to extract capacitance, resistance, and inductance values for accurate circuit simulations.

**6. Timing Analysis:** With built-in static timing analysis (STA), OpenROAD ensures that the chip meets its timing requirements for reliable operation.

### Optimization:

**1. Timing Optimization:** OpenROAD optimizes the design to meet stringent timing constraints, enhancing performance by reducing delays and improving clock distribution.

**2. Power Optimization:** The tool also focuses on power consumption, providing techniques to reduce dynamic and leakage power through its placement and routing algorithms.

### Extensibility:

OpenROAD's modular architecture makes it highly extensible, allowing users to incorporate custom algorithms, tools, or third-party features into the flow. This flexibility ensures that it can be adapted to various design requirements or technological advancements.

By offering an integrated approach to IC physical design, OpenROAD significantly accelerates the development cycle, improving efficiency while reducing the need for manual intervention. This makes it an ideal solution for both academic research and industrial-scale chip design.

### Installing and setting up ORFS

```c
git clone --recursive https://github.com/The-OpenROAD-Project/OpenROAD-flow-scripts
cd OpenROAD-flow-scripts
sudo ./setup.sh
```

### Build

```c
./build_openroad.sh --local
```

![Screenshot from 2024-11-24 18-14-55](https://github.com/user-attachments/assets/730feb41-35b9-4149-9b0d-2034facf158e)

![Screenshot from 2024-11-24 18-15-05](https://github.com/user-attachments/assets/33cdd4df-17ac-4912-9c37-72af3ceb9cc4)

![Screenshot from 2024-11-24 18-43-51](https://github.com/user-attachments/assets/a0addd72-f01c-4737-be12-cecf3fc81a05)

![Screenshot from 2024-11-24 18-45-03](https://github.com/user-attachments/assets/a9fe480e-bb88-4e0c-9d89-88647fef0cec)

![Screenshot from 2024-11-24 19-14-24](https://github.com/user-attachments/assets/257e5c52-5f24-4341-8cfb-99044ef056e4)


### Verify Installation
```c
source ./env.sh
yosys -help
openroad -help
cd flow
make
```

![Screenshot from 2024-11-24 19-33-35](https://github.com/user-attachments/assets/1a6f440e-d993-4daa-a125-7952100c3eab)

![Screenshot from 2024-11-24 19-33-43](https://github.com/user-attachments/assets/a3b13ae6-885f-496f-a107-51dedc0cc9f8)

![Screenshot from 2024-11-24 19-33-52](https://github.com/user-attachments/assets/4536e8bd-4cb0-4c70-8d72-ffb2ee1726c4)



```c
make gui_final
```

![Screenshot from 2024-11-24 19-46-22](https://github.com/user-attachments/assets/568fe803-d956-4dd3-8c6d-0f0a6b11b73c)

![Screenshot from 2024-11-24 19-46-10](https://github.com/user-attachments/assets/340b5d89-8826-45c0-8a8b-1aed06d55c1e)


















</details>  


