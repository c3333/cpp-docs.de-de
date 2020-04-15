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
ms.openlocfilehash: ad4987422fd200faef141150908d4df0722f669a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366277"
---
# <a name="cstreamrowset-class"></a>CStreamRowset-Klasse

Wird in `CCommand` `CTable` einer oder einer Deklaration verwendet.

## <a name="syntax"></a>Syntax

```cpp
template <class TAccessor = CAccessorBase>
class CStreamRowset
```

### <a name="parameters"></a>Parameter

*TAccessor*<br/>
Eine Accessorklasse.

## <a name="requirements"></a>Anforderungen

**Header:** atldbcli.h

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|||
|-|-|
|[CStreamRowset](#cstreamrowset)|Konstruktor. Instanziiert und initialisiert `CStreamRowset` das Objekt.|
|[Schließen](#close)|Gibt den [ISequentialStream-Schnittstellenzeiger](/previous-versions/windows/desktop/ms718035(v=vs.85)) in der Klasse frei.|

## <a name="remarks"></a>Bemerkungen

Verwenden `CStreamRowset` Sie `CCommand` `CTable` in Ihrer oder Deklaration, z. B.:

[!code-cpp[NVC_OLEDB_Consumer#11](../../data/oledb/codesnippet/cpp/cstreamrowset-class_1.cpp)]

oder

[!code-cpp[NVC_OLEDB_Consumer#12](../../data/oledb/codesnippet/cpp/cstreamrowset-class_2.cpp)]

`ICommand::Execute`gibt `ISequentialStream` einen Zeiger zurück, `m_spStream`der in gespeichert wird. Anschließend verwenden `Read` Sie die Methode, um die (Unicode-Zeichenfolge) Daten im XML-Format abzurufen. Beispiel:

[!code-cpp[NVC_OLEDB_Consumer#13](../../data/oledb/codesnippet/cpp/cstreamrowset-class_3.cpp)]

SQL Server 2000 führt die XML-Formatierung aus und gibt alle Spalten und alle Zeilen des Rowsets als eine XML-Zeichenfolge zurück.

> [!NOTE]
> Diese Funktion funktioniert nur mit SQL Server 2000.

## <a name="cstreamrowsetcstreamrowset"></a><a name="cstreamrowset"></a>CStreamRowset::CStreamRowset

Instanziiert und initialisiert `CStreamRowset` das Objekt.

### <a name="syntax"></a>Syntax

```cpp
CStreamRowset();
```

## <a name="cstreamrowsetclose"></a><a name="close"></a>CStreamRowset::Schließen

Gibt den [ISequentialStream-Schnittstellenzeiger](/previous-versions/windows/desktop/ms718035(v=vs.85)) in der Klasse frei.

### <a name="syntax"></a>Syntax

```cpp
void Close();
```

## <a name="see-also"></a>Siehe auch

[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Ole DB Consumer Templates Referenz](../../data/oledb/ole-db-consumer-templates-reference.md)
