---
title: 编译器警告（等级 4）C4913
ms.date: 11/04/2016
f1_keywords:
- C4913
helpviewer_keywords:
- C4913
ms.assetid: b94aa52e-6029-4170-9134-017714931546
ms.openlocfilehash: 8858f116b34451e5c7509d9aff9bb99f438c3b36
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "74989003"
---
# <a name="compiler-warning-level-4-c4913"></a>编译器警告（等级 4）C4913

**存在用户定义的二进制运算符“,”，但没有重载可以转换所有操作数，使用了默认的内置二进制运算符“,”**

对内置逗号运算符的调用发生在同样具有重载的逗号运算符的程序中；你认为可能已发生的转换没有发生。

下面的示例生成 C4913：

```cpp
// C4913.cpp
// compile with: /W4
struct A
{
};

struct S
{
};

struct B
{
   // B() { }
   // B(S &s) { s; }
};

B operator , (A a, B b)
{
   a;
   return b;
}

int main()
{
   A a;
   B b;
   S s;

   a, b;   // OK calls user defined operator
   a, s;   // C4913 uses builtin comma operator
           // uncomment the conversion code in B to resolve.
}
```
