移植falshDB步骤
1. 下载 FlashDB和 SFUD两个代码库 [FLashDB](https://gitee.com/Armink/FlashDB/tree/master)  [SFUD](https://gitee.com/Armink/SFUD)
2.  将项目文件添加到项目中 关键文件如下：
2.1.  sfud库文件包括：sfud.c sfud_sfdp.c sfud_port.c
2.2  fal库文件包括 :fal.c fal_flash.c fal_partition.c
2.3  flashDB库文件包括： fdb.c fdb.file.c fdb_kvdb.c fdb_tsdb.c fdb-utils.c 
2.4  头文件夹包括 
* SFUD\sfud\inc
* FlashDB\port\fal\inc
* FlashDB\inc
2.5  在 flashDB\inc文件夹中 找到 fdb_cfg_template.h 复制一份并修改为 fdb_cfg.h
2.6  在 flashDB\port\fal\src中 新建fal_falsh_sfud_port.c并加入项目中 内容何以仿照FlashDB\port\fal\samples\porting\fal_flash_sfud_port.c中的内容。
		
			
3.  修改sfud库中的 sfud_port文件内容 主要是编写spi_write_read函数，和sfud_spi_port_init
4.  修改sfud_cfg.h文件，调整 SFUD_FLASH_DEVICE_TABLE中的falsh配置。如果使用的falsh不支持JEDEC切sfud未添加支持，则需要在sfud_flash_def.h文件中 增加相关内容。
5.  调整fal_falsh_sfud_port.c 使他配合时机falsh情况，在使用sfud的情况下 配合sfud相关函数，
6. 在 fal_cfg.h中 调整fal分区表（FAL_PART_TABLE）和和falsh设备表（FAL_FLASH_DEV_TABLE） 分区表的第二个项目是分区名称，需要在后续数据库初始化时使用。设备表中的项目来自于 前面添加的fal_falsh_sfud_port.c中的结构体。
7. 在合适的位置增加printf兼容移植内容，方便debug部分输出。
8. 初始化部分流程：sfud_init()→sfud_device_init()→fal_init()→fdb_xxdb_init()在没有出错的情况下 就已经可以进行falshdb的功能的使用了。