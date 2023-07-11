1. 编写verilog代码，生成`.v`文件

2. ```c
   verilator -cc 文件名.v
   ```

3. 生成`obj_dir`文件夹，根据其中的`024root.h`文件编写`testbench.cpp`文件

4. 再次使用verilator对testbench文件和 .v文件进行共编译

```c
verilator -Wall --trace -cc 文件名.v --exe testbench.cpp
make -C obj_dir -f 文件名.mk 可执行文件名    
```

5. 运行仿真

```c
./obj_dir/可执行文件
```

