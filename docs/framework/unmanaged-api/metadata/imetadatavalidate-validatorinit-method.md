---
title: "IMetaDataValidate::ValidatorInit 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataValidate.ValidatorInit
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataValidate::ValidatorInit
helpviewer_keywords:
- IMetaDataValidate::ValidatorInit method [.NET Framework metadata]
- ValidatorInit method [.NET Framework metadata]
ms.assetid: 6bafd75a-e2d0-4aea-aed1-074374d5dff6
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e2a9b265b4fcc75406f5d5f1dbddb8bd74b5832d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/18/2017
---
# <a name="imetadatavalidatevalidatorinit-method"></a><span data-ttu-id="93b8d-102">IMetaDataValidate::ValidatorInit 方法</span><span class="sxs-lookup"><span data-stu-id="93b8d-102">IMetaDataValidate::ValidatorInit Method</span></span>
<span data-ttu-id="93b8d-103">设置一个标志，该标志指定当前元数据范围内的模块类型，并注册验证错误的指定回调方法。</span><span class="sxs-lookup"><span data-stu-id="93b8d-103">Sets a flag that specifies the type of the module in the current metadata scope, and registers the specified callback method for validation errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93b8d-104">语法</span><span class="sxs-lookup"><span data-stu-id="93b8d-104">Syntax</span></span>  
  
```  
HRESULT ValidatorInit (  
   [in] DWORD       dwModuleType,  
   [in] IUnknown    *pUnk  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="93b8d-105">参数</span><span class="sxs-lookup"><span data-stu-id="93b8d-105">Parameters</span></span>  
 `dwModule`  
 <span data-ttu-id="93b8d-106">[in]值为[CorValidatorModuleType](../../../../docs/framework/unmanaged-api/metadata/corvalidatormoduletype-enumeration.md)枚举当前元数据范围内指定的模块类型。</span><span class="sxs-lookup"><span data-stu-id="93b8d-106">[in] A value of the [CorValidatorModuleType](../../../../docs/framework/unmanaged-api/metadata/corvalidatormoduletype-enumeration.md) enumeration that specifies the type of the module in the current metadata scope.</span></span>  
  
 `pUnk`  
 <span data-ttu-id="93b8d-107">[in]一个指向 <<!--zzxref:IUnknown --> `IUnknown`> 用作验证错误回调函数的实例。</span><span class="sxs-lookup"><span data-stu-id="93b8d-107">[in] A pointer to an <<!--zzxref:IUnknown --> `IUnknown`> instance that serves as a function callback for validation errors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93b8d-108">要求</span><span class="sxs-lookup"><span data-stu-id="93b8d-108">Requirements</span></span>  
 <span data-ttu-id="93b8d-109">**平台：**请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="93b8d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93b8d-110">**标头：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="93b8d-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="93b8d-111">**库：**用作 MsCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="93b8d-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="93b8d-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93b8d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93b8d-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="93b8d-113">See Also</span></span>  
 [<span data-ttu-id="93b8d-114">IMetaDataValidate 接口</span><span class="sxs-lookup"><span data-stu-id="93b8d-114">IMetaDataValidate Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-interface.md)