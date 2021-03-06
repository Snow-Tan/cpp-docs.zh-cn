---
title: rdx （C++ COM 特性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.rdx
helpviewer_keywords:
- rdx attribute
ms.assetid: ff8e4312-c1ad-4934-bdaa-86f54409651e
ms.openlocfilehash: f0140b759b1d78eb1284213a0dc47d9600b2a83b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214625"
---
# <a name="rdx"></a>rdx

创建注册表项或修改现有注册表项。

## <a name="syntax"></a>语法

```cpp
[ rdx(key, valuename=NULL, regtype) ]
```

### <a name="parameters"></a>parameters

*键*<br/>
要创建或打开的项的名称。

*valuename*<br/>
可有可无指定要设置的值字段。 如果密钥中不存在具有此名称的值字段，则会将其添加。

*regtype*<br/>
要添加的注册表项的类型。 可以是下列项之一： `text`、`dword`、`binary`或 `CString`。

## <a name="remarks"></a>备注

**Rdx** C++属性创建或修改 COM 组件的现有注册表项。 特性将 BEGIN_RDX_MAP 宏添加到实现目标成员的对象。 `RegistryDataExchange`，作为 BEGIN_RDX_MAP 宏的结果注入的函数可用于在注册表和数据成员之间传输数据

此属性可与[coclass](coclass.md)、 [progid](progid.md)或[vi_progid](vi-progid.md)特性或其他隐含其中一项的特性结合使用。

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|**类**或**结构**成员|
|**可重复**|否|
|**必需的特性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="example"></a>示例

下面的代码将名为 MyValue 的注册表项添加到描述 CMyClass COM 组件的系统。

```cpp
// cpp_attr_ref_rdx.cpp
// compile with: /LD /link /OPT:NOREF
#define _ATL_ATTRIBUTES
#include "atlbase.h"

[module (name="MyLib")];

class CMyClass {
public:
   CMyClass() {
      strcpy_s(m_sz, "SomeValue");
   }

   [ rdx(key = "HKCR\\MyApp.MyApp.1", valuename = "MyValue", regtype = "text")]
   char m_sz[256];
};
```

## <a name="see-also"></a>另请参阅

[COM 特性](com-attributes.md)<br/>
[registration_script](registration-script.md)
