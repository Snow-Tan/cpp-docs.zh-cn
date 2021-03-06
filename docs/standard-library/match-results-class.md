---
title: match_results 类
ms.date: 09/10/2018
f1_keywords:
- regex/std::match_results
helpviewer_keywords:
- match_results class
ms.assetid: b504fdca-e5dd-429d-9960-6e27c9167fa6
ms.openlocfilehash: 31154a38f8bbcb879fd871f1eb1bf5a4b15af79b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371024"
---
# <a name="match_results-class"></a>match_results 类

包含一系列子匹配项。

## <a name="syntax"></a>语法

```cpp
template <class BidIt, class Alloc>
class match_results
```

## <a name="parameters"></a>参数

*比比*\
子匹配项的迭代器类型。

*Alloc*\
用于管理存储的分配器的类型。

## <a name="remarks"></a>备注

类模板描述一个对象，该对象控制由正则表达式搜索生成的不可修改的类型`sub_match<BidIt>`元素序列。 每个元素指向与该元素对应的捕获组匹配的子序列。

### <a name="constructors"></a>构造函数

|构造函数|说明|
|-|-|
|[match_results](#match_results)|构造对象。|

### <a name="typedefs"></a>Typedef

|类型名称|说明|
|-|-|
|[allocator_type](#allocator_type)|用于管理存储的分配器的类型。|
|[char_type](#char_type)|元素的类型。|
|[const_iterator](#const_iterator)|子匹配项的常量迭代器类型。|
|[const_reference](#const_reference)|元素常量引用的类型。|
|[difference_type](#difference_type)|迭代器差异的类型。|
|[迭 代](#iterator)|子匹配项的迭代器类型。|
|[参考](#reference)|元素引用的类型。|
|[size_type](#size_type)|子匹配项计数的类型。|
|[string_type](#string_type)|字符串的类型。|
|[value_type](#value_type)|子匹配项的类型。|

### <a name="member-functions"></a>成员职能

|成员函数|说明|
|-|-|
|[开始](#begin)|指定子匹配序列的开头。|
|[空](#empty)|测试是否无子匹配项。|
|[结束](#end)|指定子匹配序列的末尾。|
|[格式](#format)|设置子匹配项格式。|
|[get_allocator](#get_allocator)|返回存储的分配器。|
|[length](#length)|返回子匹配项的长度。|
|[max_size](#max_size)|获取子匹配项的最大数目。|
|[位置](#position)|获取子组的起始偏移量。|
|[prefix](#prefix)|获取第一个子匹配项之前的序列。|
|[大小](#size)|计算子匹配项的数目。|
|[Str](#str)|返回子匹配项。|
|[suffix](#suffix)|获取最后一个子匹配项后的序列。|
|[交换](#swap)|交换两个 match_results 对象。|

### <a name="operators"></a>运算符

|操作员|说明|
|-|-|
|[运算符*](#op_eq)|复制 match_results 对象。|
|[算子\[\]](#op_at)|访问子对象。|

## <a name="requirements"></a>要求

**标头：** \<regex 1>

**命名空间:** std

## <a name="example"></a>示例

```cpp
// std__regex__match_results.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
{
    std::regex rx("c(a*)|(b)");
    std::cmatch mr;

    std::regex_search("xcaaay", mr, rx);

    std::cout << "prefix: matched == " << std::boolalpha
        << mr.prefix().matched
        << ", value == " << mr.prefix() << std::endl;
    std::cout << "whole match: " << mr.length() << " chars, value == "
        << mr.str() << std::endl;
    std::cout << "suffix: matched == " << std::boolalpha
        << mr.suffix().matched
        << ", value == " << mr.suffix() << std::endl;
    std::cout << std::endl;

    std::string fmt("\"c(a*)|(b)\" matched \"$&\"\n"
        "\"(a*)\" matched \"$1\"\n"
        "\"(b)\" matched \"$2\"\n");
    std::cout << mr.format(fmt) << std::endl;
    std::cout << std::endl;

    // index through submatches
    for (size_t n = 0; n < mr.size(); ++n)
    {
        std::cout << "submatch[" << n << "]: matched == " << std::boolalpha
            << mr[n].matched <<
            " at position " << mr.position(n) << std::endl;
        std::cout << "  " << mr.length(n)
            << " chars, value == " << mr[n] << std::endl;
    }
    std::cout << std::endl;

    // iterate through submatches
    for (std::cmatch::iterator it = mr.begin(); it != mr.end(); ++it)
    {
        std::cout << "next submatch: matched == " << std::boolalpha
            << it->matched << std::endl;
        std::cout << "  " << it->length()
            << " chars, value == " << *it << std::endl;
    }
    std::cout << std::endl;

    // other members
    std::cout << "empty == " << std::boolalpha << mr.empty() << std::endl;

    std::cmatch::allocator_type al = mr.get_allocator();
    std::cmatch::string_type str = std::string("x");
    std::cmatch::size_type maxsiz = mr.max_size();
    std::cmatch::char_type ch = 'x';
    std::cmatch::difference_type dif = mr.begin() - mr.end();
    std::cmatch::const_iterator cit = mr.begin();
    std::cmatch::value_type val = *cit;
    std::cmatch::const_reference cref = val;
    std::cmatch::reference ref = val;

    maxsiz = maxsiz;  // to quiet "unused" warnings
    if (ref == cref)
        ch = ch;
    dif = dif;

    return (0);
}
```

```Output
prefix: matched == true, value == x
whole match: 4 chars, value == caaa
suffix: matched == true, value == y

"c(a*)|(b)" matched "caaa"
"(a*)" matched "aaa"
"(b)" matched ""

submatch[0]: matched == true at position 1
  4 chars, value == caaa
submatch[1]: matched == true at position 2
  3 chars, value == aaa
submatch[2]: matched == false at position 6
  0 chars, value ==

next submatch: matched == true
  4 chars, value == caaa
next submatch: matched == true
  3 chars, value == aaa
next submatch: matched == false
  0 chars, value ==

empty == false
```

## <a name="match_resultsallocator_type"></a><a name="allocator_type"></a>match_results：：allocator_type

用于管理存储的分配器的类型。

```cpp
typedef Alloc allocator_type;
```

### <a name="remarks"></a>备注

类型def是模板参数*Alloc*的同义词。

## <a name="match_resultsbegin"></a><a name="begin"></a>match_results：开始

指定子匹配序列的开头。

```cpp
const_iterator begin() const;
```

### <a name="remarks"></a>备注

该成员函数返回一个随机访问迭代器，指向序列的第一个元素（或刚超出空序列末尾的位置）。

## <a name="match_resultschar_type"></a><a name="char_type"></a>match_results：char_type

元素的类型。

```cpp
typedef typename iterator_traits<BidIt>::value_type char_type;
```

### <a name="remarks"></a>备注

typedef 是类型 `iterator_traits<BidIt>::value_type`的同义词，后者是被搜索字符序列的元素类型。

## <a name="match_resultsconst_iterator"></a><a name="const_iterator"></a>match_results：const_iterator

子匹配项的常量迭代器类型。

```cpp
typedef T0 const_iterator;
```

### <a name="remarks"></a>备注

该 typedef 描述可用作受控序列的常量随机访问迭代器的对象。

## <a name="match_resultsconst_reference"></a><a name="const_reference"></a>match_results：const_reference

元素常量引用的类型。

```cpp
typedef const typename Alloc::const_reference const_reference;
```

### <a name="remarks"></a>备注

typedef 将可作为常量引用的对象描述为受控序列中的元素。

## <a name="match_resultsdifference_type"></a><a name="difference_type"></a>match_results：:d）类型

迭代器差异的类型。

```cpp
typedef typename iterator_traits<BidIt>::difference_type difference_type;
```

### <a name="remarks"></a>备注

Typedef 是 `iterator_traits<BidIt>::difference_type`类型的同义词，它描述一个对象，该对象表示任何两个指向受控序列元素的迭代器之间的差异。

## <a name="match_resultsempty"></a><a name="empty"></a>match_results：：空

测试是否无子匹配项。

```cpp
bool empty() const;
```

### <a name="remarks"></a>备注

仅当正则表达式搜索失败时，该成员函数才返回 true。

## <a name="match_resultsend"></a><a name="end"></a>match_results：结束

指定子匹配序列的末尾。

```cpp
const_iterator end() const;
```

### <a name="remarks"></a>备注

成员函数返回一个迭代器，该迭代器指向刚刚超出的序列的末尾。

## <a name="match_resultsformat"></a><a name="format"></a>match_results：格式

设置子匹配项格式。

```cpp
template <class OutIt>
OutIt format(OutIt out,
    const string_type& fmt, match_flag_type flags = format_default) const;

string_type format(const string_type& fmt, match_flag_type flags = format_default) const;
```

### <a name="parameters"></a>参数

*出它*\
输出迭代器类型。

*出*\
要写入到的输出流。

*Fmt*\
格式字符串。

*标志*\
格式标志。

### <a name="remarks"></a>备注

每个成员函数在格式*fmt*的控制下生成格式化的文本。 第一个成员函数将格式化的文本写入其参数*定义的*序列*并返回。* 第二个成员函数返回包含格式化文本副本的字符串对象。

生成格式化文本。 格式字符串中的文字文本通常会复制到目标序列。 格式字符串中的每个转义序列均由它表示的文本替换。 复制和替换的详细信息由传递到函数的格式标志控制。

## <a name="match_resultsget_allocator"></a><a name="get_allocator"></a>match_results：get_allocator

返回存储的分配器。

```cpp
allocator_type get_allocator() const;
```

### <a name="remarks"></a>备注

成员函数返回 `*this` 使用的分配器对象的副本以分配其 `sub_match` 对象。

## <a name="match_resultsiterator"></a><a name="iterator"></a>match_results：迭代器

子匹配项的迭代器类型。

```cpp
typedef const_iterator iterator;
```

### <a name="remarks"></a>备注

该类型描述可用作受控序列的随机访问迭代器的对象。

## <a name="match_resultslength"></a><a name="length"></a>match_results：长度

返回子匹配项的长度。

```cpp
difference_type length(size_type sub = 0) const;
```

### <a name="parameters"></a>参数

*子*\
子匹配项的索引。

### <a name="remarks"></a>备注

成员函数返回 `(*this)[sub].length()`。

## <a name="match_resultsmatch_results"></a><a name="match_results"></a>match_results：match_results

构造对象。

```cpp
explicit match_results(const Alloc& alloc = Alloc());

match_results(const match_results& right);
```

### <a name="parameters"></a>参数

*异位*\
要存储的分配器对象。

*对*\
要复制的 match_results 对象。

### <a name="remarks"></a>备注

第一个构造函数构造 `match_results` 对象，其中不包含子匹配项。 第二个构造函数构造一`match_results`个对象，该对象是*右*的副本。

## <a name="match_resultsmax_size"></a><a name="max_size"></a>match_results：：max_size

获取子匹配项的最大数目。

```cpp
size_type max_size() const;
```

### <a name="remarks"></a>备注

该成员函数将返回对象可控制的最长序列的长度。

## <a name="match_resultsoperator"></a><a name="op_eq"></a>match_results：：操作员*

复制 match_results 对象。

```cpp
match_results& operator=(const match_results& right);
```

### <a name="parameters"></a>参数

*对*\
要复制的 match_results 对象。

### <a name="remarks"></a>备注

成员运算符用*右*控制的顺序的副本替换`*this`由 它控制的序列。

## <a name="match_resultsoperator"></a><a name="op_at"></a>match_results：：操作员*

访问子对象。

```cpp
const_reference operator[](size_type n) const;
```

### <a name="parameters"></a>参数

*n*\
子匹配项的索引。

### <a name="remarks"></a>备注

成员函数返回对受控序列的元素*n*的引用，或者返回对空`sub_match`对象的引用，如果`size() <= n`捕获组*n*不是匹配的一部分。

## <a name="match_resultsposition"></a><a name="position"></a>match_results：:p

获取子组的起始偏移量。

```cpp
difference_type position(size_type sub = 0) const;
```

### <a name="parameters"></a>参数

*子*\
子匹配项的索引。

### <a name="remarks"></a>备注

成员函数将返回 `std::distance(prefix().first, (*this)[sub].first)`，即目标序列中的第一个字符到受控序列的 `n` 元素指向的子匹配项中的第一个字符之间的距离。

## <a name="match_resultsprefix"></a><a name="prefix"></a>match_results：:p重新修复

获取第一个子匹配项之前的序列。

```cpp
const_reference prefix() const;
```

### <a name="remarks"></a>备注

成员函数会返回一个对类型 `sub_match<BidIt>` 的对象的引用，它指向始于目标序列开始处并止于 `(*this)[0].first`的字符序列，也即，它指向匹配的子序列之前的文本。

## <a name="match_resultsreference"></a><a name="reference"></a>match_results：参考

元素引用的类型。

```cpp
typedef const_reference reference;
```

### <a name="remarks"></a>备注

该类型是类型 `const_reference`的同义词。

## <a name="match_resultssize"></a><a name="size"></a>match_results：：大小

计算子匹配项的数目。

```cpp
size_type size() const;
```

### <a name="remarks"></a>备注

该成员函数将返回比用于搜索的正则表达式中捕获组大一的数字，或如果为进行搜索则返回 0。

## <a name="match_resultssize_type"></a><a name="size_type"></a>match_results：size_type

子匹配项计数的类型。

```cpp
typedef typename Alloc::size_type size_type;
```

### <a name="remarks"></a>备注

该类型是类型 `Alloc::size_type`的同义词。

## <a name="match_resultsstr"></a><a name="str"></a>match_results：斯特

返回子匹配项。

```cpp
string_type str(size_type sub = 0) const;
```

### <a name="parameters"></a>参数

*子*\
子匹配项的索引。

### <a name="remarks"></a>备注

成员函数返回 `string_type((*this)[sub])`。

## <a name="match_resultsstring_type"></a><a name="string_type"></a>match_results：string_type

字符串的类型。

```cpp
typedef basic_string<char_type> string_type;
```

### <a name="remarks"></a>备注

该类型是类型 `basic_string<char_type>`的同义词。

## <a name="match_resultssuffix"></a><a name="suffix"></a>match_results：后缀

获取最后一个子匹配项后的序列。

```cpp
const_reference suffix() const;
```

### <a name="remarks"></a>备注

该成员函数将返回对指向起始于 `sub_match<BidIt>` 、结束于目标序列（即指向匹配序列之后的文本）的 `(*this)[size() - 1].second` 类型对象的引用。

## <a name="match_resultsswap"></a><a name="swap"></a>match_results：：交换

交换两个 match_results 对象。

```cpp
void swap(const match_results& right) throw();
```

### <a name="parameters"></a>参数

*对*\
要交换的 match_results 对象。

### <a name="remarks"></a>备注

成员函数在恒定时间内交换`*this`和*的权利*的内容，不引发异常。

## <a name="match_resultsvalue_type"></a><a name="value_type"></a>match_results：value_type

子匹配项的类型。

```cpp
typedef sub_match<BidIt> value_type;
```

### <a name="remarks"></a>备注

typedef 是类型 `sub_match<BidIt>`的同义词。

## <a name="see-also"></a>另请参阅

[\<正则>](../standard-library/regex.md)
