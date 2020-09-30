---
title: Verweisen auf eine Eigenschaft im Anbieter
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB providers, properties
- references, to properties in providers
- referencing properties in providers
ms.assetid: bfbb3851-5eed-467a-a179-4a97a9515525
ms.openlocfilehash: ecb11c54d4c5926fbead0196c441ec23e8b0891f
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509521"
---
# <a name="referencing-a-property-in-your-provider"></a>Verweisen auf eine Eigenschaft im Anbieter

Suchen Sie die Eigenschaften Gruppe und die Eigenschaften-ID für die gewünschte Eigenschaft. Weitere Informationen finden Sie unter [OLE DB Eigenschaften](/previous-versions/windows/desktop/ms722734(v=vs.85)) in der **OLE DB Programmierer-Referenz**.

Im folgenden Beispiel wird davon ausgegangen, dass Sie versuchen, eine Eigenschaft aus dem Rowset zu erhalten. Der Code für die Verwendung der Sitzung oder des Befehls ist ähnlich, verwendet aber eine andere Schnittstelle.

Erstellen Sie ein [CDBPropSet](../../data/oledb/cdbpropset-class.md) -Objekt, indem Sie die Eigenschaften Gruppe als Parameter für den Konstruktor verwenden. Beispiel:

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);
```

Wenden Sie [AddProperty](./cdbpropset-class.md#addproperty)an, und übergeben Sie dabei die eigen schafts-ID und einen Wert, der der Eigenschaft zugewiesen werden soll. Der Typ des Werts hängt von der Eigenschaft ab, die Sie verwenden.

```cpp
CDBPropSet propset(DBPROPSET_ROWSET);

propset.AddProperty(DBPROP_IRowsetChange, true);

propset.AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_INSERT | DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_DELETE);
```

Verwenden Sie die- `IRowset` Schnittstelle zum aufzurufen `GetProperties` . Übergeben Sie den Eigenschaften Satz als Parameter. Dies ist der abschließende Code:

```cpp
CAgentRowset<CCustomCommand>* pRowset = (CAgentRowset<CCustomCommand>*) pThis;

CComQIPtr<IRowsetInfo, &IID_IRowsetInfo> spRowsetProps = pRowset;

DBPROPIDSET set;
set.AddPropertyID(DBPROP_BOOKMARKS);

DBPROPSET* pPropSet = NULL;
ULONG ulPropSet = 0;

HRESULT hr;

if (spRowsetProps)
   hr = spRowsetProps->GetProperties(1, &set, &ulPropSet, &pPropSet);

if (pPropSet)
{
   CComVariant var = pPropSet->rgProperties[0].vValue;
   CoTaskMemFree(pPropSet->rgProperties);
   CoTaskMemFree(pPropSet);

   if (SUCCEEDED(hr) && (var.boolVal == VARIANT_TRUE))
   {
      ...  // Use property here
   }
}
```

## <a name="see-also"></a>Weitere Informationen

[Arbeiten mit OLE DB Anbieter Vorlagen](../../data/oledb/working-with-ole-db-provider-templates.md)
