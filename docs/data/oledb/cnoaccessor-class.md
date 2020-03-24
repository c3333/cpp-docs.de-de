---
title: CNoAccessor-Klasse
ms.date: 11/04/2016
f1_keywords:
- ATL::CNoAccessor
- CNoAccessor
- ATL.CNoAccessor
helpviewer_keywords:
- CNoAccessor class
ms.assetid: eb669ae5-0a56-49a3-9646-c4ae6239da31
ms.openlocfilehash: c82d756690c6c2a719cb03f458c471aa44e3d5b5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211730"
---
# <a name="cnoaccessor-class"></a>CNoAccessor-Klasse

Kann als Vorlagen Argument (`TAccessor`) für Vorlagen Klassen verwendet werden, z. b. `CCommand` und `CTable`, die ein Accessor-Klassen Argument erfordern.

## <a name="syntax"></a>Syntax

```cpp
class CNoAccessor
```

## <a name="remarks"></a>Bemerkungen

Verwenden Sie `CNoAccessor` als Vorlagen Argument, wenn Sie nicht möchten, dass die Klasse Parameter oder Ausgabespalten unterstützt.

`CNoAccessor` implementiert die folgenden Stub-Methoden, die jeweils anderen Accessor-Klassen Methoden entsprechen:

- `BindColumns` bindet Spalten an Accessoren.

- `BindParameters`: bindet die erstellten Parameter an Spalten.

- `Bind`: erstellt Bindungen.

- `Close`: schließt den Accessor.

- `ReleaseAccessors`: gibt die von der-Klasse erstellten Accessoren frei.

- `FreeRecordMemory`: gibt alle Spalten im aktuellen Datensatz frei, die freigegeben werden müssen.

- `GetColumnInfo`: ruft Spalten Informationen aus dem geöffneten Rowset ab.

- `GetNumAccessors`: Ruft die Anzahl der Accessoren ab, die von der-Klasse erstellt wurden.

- `IsAutoAccessor`: gibt true zurück, wenn Daten während eines Verschiebungs Vorgangs automatisch für den Accessor abgerufen werden.

- `GetHAccessor`: Ruft das Accessorhandle eines angegebenen Accessors ab.

- `GetBuffer`: Ruft den Zeiger auf den Lesezeichen Puffer ab.

- `NoBindOnNullRowset`: verhindert die Datenbindung für leere Rowsets.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atldbcli.h

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenz der OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-reference.md)
