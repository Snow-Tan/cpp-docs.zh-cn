---
title: support_error_info （C++ COM 特性）
ms.date: 10/02/2018
f1_keywords:
- vc-attr.support_error_info
helpviewer_keywords:
- support_error_info attribute
ms.assetid: 20a2b55c-4738-4b35-a71d-e5e9c3a7e3bc
ms.openlocfilehash: e61ef2efbdc4039f496d7ffbcccc37cc8d111935
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80166141"
---
# <a name="support_error_info"></a>support_error_info

实现针对返回详细错误的支持。

## <a name="syntax"></a>语法

```cpp
[ support_error_info(error_interface=uuid) ]
```

### <a name="parameters"></a>parameters

*error_interface*<br/>
实现 `IErrorInfo`的接口的标识符。

## <a name="remarks"></a>备注

**support_error_info** C++ 属性实现针对将目标对象遇到的详细上下文错误返回到客户端的支持。 为了使对象支持错误，`IErrorInfo` 接口的方法必须由对象实现。 有关详细信息，请参阅 [支持 IDispatch 和 IErrorInfo](../../atl/supporting-idispatch-and-ierrorinfo.md)。

此属性将 [ISupportErrorInfoImpl](../../atl/reference/isupporterrorinfoimpl-class.md) 类作为基类添加到目标对象。 这会导致 `ISupportErrorInfo` 的默认实现，并且可在单个接口在对象上生成错误时使用。

## <a name="example"></a>示例

下面的代码将 `ISupportErrorInfo` 接口的默认支持添加到 `CMyClass` 对象。

```cpp
// cpp_attr_ref_support_error_info.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name="mymod")];
[object, uuid("f0b17d66-dc6e-4662-baaf-76758e09c878")]
__interface IMyErrors
{
};

[ coclass, support_error_info("IMyErrors"),
  uuid("854dd392-bdc7-4781-8667-8757936f2a4f") ]
class CMyClass
{
};
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用对象**|class|
|**可重复**|是|
|**必需的特性**|无|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>另请参阅

[COM 特性](com-attributes.md)<br/>
[类特性](class-attributes.md)
