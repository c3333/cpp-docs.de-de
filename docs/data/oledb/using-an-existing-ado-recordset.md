---
title: Verwenden eines vorhandenen ADO-Recordsets
ms.date: 11/04/2016
helpviewer_keywords:
- ADO recordsets [C++]
- OLE DB consumer templates, ADO recordsets
- recordsets [C++], using in OLE DB
ms.assetid: a9b1de8a-d379-49b1-a26e-578741e9f6a8
ms.openlocfilehash: 48f6eb3bac34b37f495b9492e19b4197ed69cca3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209351"
---
# <a name="using-an-existing-ado-recordset"></a>Verwenden eines vorhandenen ADO-Recordsets

Um OLE DB Consumervorlagen und Active Data Objects (ADO) zu mischen, verwenden Sie ADO zum Öffnen eines Recordsets (entsprechend einem Rowset in den OLE DB Consumervorlagen). Wenn Sie ein Recordset haben, führen Sie die folgenden Schritte aus, um eine Verbindung mit einem OLE DB-Rowset herzustellen:

1. Ruft `QueryInterface` für die `IRowset` und `IAccessor` Zeiger auf.

    ```cpp
    IRowset* lpRowset = NULL;
    IAccessor* lpAccessor = NULL;
    lpUnk->QueryInterface(IID_IRowset, (void**)&lpRowset);
    lpUnk->QueryInterface(IID_IAccessor, (void**)&lpAccessor);
    ```

    > [!NOTE]
    > *lpUnk* verweist auf das `IUnknown` Objekt des ADO-Recordsets.

1. Fügen Sie den Accessor und das Rowset an die entsprechenden OLE DB Consumervorlagen Klassen an.

    ```cpp
    CRowset rs;
    CAccessor accessor;

    accessor.AddAccessorInfo(0ul);      // 0 is the ordinal of an ADO accessor
    rs.m_spRowset.Attach(lpRowset);      // use the Attach method of CComPtr<>
    rs.SetAccessor(accessor);
    ```

## <a name="see-also"></a>Weitere Informationen

[Verwenden von Zugriffsmethoden](../../data/oledb/using-accessors.md)
