---
title: CAccessor-Klasse
ms.date: 11/04/2016
f1_keywords:
- ATL.CAccessor<T>
- ATL::CAccessor
- CAccessor
- ATL::CAccessor<T>
- ATL.CAccessor
helpviewer_keywords:
- CAccessor class
ms.assetid: b2ba959f-a686-46f3-8837-176248aef748
ms.openlocfilehash: 032274d7dc85aa823cd28cf61e4606903f13ad9e
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509565"
---
# <a name="caccessor-class"></a>CAccessor-Klasse

Stellt einen der Accessortypen dar.

## <a name="syntax"></a>Syntax

```cpp
template <class T>
class CAccessor : public CAccessorBase, public T
```

### <a name="parameters"></a>Parameter

*T*<br/>
Die Benutzerdaten Satz-Klasse.

## <a name="remarks"></a>Bemerkungen

Sie wird verwendet, wenn ein Datensatz statisch an eine Datenquelle gebunden ist. Der Datensatz enthält den Puffer. Diese Klasse unterstützt mehrere Accessoren für ein Rowset.

Verwenden Sie diesen Accessortyp, wenn Sie die Struktur und den Typ der Datenbank kennen.

Wenn der Accessor Felder enthält, die auf den Speicher zeigen (z. b. eine- `BSTR` oder-Schnittstelle), die freigegeben werden muss, müssen Sie die Member-Funktion [CAccessorRowset:: freerecordmemory](./caccessorrowset-class.md#freerecordmemory) vor dem Lesen des nächsten Datensatzes abrufen.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atldbcli.h

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenz zu OLE DB Consumervorlagen](../../data/oledb/ole-db-consumer-templates-reference.md)
