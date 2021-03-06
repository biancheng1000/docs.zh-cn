---
title: 如何：调用运算符过程 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedure calls [Visual Basic], operator overloading
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- overloaded operators [Visual Basic], calling
- operator overloading
ms.assetid: 0dce42cc-f0b0-4c14-9f62-018b21f33497
ms.openlocfilehash: b1dc4477daa4ceb9dfc6a9a6ab3f041e68011acd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a>如何：调用运算符过程 (Visual Basic)
通过在表达式中使用运算符调用运算符过程。 对于转换运算符，你调用[CType 函数](../../../../visual-basic/language-reference/functions/ctype-function.md)将值从一种数据类型转换为另一个。  
  
 不显式调用运算符过程。 只需使用运算符，或`CType`函数，在赋值语句或表达式，通常使用运算符相同的方式。 Visual Basic 进行到运算符过程的调用。  
  
 在类或结构上定义一个运算符也称为*重载*运算符。  
  
### <a name="to-call-an-operator-procedure"></a>若要调用运算符过程  
  
1.  运算符的表达式中使用普通的方式。  
  
2.  请确保操作数的数据类型是适合于运算符，且按正确的顺序。  
  
3.  按预期方式，运算符将分配给表达式的值。  
  
### <a name="to-call-a-conversion-operator-procedure"></a>若要调用转换运算符过程  
  
1.  使用`CType`在表达式内部。  
  
2.  请确保数据类型的操作数不适合进行转换，且正确顺序。  
  
3.  `CType` 调用转换运算符过程并返回转换后的值。  
  
## <a name="example"></a>示例  
 下面的示例创建两个<xref:System.TimeSpan>结构，并将它们相加，并将结果存储在第三个<xref:System.TimeSpan>结构。 <xref:System.TimeSpan>结构定义运算符过程重载了几个标准运算符。  
  
 [!code-vb[VbVbcnProcedures#29](./codesnippet/VisualBasic/how-to-call-an-operator-procedure_1.vb)]  
  
 因为<xref:System.TimeSpan>重载标准`+`运算符，则在计算的值前面的示例调用运算符过程`combinedSpan`。  
  
 调用会话运算符过程的示例，请参阅[如何： 使用此类定义运算符的类](./how-to-use-a-class-that-defines-operators.md)。  
  
## <a name="compiling-the-code"></a>编译代码  
 请确保类或结构将定义你想要使用的运算符。  
  
## <a name="see-also"></a>请参阅  
 [运算符过程](./operator-procedures.md)  
 [如何：定义运算符](./how-to-define-an-operator.md)  
 [如何：定义转换运算符](./how-to-define-a-conversion-operator.md)  
 [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Widening](../../../../visual-basic/language-reference/modifiers/widening.md)  
 [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [Structure 语句](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [如何：声明结构](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [隐式转换和显式转换](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [扩大转换和收缩转换](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
