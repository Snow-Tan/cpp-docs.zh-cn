---
title: allocate
ms.date: 11/04/2016
f1_keywords:
- allocate_cpp
helpviewer_keywords:
- __declspec keyword [C++], allocate
- allocate __declspec keyword
ms.assetid: 67828b31-de60-4c0e-b0a6-ef3aab22641d
ms.openlocfilehash: 6d9429aa7c079f0f99a936019e5945092dc1f006
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181520"
---
# <a name="allocate"></a>allocate

**Microsoft 专用**

**分配**声明说明符命名要在其中分配数据项的数据段。

## <a name="syntax"></a>语法

```
   __declspec(allocate("segname")) declarator
```

## <a name="remarks"></a>备注

必须使用以下杂注之一声明名称*segname* ：

- [code_seg](../preprocessor/code-seg.md)

- [const_seg](../preprocessor/const-seg.md)

- [data_seg](../preprocessor/data-seg.md)

- [init_seg](../preprocessor/init-seg.md)

- [部分](../preprocessor/section.md)

## <a name="example"></a>示例

```cpp
// allocate.cpp
#pragma section("mycode", read)
__declspec(allocate("mycode"))  int i = 0;

int main() {
}
```

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[__declspec](../cpp/declspec.md)<br/>
[关键字](../cpp/keywords-cpp.md)
