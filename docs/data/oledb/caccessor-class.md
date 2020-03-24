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
ms.openlocfilehash: 2b30cef2baf8c13c5001e44901b984aa1293494d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212302"
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

Wenn der-Accessor Felder enthält, die auf den Speicher zeigen (z. b. eine `BSTR` oder eine Schnittstelle), der freigegeben werden muss, müssen Sie die Member-Funktion [CAccessorRowset:: freerecordmemory](../../data/oledb/caccessorrowset-freerecordmemory.md) abrufen, bevor der nächste Datensatz gelesen wird.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atldbcli.h

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenz der OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-reference.md)
