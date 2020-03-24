---
title: CStreamRowset-Klasse
ms.date: 11/04/2016
f1_keywords:
- ATL::CStreamRowset<TAccessor>
- ATL::CStreamRowset
- CStreamRowset
- ATL.CStreamRowset<TAccessor>
- ATL.CStreamRowset
- CStreamRowset::CStreamRowset
- CStreamRowset.CStreamRowset
- ATL.CStreamRowset.CStreamRowset
- ATL::CStreamRowset::CStreamRowset
- CStreamRowset<TAccessor>::CStreamRowset
- ATL::CStreamRowset<TAccessor>::CStreamRowset
- CStreamRowset<TAccessor>.Close
- ATL.CStreamRowset<TAccessor>.Close
- CStreamRowset::Close
- CStreamRowset<TAccessor>::Close
- ATL::CStreamRowset::Close
- ATL.CStreamRowset.Close
- ATL::CStreamRowset<TAccessor>::Close
- CStreamRowset.Close
helpviewer_keywords:
- CStreamRowset class
- CStreamRowset class, constructor
- Close method
ms.assetid: a106e953-a38a-464e-8ea5-28963d9e4811
ms.openlocfilehash: 300933fd6d10f5da39d9276db746ab789851a9a1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211171"
---
# <a name="cstreamrowset-class"></a>CStreamRowset-Klasse

Wird in einer `CCommand`-oder `CTable` Deklaration verwendet.

## <a name="syntax"></a>Syntax

```cpp
template <class TAccessor = CAccessorBase>
class CStreamRowset
```

### <a name="parameters"></a>Parameter

*TAccessor*<br/>
Eine Accessor-Klasse.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atldbcli.h

## <a name="members"></a>Members

### <a name="methods"></a>Methoden

|||
|-|-|
|[CStreamRowset](#cstreamrowset)|Konstruktor. Instanziiert und initialisiert das `CStreamRowset`-Objekt.|
|[Close](#close)|Gibt den [ISequentialStream](/previous-versions/windows/desktop/ms718035(v=vs.85)) -Schnittstellen Zeiger in der-Klasse frei.|

## <a name="remarks"></a>Bemerkungen

Verwenden Sie `CStreamRowset` in der `CCommand`-oder `CTable` Deklaration, z. b.:

[!code-cpp[NVC_OLEDB_Consumer#11](../../data/oledb/codesnippet/cpp/cstreamrowset-class_1.cpp)]

oder

[!code-cpp[NVC_OLEDB_Consumer#12](../../data/oledb/codesnippet/cpp/cstreamrowset-class_2.cpp)]

`ICommand::Execute` gibt einen `ISequentialStream`-Zeiger zurück, der in `m_spStream`gespeichert wird. Anschließend verwenden Sie die `Read`-Methode, um die (Unicode-Zeichen folgen) im XML-Format abzurufen. Beispiel:

[!code-cpp[NVC_OLEDB_Consumer#13](../../data/oledb/codesnippet/cpp/cstreamrowset-class_3.cpp)]

SQL Server 2000 wird die XML-Formatierung durchführt und alle Spalten und alle Zeilen des Rowsets als eine XML-Zeichenfolge zurückgegeben.

> [!NOTE]
>  Diese Funktion funktioniert nur mit SQL Server 2000.

## <a name="cstreamrowsetcstreamrowset"></a><a name="cstreamrowset"></a>CStreamRowset:: CStreamRowset

Instanziiert und initialisiert das `CStreamRowset`-Objekt.

### <a name="syntax"></a>Syntax

```cpp
CStreamRowset();
```

## <a name="cstreamrowsetclose"></a><a name="close"></a>CStreamRowset:: Close

Gibt den [ISequentialStream](/previous-versions/windows/desktop/ms718035(v=vs.85)) -Schnittstellen Zeiger in der-Klasse frei.

### <a name="syntax"></a>Syntax

```cpp
void Close();
```

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenz der OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-reference.md)
