---
title: CCustomRowset (CustomRS.H)
ms.date: 10/22/2018
f1_keywords:
- cmyproviderrowset
- ccustomrowset
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderRowset class in MyProviderRS.H
- CCustomRowset class in CustomRS.H
ms.assetid: 7ba1a124-3842-40eb-a36b-302190a1af3a
ms.openlocfilehash: 8e90db287bc7ac8994914766045eb210446dfd48
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079781"
---
# <a name="ccustomrowset-customrsh"></a>CCustomRowset (CustomRS.H)

Der Assistent generiert einen Eintrag für das Rowsetobjekt. In diesem Fall wird es als `CCustomRowset`bezeichnet. Die `CCustomRowset`-Klasse erbt von einer OLE DB Anbieter Klasse mit dem Namen `CRowsetImpl`, die alle erforderlichen Schnittstellen für das Rowsetobjekt implementiert. Der folgende Code zeigt die Vererbungs Kette für `CRowsetImpl`:

```cpp
template <class T, class Storage, class CreatorClass,
   class ArrayType = CAtlArray<Storage>>
class CMyRowsetImpl:
   public CRowsetImpl<T, Storage, CreatorClass, ArrayType,
      CSimpleRow, IRowsetLocateImpl< T >>
```

`CRowsetImpl` verwendet auch die `IAccessor` und `IColumnsInfo` Schnittstellen. Diese Schnittstellen werden für Ausgabefelder in Tabellen verwendet. Die-Klasse stellt außerdem eine Implementierung für `IRowsetIdentity`bereit, die es dem Consumer ermöglicht, zu bestimmen, ob zwei Zeilen identisch sind. Die `IRowsetInfo`-Schnittstelle implementiert Eigenschaften für das Rowsetobjekt. Mit der `IConvertType`-Schnittstelle kann der Anbieter Unterschiede zwischen den vom Consumer angeforderten Datentypen und den vom Anbieter verwendeten Datentypen auflösen.

Die `IRowset`-Schnittstelle übernimmt tatsächlich das Abrufen von Daten. Der Consumer ruft zunächst eine Methode namens `GetNextRows` auf, um ein Handle für eine Zeile zurückzugeben, die als `HROW`bezeichnet wird. Der Consumer ruft dann `IRowset::GetData` mit diesem `HROW` auf, um die angeforderten Daten abzurufen.

`CRowsetImpl` erfordert auch mehrere Vorlagen Parameter. Mithilfe dieser Parameter können Sie bestimmen, wie die `CRowsetImpl` Klasse Daten behandelt. Mit dem `ArrayType`-Argument können Sie ermitteln, welche Speicher Mechanismen zum Speichern der Zeilendaten verwendet werden. Der *RowClass* -Parameter gibt an, welche Klasse eine `HROW`enthält.

Der *RowsetInterface* -Parameter ermöglicht es Ihnen, auch die `IRowsetLocate` oder `IRowsetScroll`-Schnittstelle zu verwenden. Die `IRowsetLocate`-und `IRowsetScroll` Schnittstellen erben beide von `IRowset`. Daher müssen die OLE DB Anbieter Vorlagen eine spezielle Behandlung für diese Schnittstellen bereitstellen. Wenn Sie eine dieser Schnittstellen verwenden möchten, müssen Sie diesen Parameter verwenden.

## <a name="see-also"></a>Weitere Informationen

[Vom Anbieter-Assistenten generierte Dateien](../../data/oledb/provider-wizard-generated-files.md)<br/>
