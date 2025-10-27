# 调试工具说明

## Checkpoint功能

Checkpoint功能有助于系统的调试，优化运行流程。

首先，在LA_EMU中保存Checkpoint。

可使用以下命令运行：
```shell
cd ./LA_EMU
make
make ckp KERNEL_DIR={path/to/your/linux/} CHECKPOINT_PC=####
```
其中，CHECKPOINT_PC即为期望保存现场的PC值。

LA_EMU运行时，如果运行到与CHECKPOINT_PC对应的现场，终端即会打印相关信息。

![](../_static/sim/debug/ckp_run_1.png)


执行命令后，在LA_EMU目录下，即可获得Checkpoint相关文件。

![](../_static/sim/debug/ckp_run_2.png)

进入到`{PATH_LoongChipX}/verif/config`目录中，进行以下操作。
``` shell
cd {/path/to/LoongChipX}/verif/config
vim config.kernel.checkpoint
```
编译checkpoint的对应配置文件如下。
``` shell
image_dir= {path_to_LA_EMU} 	#Checkpoint保存文件路径
kernel=../../../ext/simu-kernel/vmlinux # linux kernel路径
```
使用以下命令进行：
``` shell
cd {/path/to/LoongChipX}/verif/verilator/VerSimCKP
make CXX=clang
```
模型会加载Checkpoint文件中的regs，csr，mem等值，过程显示如下。

![](../_static/sim/debug/ckp_run_3.png)



## Difftest功能

待补充。