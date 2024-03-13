# Power_Test_Demo

### TPS62130RGTT Buck Circuit Design

> TPS6213x系列Buck电源芯片型号分为可调节和固定输出电压两种，均采用 3x3mm 16引脚VQFN封装；
>
> **TPS62130 and TPS62130A (Adjustable Output Voltage)**，可调节电压输出；
>
> **TPS62131/2/3 (Fixed Output Voltage)**，固定电压输出；

#### 1.  **Feature Description** 功能描述

* **1.1  Enable / Shutdown (EN)**
  * Enable(EN) 拉高时，设备芯片开始正常运行；
  * 如果 EN 被拉低，芯片则关断（关断电流通常为1.5uA）;
  * 关断期间，内部功率 MOSFET以及整个控制电路均关闭，内部电阻分压器拉低输出电压；
  * EN信号必须在外部控制拉高或者拉低；
  * EN引脚连接到另一个电源轨的适当输出信号可提供多个电源轨排序，可以控制多电源Soc上电时序；
* **1.2  Soft Start / Tracking (SS/TR)**
  * 内部软启动控制启动期间的输出电压斜率；
  * EN引脚拉高时，此器件大约在50us的延迟后开始开关，Vout输出电压由连接在 SS/TR 引脚的外部电容来控制斜率上升；
  * SS/TR外接容值比较小的电容（或者不连接 SS/TR引脚）可以快速启动；
* **1.3  Power Good (PG) **
  * TPS62130x 具有内置电源(PG)功能，可指示输出电压是否已达到适当水平；
  * PG信号可用于多各电源轨的启动排序；
  * PG引脚时开漏输出，需要上拉电阻(低于7V以下任何电压)，它可吸收2mA电流并保持其指定的逻辑低电平；
  * 对于TPS62130来说，当器件因EN、UVLO或热关断而关闭时，PG引脚处于高阻抗，在此情况下**TPS62130A**的PG引脚为低电平，可用于主动对Vout进行放电（<u>放电速率可通过PG引脚上拉电阻调节，为了可靠性，保持流入PG引脚的最大电流小于10mA</u>），Vin必须保持存在，PG引脚才能保持低电平；
* **1.4  Pin-Selectable Output Voltage (DEF)**
  * 
* **1.5  Frequency Selection (FSW)**
* **1.6  Undervoltage Lockout (UVLO)**
* **1.7  Thermal Shutdown**
* 