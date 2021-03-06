---
title: 初始化和清理文档和视图
ms.date: 11/04/2016
helpviewer_keywords:
- initializing documents [MFC]
- views [MFC], cleaning up
- documents [MFC], initializing
- documents [MFC], cleaning up
- views [MFC], initializing
- initializing objects [MFC], document objects
- document objects [MFC], life cycle of
- initializing views [MFC]
ms.assetid: 95d6f09b-a047-4079-856a-ae7d0548e9d2
ms.openlocfilehash: c5beed5618d4fa991160ad1688a5a686aeaa842f
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626371"
---
# <a name="initializing-and-cleaning-up-documents-and-views"></a>初始化和清理文档和视图

在对文档和视图执行以下操作后，使用下列准则进行初始化和清理：

- MFC 框架初始化文档和视图；您初始化添加到文档和视图中的所有数据。

- 框架在文档和视图关闭时进行清理；您必须从这些文档和视图的成员函数中释放在堆上分配的所有内存。

> [!NOTE]
> 请记住，在对类的[InitInstance](reference/cwinapp-class.md#initinstance)成员函数的重写中，最好是整个应用程序的初始化 `CWinApp` ，因此最好在 `CWinApp` 成员函数[ExitInstance](reference/cwinapp-class.md#exitinstance)的重写中完成整个应用程序的清理。

MDI 应用程序中的文档的生命周期（及其框架窗口和视图）如下所示：

1. 在动态创建期间，调用文档构造函数。

1. 对于每个新文档，将调用文档的[OnNewDocument](reference/cdocument-class.md#onnewdocument)或[OnOpenDocument](reference/cdocument-class.md#onopendocument) 。

1. 用户在文档的整个生存期内与之交互。 通常，当用户通过视图使用文档数据（选择并编辑数据）时会发生此情况。 视图将更改传递给文档以供存储并会更新其他视图。 在此期间，文档和视图都可能处理命令。

1. 框架调用[DeleteContents](reference/cdocument-class.md#deletecontents)来删除特定于文档的数据。

1. 调用文档的析构函数。

在 SDI 应用程序中，当第一次创建文档时，执行步骤 1 一次。 然后，每次打开新文档时，重复执行步骤 2 到步骤 4。 新文档将重用现有的文档对象。 最后，当应用程序结束时执行步骤 5。

## <a name="what-do-you-want-to-know-more-about"></a>要了解有关的详细信息

- [初始化文档和视图](initializing-documents-and-views.md)

- [清理文档和视图](cleaning-up-documents-and-views.md)

## <a name="see-also"></a>另请参阅

[文档/视图体系结构](document-view-architecture.md)
