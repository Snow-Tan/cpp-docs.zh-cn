---
title: 编译器错误 C2482
ms.date: 09/15/2017
f1_keywords:
- C2482
helpviewer_keywords:
- C2482
ms.assetid: 98c87da2-625c-4cc2-9bf7-78d15921e779
ms.openlocfilehash: 5afa81369b2cf329baae02bc1309587015946409
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205148"
---
# <a name="compiler-error-c2482"></a>编译器错误 C2482

>"*identifier*"：托管/WinRT 代码中不允许使用 "thread" 数据的动态初始化

## <a name="remarks"></a>备注

在托管或 WinRT 代码中，使用[__declspec （thread）](../../cpp/thread.md)存储类修饰符特性或[thread_local](../../cpp/storage-classes-cpp.md#thread_local)存储类说明符声明的变量无法使用需要在运行时计算的表达式进行初始化。 在这些运行时环境中初始化 `__declspec(thread)` 或 `thread_local` 数据需要静态表达式。

## <a name="example"></a>示例

下面的示例在托管（ **/clr**）和 WinRT （ **/ZW**）代码中生成 C2482：

```cpp
// C2482.cpp
// For managed example, compile with: cl /EHsc /c /clr C2482.cpp
// For WinRT example, compile with: cl /EHsc /c /ZW C2482.cpp
#define Thread __declspec( thread )
Thread int tls_i1 = tls_i1;   // C2482

int j = j;   // OK in C++; C error
Thread int tls_i2 = sizeof( tls_i2 );   // Okay in C and C++
```

若要解决此问题，请使用常量、 **constexpr**或静态表达式初始化线程本地存储。 单独执行任何线程特定的初始化。
