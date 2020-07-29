---
title: Verwenden von Textmarken
ms.date: 10/24/2018
helpviewer_keywords:
- rowsets, bookmarks
- OLE DB provider templates, bookmarks
- bookmarks, OLE DB
- OLE DB providers, bookmark support
ms.assetid: 7fa1d1a8-5063-4aa9-93ee-815bb9c98fae
ms.openlocfilehash: 8caa33b3bafbaa9e537d9669aa7b60a9355475ef
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218298"
---
# <a name="using-bookmarks"></a>Verwenden von Textmarken

Vor dem Öffnen des Rowsets müssen Sie dem Anbieter mitteilen, dass Sie Lesezeichen verwenden möchten. Legen Sie hierzu die- `DBPROP_BOOKMARKS` Eigenschaft **`true`** in Ihrem Eigenschaften Satz auf fest. Der Anbieter ruft Lesezeichen als Spalte NULL ab, sodass Sie das spezielle Makro BOOKMARK_ENTRY und die-Klasse verwenden müssen, `CBookmark` Wenn Sie einen statischen Accessor verwenden. `CBookmark`ist eine Vorlagen Klasse, bei der das-Argument die Länge des Lesezeichen Puffers in Bytes ist. Die Länge des für ein Lesezeichen erforderlichen Puffers hängt vom Anbieter ab. Wenn Sie den ODBC-OLE DB Anbieter verwenden, wie im folgenden Beispiel gezeigt, muss der Puffer 4 Bytes groß sein.

```cpp
class CProducts
{
public:
   CBookmark<4> bookmark;

   BEGIN_COLUMN_MAP(CProducts)
      BOOKMARK_ENTRY(bookmark)
   END_COLUMN_MAP()
};
```

Anschließend wird der folgende Code verwendet:

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);
propset.AddProperty(DBPROP_BOOKMARKS, true);

CTable<CAccessor<CProducts>> product;
CSession session;
product.Open(session, "Products", &propset);
```

Wenn Sie verwenden `CDynamicAccessor` , wird der Puffer dynamisch zur Laufzeit festgelegt. In diesem Fall können Sie eine spezialisierte Version von verwenden, `CBookmark` für die Sie keine Pufferlänge angeben. Verwenden Sie die-Funktion `GetBookmark` , um das Lesezeichen aus dem aktuellen Datensatz abzurufen, wie in diesem Codebeispiel gezeigt:

```cpp
CTable<CDynamicAccessor> product;
CBookmark<> bookmark;
CDBPropSet propset(DBPROPSET_ROWSET);
CSession session;

propset.AddProperty(DBPROP_BOOKMARKS, true);
product.Open(session, "Products", &propset);
product.MoveNext();
product.GetBookmark(&bookmark);
```

Informationen zur Unterstützung von Lesezeichen in Anbietern finden Sie unter [Anbieter Unterstützung für Lesezeichen](../../data/oledb/provider-support-for-bookmarks.md).

## <a name="see-also"></a>Weitere Informationen

[Verwenden von Accessoren](../../data/oledb/using-accessors.md)
