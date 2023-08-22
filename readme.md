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
