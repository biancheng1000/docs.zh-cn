---
title: 通过使用分部方法添加业务逻辑
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3a73991e-fd4e-4610-93fb-7ced4dc6b7f9
ms.openlocfilehash: db18c48d697ae79f8c33c1674544f81cdd1c426a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="adding-business-logic-by-using-partial-methods"></a>通过使用分部方法添加业务逻辑
你可以自定义 Visual Basic 和 C# 生成的代码中的你[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]项目通过使用*分部方法*。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 生成的代码定义签名作为分部方法的一部分。 如果您要实现此方法，您可以添加自己的分部方法。 如果您不添加自己的实现，编译器将丢弃分部方法签名并调用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中的默认方法。  
  
> [!NOTE]
>  如果你使用的 Visual Studio，则可以使用[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]向实体类添加验证及其他自定义项。  
  
 例如，Northwind 示例数据库中 `Customer` 类的默认映射包括下面的分部方法：  
  
 [!code-csharp[DLinqOverrideDefault#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefault#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#2)]  
  
 您可以向自己的分部 `Customer` 类添加诸如以下内容的代码来实现自己的方法。  
  
 [!code-csharp[DLinqOverrideDefault#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefault#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/Module1.vb#3)]  
  
 在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中通常使用这种方式来重写 `Insert`、`Update`、`Delete` 的默认方法以及在对象生命周期事件过程中验证属性。  
  
 有关详细信息，请参阅[分部方法](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md)(Visual Basic 中) 或[分部 （方法） （C# 参考）](~/docs/csharp/language-reference/keywords/partial-method.md) (C#)。  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 下面的示例首先显示了 `ExampleClass`，因为它可能是由像 SQLMetal 这样的代码生成工具定义的；然后，此示例演示了如何只实现两个方法之一。  
  
### <a name="code"></a>代码  
 [!code-csharp[DLinqSubmittingChanges#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#4)]
 [!code-vb[DLinqSubmittingChanges#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#4)]  
  
## <a name="example"></a>示例  
  
### <a name="description"></a>描述  
 下面的示例用到了 `Shipper` 和 `Order` 实体之间的关系。 请注意这些方法中的分部方法 `InsertShipper` 和 `DeleteShipper`。 这些方法重写了由 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 映射提供的默认分部方法。  
  
### <a name="code"></a>代码  
 [!code-csharp[DLinqOverrideDefault#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefault#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#1)]  
  
## <a name="see-also"></a>请参阅  
 [进行和提交数据更改](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 [自定义插入、更新和删除操作](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
