<details>
<summary> Tools installation  </summary>
  
### commands to install toolchain

```
git clone https://github.com/kunalg123/riscv_workshop_collaterals.git
cd riscv_workshop_collaterals
chmod +x run.sh
./run.sh

```

```
cd ~/riscv_toolchain/iverilog/
git checkout v10-branch
git pull 
chmod 777 autoconf.sh 
./autoconf.sh 
./configure 
make
sudo make install
```

### set path variable in bashrc file

The below commands will create path variable in bashrc file. 

```
gedit .bashrc
export PATH="/home/dilli/riscv_toolchain/riscv64-unknown-elf-gcc-8.3.0-2019.08.0-x86_64-linux-ubuntu14/bin:$PATH" 
source .bashrc
```

</details>

<details>
<summary>Day 1 </summary>

## Application to hardware flow
  
![Screenshot (12)](https://github.com/dillibabuporlapothula/RISCV/assets/141803312/3a2a9565-23f5-43f3-a6ec-e46495ed173c)

![Screenshot (13)](https://github.com/dillibabuporlapothula/RISCV/assets/141803312/748498f6-9979-48ab-b857-93f51cf3b239)

## Lab for software toolchain

### compiling simple c program

use below commands to compile and see the output of c program : sum of n natural numbers

```
gedit sum1ton.c
gcc sum1ton.c
./a.out

```
![sum1ton](https://github.com/dillibabuporlapothula/RISCV/assets/141803312/163f3601-dc88-4561-ad04-3a96ef1d6cfa)

![program o_p](https://github.com/dillibabuporlapothula/RISCV/assets/141803312/d36e5451-5253-49e6-b900-f4bc078fd4a7)

### GCC compile and disassemble

```
riscv64-unknown-elf-gcc -O1 -mabi=lp64 -march=rv64i -o sum1ton.o sum1ton.c
riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o sum1ton_ofast.o sum1ton.c
riscv64-unknown-elf-objdump -d sum1ton_O1.o | less

```

![disassemble](https://github.com/dillibabuporlapothula/RISCV/assets/141803312/9e7a00e6-6685-49fd-b78a-9523737ccbda)

By using -ofast

![ofast](https://github.com/dillibabuporlapothula/RISCV/assets/141803312/6c1e373c-2e24-4e71-9627-2a4ca36b6d83)

### spike simulation

```
spike -d pk sum1ton.o 
```
![spike](https://github.com/dillibabuporlapothula/RISCV/assets/141803312/345bddb6-a8f4-4897-a566-3e5d088500ac)
![Screenshot (14)](https://github.com/dillibabuporlapothula/RISCV/assets/141803312/709e741c-191b-4402-964c-ab3f6b8f5cf8)



</details>

<details>
<summary>Day 2 </summary>

## Application binary interface(ABI) and verification flow

![Screenshot (15)](https://github.com/dillibabuporlapothula/RISCV/assets/141803312/c0c69b5e-7337-4776-8c16-6ba5c84a39cb)

```
riscv64-unknown-elf-gcc -Ofast -mabi=lp64 -march=rv64i -o sum1to9_custom.o sum1to9_custom.c load.S
riscv64-unknown-elf-objdump -d sum1to9_custom.o | less
spike pk sum1to9_custom.o
```
![code](https://github.com/dillibabuporlapothula/RISCV/assets/141803312/6eee55c0-d07f-4fff-9c58-bce35443f524)
![execution](https://github.com/dillibabuporlapothula/RISCV/assets/141803312/af914a45-9e47-4265-9944-ba7fb1d1f9c7)
![machinecode](https://github.com/dillibabuporlapothula/RISCV/assets/141803312/a1a290e9-86fc-44fa-8fa5-0c7f7e2ebb3e)

### how to run C program on RISCV CPU

![Screenshot (16)](https://github.com/dillibabuporlapothula/RISCV/assets/141803312/2afe9f33-1f5a-4195-b7bf-f328acdb43fa)
![Screenshot (17)](https://github.com/dillibabuporlapothula/RISCV/assets/141803312/091c90c0-46d6-406c-ade5-eeb78262d319)

```
cd riscv_workshop_collaterals/labs/
chmod 777 rv32im.sh
./rv32im.sh 
```
![2  1](https://github.com/dillibabuporlapothula/RISCV/assets/141803312/17570320-10eb-4198-8aa1-fd1e32179348)

![2 2 - hex](https://github.com/dillibabuporlapothula/RISCV/assets/141803312/60288216-042c-44df-9763-4c56007c7e38)

</details>

<details>
<summary>Day 3 </summary> 

  # Digital Logic with TL-Verilog and Makerchip

  ## Combinational logic
  
  pythagorean on markerchip

![Screenshot (18)](https://github.com/dillibabuporlapothula/RISCV/assets/141803312/a85e7f2e-ee05-483b-a2c2-29eca1bd17a4)

  Inverter on markerchip 

  ```
   $out = $in;
  ```
![Screenshot (19)](https://github.com/dillibabuporlapothula/RISCV/assets/141803312/76ab1634-15e1-457c-bf3e-2a8e547401ad)


  Two input AND gate

  ```
   $out = $in1 && $in2;
  ```
![Screenshot (20)](https://github.com/dillibabuporlapothula/RISCV/assets/141803312/89b291c5-8d66-4715-ab14-efb879f2b713)


 vector addition

 ```
   $out[5:0] = $in1[4:0] + $in2[4:0];
 ```
 ![Screenshot (21)](https://github.com/dillibabuporlapothula/RISCV/assets/141803312/dcc45835-5d17-46d9-955a-97ca966b8586)


  Calculator

  ```
   $reset = *reset;
   $op[1:0] = $random[1:0];
   
   $val1[31:0] = $rand1[3:0];
   $val2[31:0] = $rand2[3:0];
   $sum[31:0] = $val1+$val2;
   $diff[31:0] = $val1-$val2;
   $prod[31:0] = $val1*$val2;
   $div[31:0] = $val1/$val2;
   
   $out[31:0] = $op[1] ? ($op[0] ? $div : $prod):($op[0] ? $diff : $sum);

 ```

![Screenshot (22)](https://github.com/dillibabuporlapothula/RISCV/assets/141803312/b65a384d-9371-4b8d-a65d-e25d83c3a423)

  
  
</details>

<details>
<summary>Day 4 </summary>

# Program Counter

TL-verilog code is

```
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
   
   // Optional:
   // m4_asm(JAL, r7, 00000000000000000000) // Done. Jump to itself (infinite loop). (Up to 20-bit signed immediate plus implicit 0 bit (unlike JALR) provides byte address; last immediate bit should also be 0)
   m4_define_hier(['M4_IMEM'], M4_NUM_INSTRS)

   |cpu
      @0
         $reset = *reset;



      // YOUR CODE HERE
      // ...
      @0
         $pc[31:0] = >>1$reset ? 32'd0 : (>>1$pc+32'd4);
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
      //m4+imem(@1)    // Args: (read stage)
      //m4+rf(@1, @1)  // Args: (read stage, write stage) - if equal, no register bypass is required
      //m4+dmem(@4)    // Args: (read/write stage)
      //m4+myth_fpga(@0)  // Uncomment to run on fpga

   //m4+cpu_viz(@4)    // For visualisation, argument should be at least equal to the last stage of CPU logic. @4 would work for all labs.
\SV
   endmodule
```
![Screenshot (23)](https://github.com/dillibabuporlapothula/RISCV/assets/141803312/06595bd7-a9af-49d8-8d0c-b8a0921d49d8)


# Instruction fetch

TL-verliog code:

```
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
   
   // Optional:
   // m4_asm(JAL, r7, 00000000000000000000) // Done. Jump to itself (infinite loop). (Up to 20-bit signed immediate plus implicit 0 bit (unlike JALR) provides byte address; last immediate bit should also be 0)
   m4_define_hier(['M4_IMEM'], M4_NUM_INSTRS)

   |cpu
      @0
         $reset = *reset;



      // YOUR CODE HERE
      // ...
      @0
         $pc[31:0] = >>1$reset ? 32'd0 : (>>1$pc+32'd4);
      @1
         $imem_rd_en = !$reset;
         $imem_rd_addr[M4_IMEM_INDEX_CNT-1:0] = $pc[M4_IMEM_INDEX_CNT+1:2];
         $instr[31:0] = $imem_rd_data[31:0];
      ?$imem_rd_en
         @1
            $imem_rd_data[31:0] = /imem[$imem_rd_addr]$instr;
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
      //m4+rf(@1, @1)  // Args: (read stage, write stage) - if equal, no register bypass is required
      //m4+dmem(@4)    // Args: (read/write stage)
      //m4+myth_fpga(@0)  // Uncomment to run on fpga

   m4+cpu_viz(@4)    // For visualisation, argument should be at least equal to the last stage of CPU logic. @4 would work for all labs.
\SV
   endmodule
```
![Screenshot (24)](https://github.com/dillibabuporlapothula/RISCV/assets/141803312/cb822251-9b3c-4fc3-bc07-eccca9e72d75)


</details>

<details>
<summary>Day 5 </summary>
</details>
