---
title: IAppDomainSetup 接口
ms.date: 03/30/2017
api_name:
- IAppDomainSetup
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IAppDomainSetup
helpviewer_keywords:
- IAppDomainSetup interface [.NET Framework hosting]
ms.assetid: 1844da85-c031-40bf-bea4-1a3d12a36c8c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cbcbc446eabcfcbc28c830f8860bde726c8eb6e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="iappdomainsetup-interface"></a>IAppDomainSetup 接口
提供的属性，使该主机可配置<xref:System.AppDomain?displayProperty=nameWithType>类型之前调用[icorruntimehost:: Createdomainex](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)方法来创建它。  
  
## <a name="properties"></a>属性  
  
|属性|描述|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|获取或设置包含应用程序的目录的名称。|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|获取或设置应用程序的名称。|  
|<xref:System.AppDomainSetup.CachePath%2A>|获取或设置特定于应用程序的、 从中对文件进行卷影复制使用的区域名称。|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|获取或设置应用程序的配置文件的名称。|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|获取或设置在其中存储和访问动态生成的文件的目录的名称。|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|获取或设置与此域关联的许可证文件的路径。|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|获取或设置的结合的目录列表<xref:System.AppDomainSetup.ApplicationBase%2A>目录探测专用程序集。|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|获取或设置一个字符串值，包括或排除<xref:System.AppDomainSetup.ApplicationBase%2A>应用程序的搜索路径中。|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|获取或设置包含要进行影像复制程序集的目录的名称。|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|获取或设置指示是否卷影复制打开还是关闭的字符串。 有效值为"true"或"false"。|  
  
## <a name="remarks"></a>备注  
 `IAppDomainSetup`接口对应于托管<xref:System.IAppDomainSetup>接口，该接口<xref:System.AppDomainSetup>类型实现。 请参阅<xref:System.IAppDomainSetup?displayProperty=nameWithType>有关其属性的详细说明。  
  
 `IAppDomainSetup` 表示可以添加到的程序集绑定信息<xref:System.AppDomain>之前创建的实例。 例如，主机可以设置<xref:System.AppDomainSetup.ApplicationBase%2A>属性建立公共语言运行时 (CLR) 来探测程序根目录的托管程序集。  
  
## <a name="requirements"></a>要求  
 **平台：**请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** MSCorEE.h  
  
 **库：**作为 MSCorEE.dll 中的资源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>请参阅  
 <xref:System.AppDomain>  
 <xref:System.AppDomainSetup>  
 <xref:System.IAppDomainSetup>  
 [承载接口](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
