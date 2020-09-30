---
title: CAccessorBase-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAccessorBase
- CAccessorBase.Close
- CAccessorBase::Close
- GetHAccessor
- CAccessorBase::GetHAccessor
- CAccessorBase.GetHAccessor
- CAccessorBase::GetNumAccessors
- GetNumAccessors
- CAccessorBase.GetNumAccessors
- IsAutoAccessor
- CAccessorBase.IsAutoAccessor
- CAccessorBase::IsAutoAccessor
- CAccessorBase::ReleaseAccessors
- CAccessorBase.ReleaseAccessors
- ReleaseAccessors
helpviewer_keywords:
- CAccessorBase class
- Close method
- GetHAccessor method
- GetNumAccessors method
- IsAutoAccessor method
- ReleaseAccessors method
ms.assetid: 389b65be-11ca-4ae0-9290-60c621c4982b
ms.openlocfilehash: 81b0ecd8ded7acb0c0e376d0869decb2bfcb590e
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509120"
---
# <a name="caccessorbase-class"></a>CAccessorBase-Klasse

Alle Accessoren in den OLE DB Vorlagen werden von dieser Klasse abgeleitet. `CAccessorBase` ermöglicht einem Rowset die Verwaltung mehrerer Accessoren. Außerdem werden Bindungen für Parameter und Ausgabespalten bereitstellt.

## <a name="syntax"></a>Syntax

```cpp
// Replace with syntax
```

## <a name="members"></a>Members

### <a name="methods"></a>Methoden

| Name | Beschreibung |
|--|--|
| [Schließen](#close) | Schließt die Accessoren. |
| [GetHAccessor](#geth) | Ruft das Accessorhandle ab. |
| [GetNumAccessors](#getnum) | Ruft die Anzahl der Accessoren ab, die von der-Klasse erstellt wurden. |
| [IsAutoAccessor](#isauto) | Testet, ob der angegebene Accessor ein Autoaccessor ist. |
| [ReleaseAccessors](#release) | Gibt die Accessoren frei. |

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atldbcli.h

## <a name="caccessorbaseclose"></a><a name="close"></a> CAccessorBase:: Close

Schließt die Accessoren.

### <a name="syntax"></a>Syntax

```cpp
void Close();
```

### <a name="remarks"></a>Bemerkungen

Sie müssen [releaseaccessors](#release) zuerst aufruft.

## <a name="caccessorbasegethaccessor"></a><a name="geth"></a> CAccessorBase:: gethaccessor

Ruft das Accessorhandle eines angegebenen Accessors ab.

### <a name="syntax"></a>Syntax

```cpp
HACCESSOR GetHAccessor(ULONG nAccessor) const;
```

#### <a name="parameters"></a>Parameter

*naccessor*<br/>
in Die Null-Offset Zahl für den Accessor.

### <a name="return-value"></a>Rückgabewert

Der Accessorhandle.

## <a name="caccessorbasegetnumaccessors"></a><a name="getnum"></a> CAccessorBase:: getnumaccessors

Ruft die Anzahl der Accessoren ab, die von der-Klasse erstellt wurden.

### <a name="syntax"></a>Syntax

```cpp
ULONG GetNumAccessors() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Accessoren, die von der-Klasse erstellt wurden.

## <a name="caccessorbaseisautoaccessor"></a><a name="isauto"></a> CAccessorBase:: isautoaccessor

Gibt true zurück, wenn Daten während eines Verschiebungs Vorgangs automatisch für den Accessor abgerufen werden.

### <a name="syntax"></a>Syntax

```cpp
bool IsAutoAccessor(ULONG nAccessor) const;
```

#### <a name="parameters"></a>Parameter

*naccessor*<br/>
in Die Null-Offset Zahl für den Accessor.

### <a name="return-value"></a>Rückgabewert

Gibt zurück, **`true`** Wenn der Accessor ein Autoaccessor ist. Andernfalls wird zurückgegeben **`false`** .

## <a name="caccessorbasereleaseaccessors"></a><a name="release"></a> CAccessorBase:: releaseaccessors

Gibt die von der-Klasse erstellten Accessoren frei.

### <a name="syntax"></a>Syntax

```cpp
HRESULT ReleaseAccessors(IUnknown* pUnk);
```

#### <a name="parameters"></a>Parameter

*Kro*<br/>
in Ein Zeiger auf eine- `IUnknown` Schnittstelle für das COM-Objekt, für das die Accessoren erstellt wurden.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

### <a name="remarks"></a>Bemerkungen

Wird von [CAccessorRowset:: Close](./caccessorrowset-class.md#close)aufgerufen.

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenz zu OLE DB Consumervorlagen](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessorBase-Klasse](../../data/oledb/caccessorbase-class.md)
