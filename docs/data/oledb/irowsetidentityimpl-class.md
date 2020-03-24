---
title: IRowsetIdentityImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- ATL::IRowsetIdentityImpl
- ATL.IRowsetIdentityImpl
- IRowsetIdentityImpl
- IRowsetIdentityImpl.IsSameRow
- ATL.IRowsetIdentityImpl.IsSameRow
- IRowsetIdentityImpl::IsSameRow
- ATL::IRowsetIdentityImpl::IsSameRow
helpviewer_keywords:
- IRowsetIdentityImpl class
- IsSameRow method
ms.assetid: 56821edf-e045-40c8-96bd-231552cd5799
ms.openlocfilehash: 20f558099c02d7de8a20b3cf631812b44a742a48
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210405"
---
# <a name="irowsetidentityimpl-class"></a>IRowsetIdentityImpl-Klasse

Implementiert die [IRowset tidentity](/previous-versions/windows/desktop/ms715913(v=vs.85)) -Schnittstelle OLE DB, die das Testen der Zeilen Identität ermöglicht.

## <a name="syntax"></a>Syntax

```cpp
template <class T, class RowClass = CSimpleRow>
class ATL_NO_VTABLE IRowsetIdentityImpl
   : public IRowsetIdentity
```

### <a name="parameters"></a>Parameter

*T*<br/>
Eine von `IRowsetIdentityImpl`abgeleitete Klasse.

*RowClass*<br/>
Die Speichereinheit für die `HROW`.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atldb.h

## <a name="members"></a>Members

### <a name="methods"></a>Methoden

|||
|-|-|
|[IsSameRow](#issamerow)|Vergleicht zwei Zeilen Handles, um festzustellen, ob Sie auf dieselbe Zeile verweisen.|

## <a name="irowsetidentityimplissamerow"></a><a name="issamerow"></a>Irowabtidentityimpl:: IsSameRow

Vergleicht zwei Zeilen Handles, um festzustellen, ob Sie auf dieselbe Zeile verweisen.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD(IsSameRow )(HROW hThisRow,
   HROW hThatRow);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie in der *OLE DB Programmierer-Referenz*unter [irowsee tidentity:: IsSameRow](/previous-versions/windows/desktop/ms719629(v=vs.85)) .

### <a name="remarks"></a>Bemerkungen

Zum Vergleichen von Zeilen Handles wandelt diese Methode die `HROW` Handles in `RowClass` Member um und ruft `memcmp` auf den Zeigern auf.

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektur von OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-template-architecture.md)
