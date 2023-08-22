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


</details>

<details>
<summary>Day 2 </summary>
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
