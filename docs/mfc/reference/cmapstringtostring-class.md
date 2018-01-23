---
title: "CMapStringToString 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMapStringToString
- AFXCOLL/CMapStringToString
- AFXCOLL/CMapStringToString::CPair
- AFXCOLL/CMapStringToOb::CMapStringToOb
- AFXCOLL/CMapStringToOb::GetCount
- AFXCOLL/CMapStringToOb::GetHashTableSize
- AFXCOLL/CMapStringToOb::GetNextAssoc
- AFXCOLL/CMapStringToOb::GetSize
- AFXCOLL/CMapStringToOb::GetStartPosition
- AFXCOLL/CMapStringToOb::HashKey
- AFXCOLL/CMapStringToOb::InitHashTable
- AFXCOLL/CMapStringToOb::IsEmpty
- AFXCOLL/CMapStringToOb::Lookup
- AFXCOLL/CMapStringToOb::LookupKey
- AFXCOLL/CMapStringToString::PGetFirstAssoc
- AFXCOLL/CMapStringToString::PGetNextAssoc
- AFXCOLL/CMapStringToString::PLookup
- AFXCOLL/CMapStringToOb::RemoveAll
- AFXCOLL/CMapStringToOb::RemoveKey
- AFXCOLL/CMapStringToOb::SetAt
dev_langs: C++
helpviewer_keywords:
- CMapStringToString [MFC], CPair
- CMapStringToOb [MFC], CMapStringToOb
- CMapStringToOb [MFC], GetCount
- CMapStringToOb [MFC], GetHashTableSize
- CMapStringToOb [MFC], GetNextAssoc
- CMapStringToOb [MFC], GetSize
- CMapStringToOb [MFC], GetStartPosition
- CMapStringToOb [MFC], HashKey
- CMapStringToOb [MFC], InitHashTable
- CMapStringToOb [MFC], IsEmpty
- CMapStringToOb [MFC], Lookup
- CMapStringToOb [MFC], LookupKey
- CMapStringToString [MFC], PGetFirstAssoc
- CMapStringToString [MFC], PGetNextAssoc
- CMapStringToString [MFC], PLookup
- CMapStringToOb [MFC], RemoveAll
- CMapStringToOb [MFC], RemoveKey
- CMapStringToOb [MFC], SetAt
ms.assetid: b45794c2-fe6b-4edb-a8ca-faa03b57b4a8
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 142a000b5521458e3bdace8f840295efd07209fc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="cmapstringtostring-class"></a>CMapStringToString 类
支持 `CString` 对象键控的 `CString` 对象的映射。  
  
## <a name="syntax"></a>语法  
  
```  
class CMapStringToString : public CObject  
```  
  
## <a name="members"></a>成员  
 成员函数的`CMapStringToString`类似于类的成员函数[CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md)。 由于此相似性，因此你可以使用 `CMapStringToOb` 参考文档获取成员函数细节。 无论您在何处`CObject`指针返回值或"输出"函数参数，如替换指向`char`。 无论您在何处`CObject`指针作为"输入"函数参数，替换指向`char`。  
  
 `BOOL CMapStringToOb::Lookup(const char*<key>, CObject*&<rValue>) const;`  
  
 例如，转换为  
  
 `BOOL CMapStringToString::Lookup(LPCTSTR<key>, CString&<rValue>) const;`  
  
### <a name="public-structures"></a>公共结构  
  
|name|描述|  
|----------|-----------------|  
|[CMapStringToString::CPair](#cpair)|一个包含密钥值和关联的字符串对象的值的嵌套的结构。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CMapStringToOb::CMapStringToOb](../../mfc/reference/cmapstringtoob-class.md#cmapstringtoob)|构造函数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CMapStringToOb::GetCount](../../mfc/reference/cmapstringtoob-class.md#getcount)|在此地图中返回元素的数。|  
|[CMapStringToOb::GetHashTableSize](../../mfc/reference/cmapstringtoob-class.md#gethashtablesize)|确定当前的哈希表中的元素数。|  
|[CMapStringToOb::GetNextAssoc](../../mfc/reference/cmapstringtoob-class.md#getnextassoc)|获取循环的下一个元素。|  
|[CMapStringToOb::GetSize](../../mfc/reference/cmapstringtoob-class.md#getsize)|在此地图中返回元素的数。|  
|[CMapStringToOb::GetStartPosition](../../mfc/reference/cmapstringtoob-class.md#getstartposition)|返回的第一个元素的位置。|  
|[CMapStringToOb::HashKey](../../mfc/reference/cmapstringtoob-class.md#hashkey)|计算指定的键的哈希值。|  
|[CMapStringToOb::InitHashTable](../../mfc/reference/cmapstringtoob-class.md#inithashtable)|初始化哈希表。|  
|[CMapStringToOb::IsEmpty](../../mfc/reference/cmapstringtoob-class.md#isempty)|空映射条件 （没有元素） 的测试。|  
|[CMapStringToOb::Lookup](../../mfc/reference/cmapstringtoob-class.md#lookup)|查找基于 void 指针密钥的 void 指针。 指针值，它指向不实体用于键的比较。|  
|[CMapStringToOb::LookupKey](../../mfc/reference/cmapstringtoob-class.md#lookupkey)|返回与指定的密钥值关联的密钥的引用。|  
|[CMapStringToString::PGetFirstAssoc](#pgetfirstassoc)|获取一个指针指向第一个`CString`映射中。|  
|[CMapStringToString::PGetNextAssoc](#pgetnextassoc)|获取一个指针指向下一步`CString`来循环。|  
|[CMapStringToString::PLookup](#plookup)|返回一个指向`CString`其值与指定的值匹配。|  
|[CMapStringToOb::RemoveAll](../../mfc/reference/cmapstringtoob-class.md#removeall)|从此映射中移除所有元素。|  
|[CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey)|移除由键指定的元素。|  
|[CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat)|将元素插入到映射;如果找到匹配的键，将替换现有元素。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|描述|  
|----------|-----------------|  
|[CMapStringToOb::operator]](../../mfc/reference/cmapstringtoob-class.md#operator_at)|将元素插入到映射 — 运算符替换`SetAt`。|  
  
## <a name="remarks"></a>备注  
 `CMapStringToString` 包括用于支持其元素序列化和转储的 `IMPLEMENT_SERIAL` 宏。 如果映射存储到存档中，使用重载插入反过来序列的每个元素 (  **<<** ) 运算符或`Serialize`成员函数。  
  
 如果你需要个人的转储`CString` -  `CString`元素，必须将转储上下文的深度设置为 1 或更高版本。  
  
 当`CMapStringToString`对象被删除，或删除其元素时，`CString`中删除相应的对象。  
  
 有关详细信息`CMapStringToString`，请参阅文章[集合](../../mfc/collections.md)。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMapStringToString`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxcoll.h  
  
##  <a name="cpair"></a>CMapStringToString::CPair  
 包含一个密钥值和关联的字符串对象的值。  
  
### <a name="remarks"></a>备注  
 这是在类中的嵌套的结构[CMapStringToString](../../mfc/reference/cmapstringtostring-class.md)。  
  
 结构组成两个字段：  
  
- **密钥**与键类型的实际值。  
  
- **值**关联的对象的值。  
  
 它用于存储中的返回值[CMapStringToString::PLookup](#plookup)， [CMapStringToString::PGetFirstAssoc](#pgetfirstassoc)，和[CMapStringToString::PGetNextAssoc](#pgetnextassoc)。  
  
### <a name="example"></a>示例  
  有关用法的一个示例，请参阅示例[CMapStringToString::PLookup](#plookup)。  
  
##  <a name="pgetfirstassoc"></a>CMapStringToString::PGetFirstAssoc  
 返回 map 对象的第一个条目。  
  
```  
const CPair* PGetFirstAssoc() const;

CPair* PGetFirstAssoc();
```  
  
### <a name="return-value"></a>返回值  
 指向映射; 中的第一个条目请参阅[CMapStringToString::CPair](#cpair)。 如果映射为空，则值是`NULL`。  
  
### <a name="remarks"></a>备注  
 调用此函数可返回 map 对象中的第一个元素的指针。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections#73](../../mfc/codesnippet/cpp/cmapstringtostring-class_1.cpp)]  
  
##  <a name="pgetnextassoc"></a>CMapStringToString::PGetNextAssoc  
 检索指向的地图元素`pAssocRec`。  
  
```  
const CPair *PGetNextAssoc(const CPair* pAssoc) const;  
  
CPair *PGetNextAssoc(const CPair* pAssoc);
```  
  
### <a name="parameters"></a>参数  
 *pAssoc*  
 指向先前返回一个映射条目[PGetNextAssoc](#pgetnextassoc)或[PGetFirstAssoc](#pgetfirstassoc)调用。  
  
### <a name="return-value"></a>返回值  
 指向映射; 中的下一个条目请参阅[CMapStringToString::CPair](#cpair)。 如果该元素为地图中的最后一个，则值是**NULL**。  
  
### <a name="remarks"></a>备注  
 调用此方法以循环访问映射中的所有元素。 检索通过调用的第一个元素`PGetFirstAssoc`，然后循环访问映射到的连续调用`PGetNextAssoc`。  
  
### <a name="example"></a>示例  
  请参阅示例[CMapStringToString::PGetFirstAssoc](#pgetfirstassoc)。  
  
##  <a name="plookup"></a>CMapStringToString::PLookup  
 查找映射到给定键的值。  
  
```  
const CPair* PLookup(LPCTSTR key) const;

CPair* PLookup(LPCTSTR key);
```  
  
### <a name="parameters"></a>参数  
 `key`  
 指向要搜索元素的键的指针。  
  
### <a name="return-value"></a>返回值  
 指定的键指向的指针。  
  
### <a name="remarks"></a>备注  
 调用此方法可搜索的地图元素与给定的键完全匹配的密钥。  
  
### <a name="example"></a>示例  
 [!code-cpp[NVC_MFCCollections#74](../../mfc/codesnippet/cpp/cmapstringtostring-class_2.cpp)]  
  
## <a name="see-also"></a>请参阅  
 [MFC 示例收集](../../visual-cpp-samples.md)   
 [CObject 类](../../mfc/reference/cobject-class.md)   
 [层次结构图](../../mfc/hierarchy-chart.md)


