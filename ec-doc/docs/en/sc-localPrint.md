<h5 id="start"></h5>

### Local Print Service

<aside>
💡 Local print service refers to the service of connecting printers directly to a local computer or network environment for printing operations. Unlike cloud printing, local printing does not require internet or third-party relay applications, so you don't have to worry about network stability or data security. In local print service, users only need to ensure that the printer is correctly connected to the local computer or network and that the appropriate printer drivers and certificates are installed on the computer.
</aside>
<br>

#### **1. Initial Setup: Configure Print Parameters**

**1.1 Download and Start:** Please visit [Print Terminal](download.md) to download the print application.

**1.2 Set Connection Parameters:** After starting, you need to follow the instructions to set the connection parameters.

```
Server Address:
    https://192.168.32.245:17521
```

① Set function  
② Device number of the current machine  
③ Select the printer to print

<img src="../_images/zh-cn/本地打印服务_初始设置.png" style="width: 50%;"></img>

① Port number of the print service, can be set arbitrarily.  
② Name of the current print service device, can be set arbitrarily.  
③ Cloud print switch, off for local printing, on for cloud printing.

<img src="../_images/zh-cn/本地打印服务_设定功能.png" style="width: 50%;"></img>

#### **2. Local Print Service Configuration**

**2.1 Enter Print Settings Interface:** Click the "Print Service Setting" tab to enter the print service configuration interface.

![Local Print Service_Print Service Setting](../_images/zh-cn/本地打印服务_打印服务设置.png)

**2.2 Create or Edit Print Service:** In this interface, you can create a new local print service or edit existing configurations.

![Local Print Service_Create or Edit](../_images/zh-cn/本地打印服务_新建或编辑.gif)

**2.3 View Connected Print Devices:** If you have correctly configured, the connected print devices information will be displayed under the local print configuration.

![Local Print Service_View Connected Devices](../_images/zh-cn/本地打印服务_查看连接设备.gif)

**2.4 Download Certificate:** By default, local print service is not connected. Click the "Certificate Download" button, and after configuring the certificate, the connected print devices information will be displayed.

![Local Print Service_Download Certificate](../_images/zh-cn/本地打印服务_下载证书.gif)