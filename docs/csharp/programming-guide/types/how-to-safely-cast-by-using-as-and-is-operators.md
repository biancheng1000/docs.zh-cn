---
title: 如何：使用 as 和 is 运算符安全地进行强制转换（C# 编程指南）
ms.date: 07/20/2015
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.assetid: c1176cea-1426-4a44-8570-3eadafa58863
ms.openlocfilehash: 6e02675a2a895add245d3c2e40305a0417fdf429
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-safely-cast-by-using-as-and-is-operators-c-programming-guide"></a>如何：使用 as 和 is 运算符安全地进行强制转换（C# 编程指南）
由于是多态对象，基类类型的变量可以保存派生类型。 若要访问派生类型的方法，必须将值强制转换回派生类型。 但是，在这些情况下尝试简单的强制转换会产生引发 <xref:System.InvalidCastException> 的风险。 这就是 C# 提供 [is](../../../csharp/language-reference/keywords/is.md) 和 [as](../../../csharp/language-reference/keywords/as.md) 运算符的原因。 这些运算符可用于测试强制转换是否会成功且不引发异常。 一般情况下，`as` 运算符更高效，因为如果可以成功执行强制转换，实际上它会返回强制转换值。 `is` 运算符只返回一个布尔值。 因此，可以在只需确定对象类型，无需实际强制转换时使用。  
  
## <a name="example"></a>示例  
 以下示例演示如何使用 `is` 和 `as` 运算符将一种引用类型强制转换为另一种引用类型，且无引发异常的风险。 该示例还演示如何将 `as` 运算符用于可以为 null 的值类型。  
  
 [!code-csharp[csProgGuideTypes#40](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-safely-cast-by-using-as-and-is-operators_1.cs)]  
  
## <a name="see-also"></a>请参阅  
 [类型](../../../csharp/programming-guide/types/index.md)  
 [强制转换和类型转换](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [可以为 null 的类型](../../../csharp/programming-guide/nullable-types/index.md)
