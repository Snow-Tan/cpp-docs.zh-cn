---
title: 编译器警告（等级1） C4190
ms.date: 11/04/2016
f1_keywords:
- C4190
helpviewer_keywords:
- C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
ms.openlocfilehash: 6d110aa70a470382e274546e95599804fa3bc7d6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199870"
---
# <a name="compiler-warning-level-1-c4190"></a>编译器警告（等级1） C4190

"identifier1" 指定了 C 链接，但返回了与 C 不兼容的 UDT "identifier2"

函数或指向函数的指针具有 UDT （用户定义的类型，它是类、结构、枚举或联合）作为返回类型并 `extern` "C" 链接。 这是合法的：

- 对此函数的所有调用都C++从进行。

- 函数的定义位于中C++。

## <a name="example"></a>示例

```cpp
// C4190.cpp
// compile with: /W1 /LD
struct X
{
   int i;
   X ();
   virtual ~X ();
};

extern "C" X func ();   // C4190
```
