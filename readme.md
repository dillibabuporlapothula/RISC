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
</details>

<details>
<summary>Day 4 </summary>
</details>

<details>
<summary>Day 5 </summary>
</details>
