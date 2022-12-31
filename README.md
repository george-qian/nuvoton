# nuvoton
主要的no os代码资料
https://github.com/OpenNuvoton/MPU-Family

## 开发环境部署过程：
1. 接线(接线贼难受，差评)

   1.1 开发板上J2端子ICE与JTAG引脚链接关系：

   - RST - 15(RESET),

   - TDO - 13(TDO),

   - VSS - 4~12(GND),

   - TCK - 9(TCK),

   - TMS - 7(TMS),

   - TDI -5(TDI),

   - TRST - 3(nTRST),

   - VDD33 - 19 (5V - SUPPLY)

   ![jtag引脚定义](JTAG.svg)

2. 安装开发环境

   2.1 安装keil mdk5.18.exe

   2.2 安装keil518 legacy support for arm mdk79518.exe(装了支持arm9开发)

   2.3 安装jlink驱动Setup_JLinkARM_V408l.exe
   
      - 避免mdk调试时，弹框提示更新jlink：点更新，更新完成后，将\Program Files (x86)\SEGGER\JLinkARM_V408l目录下文件覆盖到\Keil_v5\ARM\Segger目录下

3. 下载示例代码

   开发板是：N9H30系列，[地址](https://github.com/OpenNuvoton/N9H30_NonOS)

    正式芯片是：NUC970系列，[地址](https://github.com/OpenNuvoton/NUC970_NonOS_BSP)

    下载后打开SampleCode/hello/Keil/hello.uvproj工程。
    
4. 配置工程
    【重点】
    1. 修改Options for Target...|Debug下的ULink2/Me arm debugger改为J-link/J-trace arm。
    - 旁边的Settings下Reset Strategy设为No Reset。
    2. 同样，修改Options for Target...|Utilities下的ULink2/Me arm debugger改为J-link/J-trace arm。

# 即可在线调试代码！！（仅在片内ram中调试）

5. 烧录程序

#    *****说明：由于没有片内flash，MDK无法下载程序到flash！因此需要用icp工具下载。

    使用NuWriter下载程序，驱动及源代码下载[地址](https://github.com/OpenNuvoton/NUC970_NuWriter)

    1. 安装驱动，WinUSB4NuVCOM.exe

    2. 接线，电脑usb接开发板micro usb

    3. 拨码开关，SW4的 1->ON 2->ON，（usb boot模式），复位开发板

    4. 打开NuWriter.exe
