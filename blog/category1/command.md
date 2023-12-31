---
title: 计算常用命令
keywords: 指令
desc: teedoc 生成静态博客页面, 第3篇博客
author: derk
date: 2023-12-11
tags: DFT, blog, Gaussian
---





<strong><center><font face="微软雅黑" color=maroon size=5>常用命令与设置参数</font></center></strong>
<center><font face="Consolas" size=3>06/12-23 by Qiao</font></center>


<strong><font face="微软雅黑" color=blue size=4>定时执行命令at</font></strong><br><br><font face="Consolas" size=3>at -V 「查看是否安装at命令」</font><br><font face="Consolas" size=3>sudo systemctl enable --now atd</font><br><font face="Consolas" size=3>（启动 at 守护进程，称为 atd 。 在大多数 Linux 系统上，你可以使用 systemctl 命令启用 atd 服务并将它们设置为从现在开始自动启动）</font><br><font face="Consolas" size=3>echo "g09 < 1.gjf > 1.out" | at 1:30 </font><br><font face="Consolas" size=3>(在1:30执行命令g09 < 1.gjf > 1.out)</font><br><font face="Consolas" size=3>atq (查看 at 任务队列)</font><br><font face="Consolas" size=3>atrm 7 (要从队列中删除任务，请使用 atrm 命令和任务编号。例如要删除任务7)</font><br>

<strong><font face="微软雅黑" color=blue size=4>xtb的基本使用</font></strong><br>

<font face="Consolas" size=3>参考命令：xtb 1.xyz --opt extreme --gfn 2  
xtb的输入文件就是一个xyz文件，这是最常用的记录分子结构的格式之一，很多程序都可以产生。用Multiwfn产生也可以，可以把fch、pdb、mol、wfn、wfx、molden等Multiwfn能认的格式载入Multiwfn，然后进入主功能100的子功能2，选择输出xyz文件。由于这个文件格式非常简单，比如自己把Gaussian的.gjf文件编辑一下产生也可以。<br>
xtb的详细使用说明也可以通过xtb -h查看。几个比较常用的选项如下<br>
-c或--chrg：设定体系净电荷 <br>
-u或--uhf：设定alpha电子数减beta电子数（相当于自旋多重度减1）<br>
-g或--gbsa：使用隐式溶剂模型。目前支持的溶剂有toluene、thf、methanol、h2o、ether、chcl3、acetonitrile、acetone、cs2<br>
--molden：计算结束后产生molden.input，这是Molden输入文件 <br>
--gfn：选择GFN-xTB理论的版本，可以为0、1、2。如--gfn 0就代表GFN0-xTB。GFN2-xTB物理上最严格，多数情况精度最佳，但有时候SCF收敛困难；GFN1-xTB不如GFN2-xTB严格，平均精度稍逊一点，但SCF收敛容易（因此明显更适合SCF难收敛的金属团簇等情况），耗时也比GFN2-xTB低一些。GFN0-xTB精度最烂但速度也最快，非常适合快速简单粗暴地搞巨大体系，但对于找过渡态的目的就太糙了而不建议用<br>
常用任务类型：<br>
--sp：计算单点（此为默认，可不写）<br>
--grad：计算梯度<br>
--opt [级别]：几何优化。级别默认为normal，更佳的是tight、verytight、extreme<br>
--hess：计算数值Hessian并做振动分析<br>
--ohess [级别]：优化后自动计算Hessian并做振动分析<br>
--md：基于当前结构做分子动力学（目前xtb还支持metadynamics，详见手册）<br>
--omd：优化后做分子动力学<br>
例如：<br>
对yoshiko.xyz做真空中的单点计算，电荷为1，自旋多重度为2（alpha比beta电子多1个）：xtb yoshiko.xyz --chrg 1 --uhf 1 -sp<br> 
对yohane.xyz做甲苯溶剂下优化和振动分析。体系是默认的中性单重态：xtb yohane.xyz --ohess --gbsa toluene  
xtb运行时一方面会在屏幕上输出信息，同时也会在当前目录下产生一大堆文件。这些文件的含义在自带的文档里有说明。  
xtb目前有解析梯度，但只支持数值Hessian。--hess或-ohess任务做完会输出g98.out和g98_canmode.out。前者是模仿高斯freq输出格式来输出频率、红外强度、正则坐标。后者没用。  
--opt任务产生的xtbopt.xyz是最后结构的xyz坐标文件，其中第二行是对应的能量。xtbopt.log是含有优化过程每一帧的多帧xyz文件，后缀改为.xyz后就可以拖入VMD查看优化轨迹。  
Multiwfn可以载入xtb用--molden产生的molden.input文件做十分丰富的波函数分析，相关知识看《Multiwfn波函数分析程序的意义、功能与用途》（http://sobereva.com/184）、《Multiwfn入门tips》（http://sobereva.com/167）。  
Multiwfn载入--hess或--ohess的输出文件后，进主功能11，选择IR或Raman，进入界面后选0就可以绘制出相应的光谱，超级容易。更多信息见《使用Multiwfn绘制红外、拉曼、UV-Vis、ECD、VCD和ROA光谱图》（http://sobereva.com/224）。</font><br>
  
<strong><font face="微软雅黑" color=blue size=4>lampps常用命令</font></strong><br>

<font face="Consolas" size=3>安装参考： https://zhuanlan.zhihu.com/p/337947153<br>
运行命令<br> 
mpirun -np 2 ~/lammps/build/lmp -in ~/lammps/examples/deposit/in.deposit.atom 3374<br>
mpirun -np 4 ~/lammps/build/lmp -in ~/lammps/examples/deposit/in.deposit.atom 4437<br>
mpirun -np 6 ~/lammps/build/lmp -in ~/lammps/examples/deposit/in.deposit.atom 5057<br>
mpirun -np 8 ~/lammps/build/lmp -in ~/lammps/examples/deposit/in.deposit.atom 5794<br>
mpirun -np 10 ~/lammps/build/lmp -in ~/lammps/examples/deposit/in.deposit.atom 6533<br>
mpirun -np 12 ~/lammps/build/lmp -in ~/lammps/examples/deposit/in.deposit.atom 7589<br>
mpirun -np 14 ~/lammps/build/lmp -in ~/lammps/examples/deposit/in.deposit.atom 6850<br>
mpirun -np 16 ~/lammps/build/lmp -in ~/lammps/examples/deposit/in.deposit.atom 5302</font><br>

