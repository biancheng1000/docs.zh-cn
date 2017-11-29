---
title: "CorDebugIntercept 枚举"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugIntercept
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugIntercept
helpviewer_keywords: CorDebugIntercept enumeration [.NET Framework debugging]
ms.assetid: 3d5b642e-7ef2-428b-a5ae-509c35ed461a
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b7d34b5f1bdff7a7089d780645b91503a8464849
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugintercept-enumeration"></a><span data-ttu-id="49409-102">CorDebugIntercept 枚举</span><span class="sxs-lookup"><span data-stu-id="49409-102">CorDebugIntercept Enumeration</span></span>
<span data-ttu-id="49409-103">指示可截获（即可单步执行）的代码的类型。</span><span class="sxs-lookup"><span data-stu-id="49409-103">Indicates the types of code that can be intercepted (that is, stepped into).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49409-104">语法</span><span class="sxs-lookup"><span data-stu-id="49409-104">Syntax</span></span>  
  
```  
typedef enum CorDebugIntercept {  
    INTERCEPT_NONE                = 0x0,  
    INTERCEPT_CLASS_INIT          = 0x01,  
    INTERCEPT_EXCEPTION_FILTER    = 0x02,  
    INTERCEPT_SECURITY            = 0x04,  
    INTERCEPT_CONTEXT_POLICY      = 0x08,  
    INTERCEPT_INTERCEPTION        = 0x10,  
    INTERCEPT_ALL                 = 0xffff  
} CorDebugIntercept;  
```  
  
## <a name="members"></a><span data-ttu-id="49409-105">成员</span><span class="sxs-lookup"><span data-stu-id="49409-105">Members</span></span>  
  
|<span data-ttu-id="49409-106">成员</span><span class="sxs-lookup"><span data-stu-id="49409-106">Member</span></span>|<span data-ttu-id="49409-107">描述</span><span class="sxs-lookup"><span data-stu-id="49409-107">Description</span></span>|  
|------------|-----------------|  
|`INTERCEPT_NONE`|<span data-ttu-id="49409-108">未截获任何代码。</span><span class="sxs-lookup"><span data-stu-id="49409-108">No code can be intercepted.</span></span>|  
|`INTERCEPT_CLASS_INIT`|<span data-ttu-id="49409-109">可以截获构造函数。</span><span class="sxs-lookup"><span data-stu-id="49409-109">A constructor can be intercepted.</span></span>|  
|`INTERCEPT_EXCEPTION_FILTER`|<span data-ttu-id="49409-110">可以截获异常筛选器。</span><span class="sxs-lookup"><span data-stu-id="49409-110">An exception filter can be intercepted.</span></span>|  
|`INTERCEPT_SECURITY`|<span data-ttu-id="49409-111">可以截获强制保护的代码。</span><span class="sxs-lookup"><span data-stu-id="49409-111">Code that enforces security can be intercepted.</span></span>|  
|`INTERCEPT_CONTEXT_POLICY`|<span data-ttu-id="49409-112">可以截获上下文策略。</span><span class="sxs-lookup"><span data-stu-id="49409-112">A context policy can be intercepted.</span></span>|  
|`INTERCEPT_INTERCEPTION`|<span data-ttu-id="49409-113">未使用。</span><span class="sxs-lookup"><span data-stu-id="49409-113">Not used.</span></span>|  
|`INTERCEPT_ALL`|<span data-ttu-id="49409-114">可以截获所有代码。</span><span class="sxs-lookup"><span data-stu-id="49409-114">All code can be intercepted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49409-115">备注</span><span class="sxs-lookup"><span data-stu-id="49409-115">Remarks</span></span>  
 <span data-ttu-id="49409-116">使用[icordebugstepper:: Setinterceptmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md)方法建立可以截获的代码类型。</span><span class="sxs-lookup"><span data-stu-id="49409-116">Use the [ICorDebugStepper::SetInterceptMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md) method to establish the types of code that can be intercepted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49409-117">要求</span><span class="sxs-lookup"><span data-stu-id="49409-117">Requirements</span></span>  
 <span data-ttu-id="49409-118">**平台：**请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="49409-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49409-119">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="49409-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="49409-120">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49409-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49409-121">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49409-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49409-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="49409-122">See Also</span></span>  
 [<span data-ttu-id="49409-123">调试枚举</span><span class="sxs-lookup"><span data-stu-id="49409-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)