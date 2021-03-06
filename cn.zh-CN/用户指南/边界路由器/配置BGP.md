# 配置BGP {#concept_ljj_4vx_dfb .concept}

您可以在本地数据中心和边界路由器间建立BGP路由。只需要将与VBR通信的BGP邻居添加到对应的BGP组中，然后在VBR中宣告BGP网段即可。

**说明：** 高速通道仅支持在边界路由器和本地数据中心之间建立BGP路由。在物理专线接入过程中，您仍需要为边界路由器添加指向VPC和专线的路由，详情参见[添加路由条目](intl.zh-CN/用户指南/边界路由器/添加路由条目.md#)。

## BGP介绍 {#section_e3x_wwx_dfb .section}

BGP（Border Gateway Protocol）是一种基于TCP协议的动态路由协议，主要应用于不同自治域间交换路由信息和网络可达信息。在物理专线接入的过程中，您可以使用BGP来实现本地数据中心与边界路由器（VBR）之间的内网互连。BGP可以帮您更高效、灵活且可靠地搭建混合云。

在配置BGP前，您需要创建BGP组。BGP组主要用于简化BGP配置，将需要不断重复的配置合并到一个BGP组后，可以减少配置复杂度。您只需根据ASN建立一个BGP组，然后将符合条件的BGP邻居加入此BGP组即可。加入BGP组之后，BGP邻居将继承BGP组的配置，您不再需要单独配置BGP邻居。

## 使用限制 {#section_ksj_qxx_dfb .section}

BGP的使用限制如下：

-   VBR仅支持与物理专线对端的本地数据中心建立BGP邻居，VBR与VPC之间仍需使用静态路由。
-   VBR支持的BGP版本为BGP4。
-   VBR支持IPv4 BGP，不支持IPv6 BGP。
-   每个VBR下最多建立8个BGP邻居。
-   每个BGP邻居的动态路由条数上限为100条。
-   阿里云侧ASN（Autonomous System Number）为：45104，可接受用户侧传递2字节或4字节的ASN。

## 步骤一 创建BGP组 {#section_uks_sxx_dfb .section}

在配置BGP路由前，您需要根据申请的ASN创建一个BGP组。

完成以下操作，创建BGP组：

1.  登录[高速通道管理控制台](https://expressconnectnext.console.aliyun.com)。
2.  在左侧导航栏，单击**物理专线连接** \> **边界路由器（VBR）**。
3.  选择一个地域，然后单击目标VBR的ID。
4.  单击**BGP组**页签，然后单击**创建BGP组**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21437/154201679212049_zh-CN.png)

5.  配置BGP组，然后单击**确定**。

    |配置|说明|
    |:-|:-|
    |**名称**|输入BGP组的名称。|
    |**Peer AS号**|输入本地数据中心侧网络的AS \(Autonomous System\) 号码。|
    |**BGP秘钥**|输入该BGP组的密钥。|
    |**描述**|输入BGP组的描述信息。|


## 步骤二 添加BGP邻居 {#section_lpj_tyx_dfb .section}

完成以下操作，添加BGP邻居：

1.  登录[高速通道管理控制台](https://expressconnectnext.console.aliyun.com)。
2.  在左侧导航栏，单击**物理专线连接** \> **边界路由器（VBR）**。
3.  选择一个地域，然后单击目标VBR的ID。
4.  单击**BGP邻居**页签，然后单击**创建BGP邻居**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21437/154201679212050_zh-CN.png)

5.  添加BGP邻居，然后单击**确定**。

    |配置|说明|
    |:-|:-|
    |**BGP组**|选择要加入的BGP组。|
    |**BGP邻居IP**|输入BGP邻居IP。|


## 步骤三 宣告BGP网段 {#section_lbw_wzx_dfb .section}

在配置BGP邻居后，您需要宣告本地IDC的网段，完成BGP配置。

完成以下操作，宣告本地IDC的网段：

1.  登录[高速通道管理控制台](https://expressconnectnext.console.aliyun.com)。
2.  在左侧导航栏，单击**物理专线连接** \> **边界路由器（VBR）**。
3.  选择一个地域，然后单击目标VBR的ID。
4.  单击**宣告BGP网段**页签，然后单击**宣告BGP网段**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21437/154201679312051_zh-CN.png)

5.  输入要宣告的网段，然后单击**确定**。

