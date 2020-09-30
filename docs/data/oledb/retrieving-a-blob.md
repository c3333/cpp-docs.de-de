---
title: Abrufen eines BLOBs
ms.date: 10/24/2018
helpviewer_keywords:
- retrieving BLOBs
- BLOB (binary large object), retrieving
- OLE DB, BLOBs (binary large objects)
ms.assetid: 2893eb0a-5c05-4016-8914-1e40ccbaf0b3
ms.openlocfilehash: 352841595e8b197407ccb52a22c8b0502d314c98
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509513"
---
# <a name="retrieving-a-blob"></a>Abrufen eines BLOBs

Sie können eine Binary Large Object (BLOB) auf unterschiedliche Weise abrufen. Sie können verwenden `DBTYPE_BYTES` , um das BLOB als Sequenz von Bytes abzurufen oder eine Schnittstelle wie zu verwenden `ISequentialStream` . Weitere Informationen finden Sie unter [BLOB-und OLE-Objekte](/previous-versions/windows/desktop/ms711511(v=vs.85)) in der **OLE DB Programmierer-Referenz**.

Der folgende Code zeigt, wie ein BLOB mithilfe von abgerufen wird `ISequentialStream` . Mit dem-Makro [BLOB_ENTRY](./macros-and-global-functions-for-ole-db-consumer-templates.md#blob_entry) können Sie die-Schnittstelle und die für die-Schnittstelle verwendeten Flags angeben. Nach dem Öffnen der Tabelle ruft der Code `Read` wiederholt auf, `ISequentialStream` um Bytes aus dem BLOB zu lesen. Der Code ruft `Release` auf, um den Schnittstellen Zeiger zu verwerfen, bevor aufgerufen wird `MoveNext` , um den nächsten Datensatz abzurufen.

```cpp
class CCategories
{
public:
   ISequentialStream* pPicture;

BEGIN_COLUMN_MAP(CCategories)
   BLOB_ENTRY(4, IID_ISequentialStream, STGM_READ, pPicture)
END_COLUMN_MAP()
};
```

Anschließend wird der folgende Code verwendet:

```cpp
CTable<CAccessor<CCategories>> categories;
ULONG cb;
BYTE myBuffer[65536];

categories.Open(session, "Categories");

while (categories.MoveNext() == S_OK)
{
   do
   {
      categories.pPicture->Read(myBuffer, 65536, &cb);
      // Do something with the buffer
   } while (cb > 0);
   categories.pPicture->Release();
}
```

Weitere Informationen zu Makros, die BLOB-Daten verarbeiten, finden Sie Unterspalten Zuordnungs **Makros** in [Makros und globalen Funktionen für OLE DB Consumervorlagen](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md).

## <a name="see-also"></a>Weitere Informationen

[Verwenden von Accessoren](../../data/oledb/using-accessors.md)<br/>
[Makros und globale Funktionen für OLE DB Consumervorlagen](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)<br/>
