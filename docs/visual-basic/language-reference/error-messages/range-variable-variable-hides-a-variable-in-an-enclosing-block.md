---
title: 范围变量 <variable> 隐藏封闭块中的变量、以前定义的范围变量或在查询表达式中隐式声明的变量
ms.date: 07/20/2015
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
ms.openlocfilehash: 290ca81dea500558ed73956c91bdf7bfec312014
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400391"
---
# <a name="range-variable-variable-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a>范围变量 \<variable> 隐藏封闭块中的变量、以前定义的范围变量或在查询表达式中隐式声明的变量
在、、或子句中指定的范围变量名称会 `Select` `From` `Aggregate` `Let` 复制以前在查询中指定的范围变量的名称，或查询隐式声明的变量的名称，例如字段名称或聚合函数的名称。  
  
 **错误 ID：** BC36633  
  
## <a name="to-correct-this-error"></a>更正此错误  
  
- 确保特定查询范围内的所有范围变量都具有唯一的名称。 可以将查询括在括号中，以确保嵌套查询具有唯一的作用域。  
  
## <a name="see-also"></a>另请参阅

- [Visual Basic 中的 LINQ 简介](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [From 子句](../queries/from-clause.md)
- [Let 子句](../queries/let-clause.md)
- [Aggregate Clause](../queries/aggregate-clause.md)
- [Select 子句](../queries/select-clause.md)
