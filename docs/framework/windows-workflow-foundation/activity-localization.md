---
title: 活动本地化
ms.date: 03/30/2017
ms.assetid: 8ee7bc16-e609-469a-a3e8-8062952e2676
ms.openlocfilehash: 23a6d5c2ed202f030397eb70382896468a68a724
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="activity-localization"></a>活动本地化
当工作流应用程序和组件可能要根据其他区域文化和语言进行本地化时，应使用资源字符串，以便无需重新编译即可对它们进行本地化。  
  
## <a name="activity-localization"></a>活动本地化  
 与必须本地化（针对不同的语言和区域文化发布不同的版本）的所有应用程序一样，向用户显示的任何字符串不应直接放在代码中，而应存储在某个资源文件中。 然后可以通过访问这些字符串<!--zz <xref:System.Environment.GetResourceString> --> `GetResourceString`。 如果您开发的某个组件以多种语言分发，则还需要对活动验证消息、用户定义的跟踪数据、跟踪消息以及错误消息使用资源字符串。  
  
 下面的练习演示如何使用资源文件。  
  
#### <a name="using-resource-files-for-localized-strings"></a>对本地化的字符串使用资源文件  
  
1.  在[!INCLUDE[vs2010](../../../includes/vs2010-md.md)]，右键单击你的项目中**解决方案资源管理器**和选择**添加...**，**新建项...**.  
  
2.  选择**资源文件**并将文件命名为 ErrorResources.resx。 单击 **添加**。  
  
3.  打开该资源文件。 添加一个新项**名称**为 ErrorString 和**值**的"活动无效。"  
  
4.  向类中添加以下 `using` 声明。  
  
    ```  
    using System.Reflection;  
    using System.Resources;  
    ```  
  
5.  在项目中创建一个资源管理器。  
  
    ```  
    ResourceManager ErrorManager;  
    ...  
    ErrorManager = new ResourceManager("MyNamespace.ErrorResources", Assembly.GetExecutingAssembly());  
    ```  
  
6.  从资源管理器中获取字符串，该字符串在资源管理器中是必需的。  
  
    ```  
    String errorMessage = ErrorManager.GetString("ErrorString");  
    ```  
  
 以下代码示例演示了如何在 <xref:System.Activities.Activity.CacheMetadata%2A> 方法中使用本地化的字符串。  
  
```  
       protected override void CacheMetadata(CodeActivityMetadata metadata)  
        {  
           .....  
          // rest of the code elided for brevity  
           .....  
            if (this.Value != null && this.To != null)  
            {  
                if (!TypeHelper.AreTypesCompatible(this.Value.ArgumentType, this.To.ArgumentType))  
                {  
//---------------------------------------------  
// ** SR.TypeMismatchForAssign will fetch the string from the resource manager **  
//---------------------------------------------  
                    metadata.AddValidationError(SR.TypeMismatchForAssign(  
                                this.Value.ArgumentType,  
                                this.To.ArgumentType,  
                                this.DisplayName));  
                }  
            }  
        }  
```
