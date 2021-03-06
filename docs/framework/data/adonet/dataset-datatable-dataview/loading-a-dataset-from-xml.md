---
title: 从 XML 加载数据集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
ms.openlocfilehash: 0b74480209c8d06f38ea39e7a89741fc5a89512b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="loading-a-dataset-from-xml"></a>从 XML 加载数据集
ADO.NET <xref:System.Data.DataSet> 的内容可以从 XML 流或文档创建。 此外，利用 .NET Framework，您可以相当灵活地控制从 XML 中加载哪些信息以及如何创建 <xref:System.Data.DataSet> 的架构（即关系结构）。  
  
 若要填充<xref:System.Data.DataSet>与 XML 中的数据，使用**ReadXml**方法<xref:System.Data.DataSet>对象。 **ReadXml**方法从文件、 流，读取或**XmlReader**，并将作为自变量的 XML 以及可选的源**XmlReadMode**自变量。 (有关详细信息**XmlReader**，请参阅[NIB： 读取 XML 数据与 XmlTextReader](http://msdn.microsoft.com/library/762c069b-b50c-41b8-936e-39eacfb0d540)。)**ReadXml**方法读取 XML 流或文档和加载的内容<xref:System.Data.DataSet>使用数据。 它还将创建的关系架构<xref:System.Data.DataSet>具体取决于**XmlReadMode**指定，并且是否关系架构已存在。  
  
 下表描述的选项**XmlReadMode**自变量。  
  
|选项|描述|  
|------------|-----------------|  
|**Auto**|这是默认设置。 检查 XML 并按如下顺序选择最适合的选项：<br /><br /> -如果 XML 为 DiffGram， **DiffGram**使用。<br />-如果<xref:System.Data.DataSet>包含架构或 XML 包含内联架构， **ReadSchema**使用。<br />-如果<xref:System.Data.DataSet>不包含架构且 XML 不包含内联架构， **InferSchema**使用。<br /><br /> 如果你知道所读取的 XML 的格式，以获得最佳性能建议设置显式**XmlReadMode**，而不是接受**自动**默认值。|  
|**ReadSchema**|读取内联架构并加载数据和架构。<br /><br /> 如果 <xref:System.Data.DataSet> 已包含架构，则新表将从内联架构添加到 <xref:System.Data.DataSet> 中的现有架构。 如果 <xref:System.Data.DataSet> 中已存在内联架构中的任何表，则将引发异常。 你将不能修改现有的表使用的架构**XmlReadMode.ReadSchema**。<br /><br /> 如果 <xref:System.Data.DataSet> 不包含架构，并且没有内联架构，则不会读取任何数据。<br /><br /> 内联架构可以使用 XML 架构定义语言 (XSD) 架构来定义。 有关编写内联架构作为 XML 架构的详细信息，请参阅[派生数据集关系结构从 XML 架构 (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)。|  
|**IgnoreSchema**|忽略任何内联架构并将数据加载到现有的 <xref:System.Data.DataSet> 架构中。 任何与现有架构不匹配的数据都将被丢弃。 如果 <xref:System.Data.DataSet> 中不存在任何架构，则不会加载任何数据。<br /><br /> 如果数据为 DiffGram， **IgnoreSchema**具有与相同的功能**DiffGram** *。*|  
|**InferSchema**|忽略任何内联架构并按照 XML 数据的结构推断架构，然后加载数据。<br /><br /> 如果 <xref:System.Data.DataSet> 已经包含架构，则会通过向现有表中添加列来扩展当前架构。 如果不存在表，则不会添加其他表。 如果已存在具有不同命名空间的推断表或者任何推断表与现有列发生冲突，则会引发异常。<br /><br /> 有关详细信息，有关如何**ReadXmlSchema**推断架构从 XML 文档，请参阅[推断数据集关系结构从 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)。|  
|**DiffGram**|读取 DiffGram 并将数据添加到当前架构中。 **DiffGram**会将新行的唯一标识符的值匹配的现有行合并。 请参见本主题末尾的“合并 XML 中的数据”。 有关 Diffgram 的详细信息，请参阅[Diffgram](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)。|  
|**片段**|持续读取多个 XML 片断，直至到达流的末尾。 与 <xref:System.Data.DataSet> 架构匹配的片断会追加到相应的表。 与 <xref:System.Data.DataSet> 架构不匹配的片断将被丢弃。|  
  
> [!NOTE]
>  如果你通过**XmlReader**到**ReadXml**定位的一部分的方式插入 XML 文档， **ReadXml**将读取至下一个元素节点并将其当作根元素，元素节点仅结束之前一直读取。 这不适用于如果指定**XmlReadMode.Fragment**。  
  
## <a name="dtd-entities"></a>DTD 实体  
 如果你尝试加载，如果 XML 包含文档类型定义 (DTD) 架构中定义的实体，将引发异常<xref:System.Data.DataSet>通过传递文件名称、 流或非验证**XmlReader**到**ReadXml**。 相反，您必须创建**XmlValidatingReader**，与**EntityHandling**设置为**EntityHandling.ExpandEntities**，并传递你**XmlValidatingReader**到**ReadXml**。 **XmlValidatingReader**将之前扩展实体被读取<xref:System.Data.DataSet>。  
  
 以下代码示例显示如何从 XML 流中加载 <xref:System.Data.DataSet>。 第一个示例演示文件名传递给**ReadXml**方法。 第二个示例显示一个字符串，包含使用 <xref:System.IO.StringReader> 加载的 XML。  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXml("input.xml", XmlReadMode.ReadSchema)  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXml("input.xml", XmlReadMode.ReadSchema);  
```  
  
```vb  
Dim dataSet As DataSet = New DataSet  
Dim dataTable As DataTable = New DataTable("table1")  
dataTable.Columns.Add("col1", Type.GetType("System.String"))  
dataSet.Tables.Add(dataTable)  
  
Dim xmlData As String = "<XmlDS><table1><col1>Value1</col1></table1><table1><col1>Value2</col1></table1></XmlDS>"  
  
Dim xmlSR As System.IO.StringReader = New System.IO.StringReader(xmlData)  
  
dataSet.ReadXml(xmlSR, XmlReadMode.IgnoreSchema)  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
DataTable dataTable = new DataTable("table1");  
dataTable.Columns.Add("col1", typeof(string));  
dataSet.Tables.Add(dataTable);  
  
string xmlData = "<XmlDS><table1><col1>Value1</col1></table1><table1><col1>Value2</col1></table1></XmlDS>";  
  
System.IO.StringReader xmlSR = new System.IO.StringReader(xmlData);  
  
dataSet.ReadXml(xmlSR, XmlReadMode.IgnoreSchema);  
```  
  
> [!NOTE]
>  如果调用**ReadXml**若要加载非常大的文件，你可能会遇到性能变慢。 若要确保最佳性能**ReadXml**，对于大文件，调用<xref:System.Data.DataTable.BeginLoadData%2A>每个表中的方法<xref:System.Data.DataSet>，，然后调用**ReadXml**。 最后，为 <xref:System.Data.DataTable.EndLoadData%2A> 中的每个表调用 <xref:System.Data.DataSet>，如下面的示例所示。  
  
```vb  
Dim dataTable As DataTable  
  
For Each dataTable In dataSet.Tables  
   dataTable.BeginLoadData()  
Next  
  
dataSet.ReadXml("file.xml")  
  
For Each dataTable in dataSet.Tables  
   dataTable.EndLoadData()  
Next  
```  
  
```csharp  
foreach (DataTable dataTable in dataSet.Tables)  
   dataTable.BeginLoadData();  
  
dataSet.ReadXml("file.xml");   
  
foreach (DataTable dataTable in dataSet.Tables)  
   dataTable.EndLoadData();  
```  
  
> [!NOTE]
>  如果的 XSD 架构你<xref:System.Data.DataSet>包括**targetNamespace**，不能读取数据，且调用时，你可能会发生异常， **ReadXml**加载<xref:System.Data.DataSet>与包含的 XML与非限定命名空间的元素。 若要读取未限定的元素在这种情况下，设置**elementFormDefault**等于"qualified"中的 XSD 架构。 例如：  
  
```xml  
<xsd:schema id="customDataSet"   
  elementFormDefault="qualified"  
  targetNamespace="http://www.tempuri.org/customDataSet.xsd"   
  xmlns="http://www.tempuri.org/customDataSet.xsd"   
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
  xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
</xsd:schema>  
```  
  
## <a name="merging-data-from-xml"></a>合并 XML 中的数据  
 如果 <xref:System.Data.DataSet> 已经包含数据，则会向已存在于 <xref:System.Data.DataSet> 中的数据添加 XML 中的新数据。 **ReadXml**不会合并从 XML 向<xref:System.Data.DataSet>任何具有匹配的主键行信息。 若要使用 XML 的新信息覆盖现有行信息，请使用**ReadXml**创建新<xref:System.Data.DataSet>，，然后<xref:System.Data.DataSet.Merge%2A>新<xref:System.Data.DataSet>到现有<xref:System.Data.DataSet>。 请注意，加载 DiffGram 使用**ReadXML**与**XmlReadMode**的**DiffGram**将合并具有相同的唯一标识符的行。  
  
## <a name="see-also"></a>请参阅  
 <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>  
 [在数据集中使用 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)  
 [从 XML 架构派生数据集关系结构 (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 [从 XML 推断数据集关系结构](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [从 XML 加载数据集构架信息](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [数据集、数据表和数据视图](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET 托管提供程序和数据集开发人员中心](http://go.microsoft.com/fwlink/?LinkId=217917)
