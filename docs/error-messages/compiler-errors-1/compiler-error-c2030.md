---
title: 编译器错误 C2030
ms.date: 11/04/2016
f1_keywords:
- C2030
helpviewer_keywords:
- C2030
ms.assetid: 5806cead-64df-4eff-92de-52c9a3f5ee62
ms.openlocfilehash: e3f3936e6fd37da16c923cb482f45cec11833b3c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208027"
---
# <a name="compiler-error-c2030"></a>编译器错误 C2030

具有“protected private”可访问性的析构函数不能是声明为“sealed”的类的成员

声明为 `sealed` 的 Windows 运行时类不能具有受保护的私有析构函数。 已密封的类型上只允许使用公共虚拟和私有非虚拟析构函数。 有关详细信息，请参阅 [ref class 和 ref struct](../../cppcx/ref-classes-and-structs-c-cx.md)。

若要修复此错误，请更改析构函数的可访问性。
