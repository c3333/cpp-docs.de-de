---
title: Verwenden von Textmarken
ms.date: 10/24/2018
helpviewer_keywords:
- rowsets, bookmarks
- OLE DB provider templates, bookmarks
- bookmarks, OLE DB
- OLE DB providers, bookmark support
ms.assetid: 7fa1d1a8-5063-4aa9-93ee-815bb9c98fae
ms.openlocfilehash: 5a4a2d65ba7367b5568603b5f08a07c6d85cc4a5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209312"
---
# <a name="using-bookmarks"></a>Verwenden von Textmarken

Vor dem Öffnen des Rowsets müssen Sie dem Anbieter mitteilen, dass Sie Lesezeichen verwenden möchten. Legen Sie hierzu die `DBPROP_BOOKMARKS`-Eigenschaft in Ihrem Eigenschaften Satz auf **true** fest. Der Anbieter ruft Lesezeichen als Spalte NULL ab, sodass Sie das spezielle Makro BOOKMARK_ENTRY und die `CBookmark` Klasse verwenden müssen, wenn Sie einen statischen Accessor verwenden. `CBookmark` ist eine Vorlagen Klasse, in der das-Argument die Länge des Lesezeichen Puffers in Bytes ist. Die Länge des für ein Lesezeichen erforderlichen Puffers hängt vom Anbieter ab. Wenn Sie den ODBC-OLE DB Anbieter verwenden, wie im folgenden Beispiel gezeigt, muss der Puffer 4 Bytes groß sein.

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

Wenn Sie `CDynamicAccessor`verwenden, wird der Puffer dynamisch zur Laufzeit festgelegt. In diesem Fall können Sie eine spezialisierte Version von `CBookmark` verwenden, für die Sie keine Pufferlänge angeben. Verwenden Sie die Funktion `GetBookmark`, um das Lesezeichen aus dem aktuellen Datensatz abzurufen, wie im folgenden Codebeispiel gezeigt:

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

[Verwenden von Zugriffsmethoden](../../data/oledb/using-accessors.md)
