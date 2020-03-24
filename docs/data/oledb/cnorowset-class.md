---
title: CNoRowset-Klasse
ms.date: 11/04/2016
f1_keywords:
- ATL.CNoRowset
- ATL::CNoRowset<TAccessor>
- CNoRowset
- ATL.CNoRowset<TAccessor>
- ATL::CNoRowset
helpviewer_keywords:
- CNoRowset class
ms.assetid: 55c6c7a4-9e3a-4775-a2dd-c8b333012fa6
ms.openlocfilehash: 19a1e01fd29c74cf1c44081c24bf384704cf2acd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211471"
---
# <a name="cnorowset-class"></a>CNoRowset-Klasse

Kann als Vorlagen Argument (`TRowset`) für [CCommand](../../data/oledb/ccommand-class.md) [oder zum](../../data/oledb/ctable-class.md)verwenden verwendet werden.

## <a name="syntax"></a>Syntax

```cpp
template <class TAccessor = CAccessorBase>
class CNoRowset
```

### <a name="parameters"></a>Parameter

*TAccessor*<br/>
Eine Accessor-Klasse. Der Standardwert lautet `CAccessorBase`.

## <a name="remarks"></a>Bemerkungen

Verwenden Sie `CNoRowset` als Vorlagen Argument, wenn der Befehl kein Rowset zurückgibt.

`CNoRowset` implementiert die folgenden Stub-Methoden, die jeweils anderen Accessor-Klassen Methoden entsprechen:

- `BindFinished`: zeigt an, wenn die Bindung beendet ist (gibt `S_OK`zurück).

- `Close`: gibt Zeilen und die aktuelle IRowset-Schnittstelle frei.

- `GetIID`: Ruft die Schnittstellen-ID eines Verbindungs Punkts ab.

- `GetInterface`: Ruft eine Schnittstelle ab.

- `GetInterfacePtr`-Ruft einen gekapselten Schnittstellen Zeiger ab.

- `SetAccessor`: legt einen Zeiger auf den-Accessor fest.

- `SetupOptionalRowsetInterfaces`: richtet optionale Schnittstellen für das Rowset ein.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atldbcli.h

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenz der OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-reference.md)
