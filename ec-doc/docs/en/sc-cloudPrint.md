<h5 id="start"></h5>

### Cloud Print Service

<aside>
💡 Cloud printing technology connects printing devices via the internet, supporting remote printing. After completing the design, you can directly send it to a remote printer, regardless of geographic location. Cloud printing improves efficiency and flexibility, allowing you to print anytime and anywhere with simple configuration. Easily modify settings to switch devices or locations seamlessly. Cloud printing brings great convenience and efficiency to printing.
</aside>
<br>

#### **1. Initial Setup: Configure Print Relay Application (Skip if already configured)**

**1.1 Download and Start:** Please visit [Print Terminal](download.md) to download the print relay application.

**1.2 Set Connection Parameters:** After starting, you need to follow the instructions to set the connection parameters for the print relay application.
> Please send an email to info@e-cloudsoft.com to obtain a server token for testing purposes.

```
Server Address:
    https://print.e-cloudsoft.com:8443
Server Token (provided after purchase):
    4a504e303030303031313233343536
```

① Set function  
② Device number of the current machine  
③ Select the printer to print

<img src="../_images/zh-cn/云打印服务_初始设置.png" style="width: 50%;"></img>

① Port number of the print service, can be set arbitrarily.  
② Name of the current print service device, can be set arbitrarily.  
③ Cloud print switch, off for local printing, on for cloud printing.  
④ Cloud print configuration, fill in the cloud print address and TOKEN to print through the cloud.

<img src="../_images/zh-cn/云打印服务_设定功能.png" style="width: 50%;"></img>

#### **2. Cloud Print Service Configuration**

**2.1 Enter Print Settings Interface:** Click the "Print Service Setting" tab to enter the print service configuration interface.

![Cloud Print Service_Print Service Setting](../_images/zh-cn/云打印服务_打印服务设置.png)

**2.2 Create or Edit Print Service:** In this interface, you can create a new cloud print service or edit existing configurations.

![Cloud Print Service_Create or Edit](../_images/zh-cn/云打印服务_新建或编辑.gif)

**2.3 View Connected Print Devices:** If you have correctly configured the print relay application, the connected print devices information will be displayed under the cloud print configuration, ensuring you can identify and select the correct print device.

![Cloud Print Service_View Connected Devices](../_images/zh-cn/云打印服务_查看连接设备.gif)