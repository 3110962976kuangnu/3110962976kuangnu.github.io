首先，在头文件中包含QSerialPortlnfo头文件：
`#include <QSerialPortInfo>`
连接信号
QSerialPortInfo serialPortInfo;
connect(&amp;serialPortInfo, &amp;QSerialPortInfo::availablePortsChanged, this, &随便干点啥);


这个槽函数会在串口插入或拔出时被调用，遍历所有可用串口并输出它们的状态。
最后，记得在析构函数中断开连接：
disconnect(&amp;serialPortInfo, &amp;QSerialPortInfo::availablePortsChanged, this, &随便干点啥);