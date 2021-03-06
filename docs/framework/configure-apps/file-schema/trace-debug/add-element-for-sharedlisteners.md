---
title: '&lt;添加&gt;元素&lt;sharedListeners&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <sharedListeners>
- add element for <sharedListeners>
ms.assetid: 1595e1bc-2492-421f-8384-7f382eb8eb57
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 27d83ba706b4d93b4ac5426bf5bae59b4bfc0d9a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-element-for-ltsharedlistenersgt"></a>&lt;添加&gt;元素&lt;sharedListeners&gt;
将侦听器添加到 `sharedListeners` 集合中。 `sharedListeners` 是的侦听器集合的任何[\<源 >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)或[\<跟踪 >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)可以引用。  默认情况下，侦听器中`sharedListeners`集合不都将置于`Listeners`集合。 它们肯定会添加到名称[\<源 >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)或[\<跟踪 >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)。 不能获取侦听器`sharedListeners`在运行时在代码中的集合。  
  
 \<configuration>  
\<system.diagnostics >  
\<sharedListeners > 元素  
\<add>  
  
## <a name="syntax"></a>语法  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|`name`|必需的特性。<br /><br /> 指定用于将共享的侦听器添加到侦听器的名称`Listeners`集合。|  
|`type`|必需的特性。<br /><br /> 指定侦听器的类型。 你必须使用满足要求中指定的字符串[指定完全限定的类型名称](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)。|  
|`initializeData`|可选特性。<br /><br /> 传递给构造函数指定类的字符串。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<filter>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-sharedlisteners.md)|将筛选器添加到 `sharedListeners` 集合中的侦听器。|  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。|  
|`system.diagnostics`|指定用于收集、存储和路由消息的跟踪侦听器以及对跟踪开关设置的级别。|  
|`sharedListeners`|任何源或跟踪元素可以引用的侦听器集合。|  
  
## <a name="remarks"></a>备注  
 随.NET Framework 提供的侦听器类派生自<xref:System.Diagnostics.TraceListener>类。 值`name`特性用于将共享的侦听器添加到`Listeners`跟踪或跟踪源的集合。 值`initializeData`属性取决于你创建的侦听器的类型。 并非所有的跟踪侦听器需要你指定`initializeData`。  
  
> [!NOTE]
>  当你使用`initializeData`属性中，你可能会收到编译器警告"未声明 initializeData 特性。" 因为配置设置验证针对的抽象基类，会出现此警告<xref:System.Diagnostics.TraceListener>，这不能识别`initializeData`属性。 通常情况下，你可以忽略此警告的具有构造函数采用参数的跟踪侦听器实现。  
  
 下表显示.NET Framework 附带的跟踪侦听器，并描述的值的其`initializeData`属性。  
  
|跟踪侦听器类|initializeData 特性值|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|`useErrorStream`值<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>构造函数。  设置`initializeData`属性设为"`true`"编写跟踪和调试输出发送到标准错误流; 将其设置为"`false`"要写入到标准输出流。|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|文件的名称<xref:System.Diagnostics.DelimitedListTraceListener>写入。|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|现有的事件日志源的名称。|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|文件的名称，<xref:System.Diagnostics.EventSchemaTraceListener>写入。|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|文件的名称，<xref:System.Diagnostics.TextWriterTraceListener>写入。|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|文件的名称，<xref:System.Diagnostics.XmlWriterTraceListener>写入。|  
  
## <a name="configuration-file"></a>配置文件  
 计算机配置文件 (Machine.config) 和应用程序配置文件中，可以使用此元素。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用`<add>`要添加元素<xref:System.Diagnostics.TextWriterTraceListener>`textListener`到`sharedListeners`集合。   `textListener` 按名称添加到`Listeners`跟踪源集合`TraceSourceApp`。 `textListener`侦听器将跟踪输出写入文件 myListener.log。  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"   
        type="System.Diagnostics.TextWriterTraceListener"   
        initializeData="myListener.log"/>  
    </sharedListeners>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a>请参阅  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 [跟踪和调试设置架构](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [跟踪侦听器](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
