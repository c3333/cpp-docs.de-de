---
title: CColumnAccessor-Klasse
ms.date: 11/04/2016
f1_keywords:
- CColumnAccessor
- ATL::CColumnAccessor
- ATL.CColumnAccessor
helpviewer_keywords:
- CColumnAccessor class
ms.assetid: 6ce1e67f-6a20-490d-9326-c168b43eee7e
ms.openlocfilehash: 2a3b1dac51a8300a915a7177c36f15512b583fa0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212109"
---
# <a name="ccolumnaccessor-class"></a>CColumnAccessor-Klasse

Generiert injizierten Consumer-Code.

## <a name="syntax"></a>Syntax

```cpp
class CColumnAccessor : public CAccessorBase
```

## <a name="remarks"></a>Bemerkungen

Im injizierten Code ist jede Spalte als separater Accessor gebunden. Sie sollten sich bewusst sein, dass diese Klasse im eingefügten Code verwendet wird (z. b. beim Debuggen), aber Sie müssen Sie in der Regel niemals direkt verwenden.

`CColumnAccessor` implementiert die folgenden Stub-Methoden, von denen jede Funktionalität anderen Methoden der Accessorklasse entspricht:

- `CColumnAccessor` den Konstruktor ein. instanziiert und initialisiert das `CColumnAccessor`-Objekt.

- `CreateAccessor` weist Speicher für die Spalten Bindungs Strukturen zu und initialisiert die Spalten Datenmember.

- `BindColumns` bindet Spalten an Accessoren.

- `SetParameterBuffer` ordnet Puffer für Parameter zu.

- `AddParameter` fügt den Parameter Eintrags Strukturen einen Parameter Eintrag hinzu.

- `HasOutputColumns` bestimmt, ob der Accessor über Ausgabespalten verfügt.

- `HasParameters` bestimmt, ob der Accessor über Parameter verfügt.

- `BindParameters` bindet die erstellten Parameter an Spalten.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atldbcli.h

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenz der OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-reference.md)
