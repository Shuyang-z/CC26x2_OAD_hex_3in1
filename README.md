# CC26x2_OAD_hex_3in1

本仓库存储的是将CC26x2 OAD所需的3个镜像文件合成一个单一文件所需的工具和步骤。


## 操作步骤：

### 1. 将simple_peripheral_oad_onchip_CC26X2R1_LAUNCHXL_tirtos_ccs_Debug_oad.bin转化成hex

   使用工具：output_converter.exe
   
   命令：
   ```
   cd <.bin所在文件夹>
   output_converter.exe -o simple_peripheral_oad_onchip_CC26X2R1_LAUNCHXL_tirtos_ccs_Debug_oad.hex simple_peripheral_oad_onchip_CC26X2R1_LAUNCHXL_tirtos_ccs_Debug_oad.bin
   ```
   更多使用方法请在命令行中运行output_converter.exe -h
   
   
### 2. 将上一步生成的hex文件以及persistent app和BIM hex文件合成一个hex

   使用工具：hexmerge
   
   命令：
   
   ```
   cd <.hex所在文件夹>
        
   hexmerge.exe -o simple_peripheral_oad_onchip_3in1.hex sp_oad_onchip_cc26x2r1lp_persistent_app_FlashROM_Debug.hex simple_peripheral_oad_onchip_CC26X2R1_LAUNCHXL_tirtos_ccs_Debug_oad_v0001.hex cc26x2r1lp_bim_onchip.hex
   ```
        
   其中-o后面的参数是输出文件名。更多使用方法请在命令行中运行hexmerge.exe -h
   
   
### 3. 上一步生成的hex可直接用于生产，如果想用bin文件生产，可以再将上一步的hex文件转成bin

   使用工具：hex2bin
   
   命令：
   
   ```
   cd <.hex所在文件夹>
        
   hex2bin_exe>hex2bin.exe simple_peripheral_oad_onchip_3in1.hex simple_peripheral_oad_onchip_3in1.bin
   ```
        
   更多使用方法请在命令行中运行hex2bin.exe -h
   
   
## 注：
output_converter.exe可以在cc2640r2f SDK中找到

hexmerge和hex2bin源代码请见：https://github.com/python-intelhex/intelhex

参考文档：https://zhuanlan.zhihu.com/p/35112093
