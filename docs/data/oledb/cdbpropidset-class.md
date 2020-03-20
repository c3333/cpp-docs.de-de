---
title: CDBPropIDSet-Klasse
ms.date: 11/04/2016
f1_keywords:
- CDBPropIDSet
- ATL.CDBPropIDSet
- ATL::CDBPropIDSet
- CDBPropIDSet.AddPropertyID
- CDBPropIDSet::AddPropertyID
- AddPropertyID
- ATL.CDBPropIDSet.AddPropertyID
- ATL::CDBPropIDSet::AddPropertyID
- ATL::CDBPropIDSet::CDBPropIDSet
- CDBPropIDSet.CDBPropIDSet
- CDBPropIDSet::CDBPropIDSet
- ATL.CDBPropIDSet.CDBPropIDSet
- CDBPropIDSet.operator=
- ATL.CDBPropIDSet.operator=
- ATL::CDBPropIDSet::operator=
- CDBPropIDSet::operator=
- CDBPropIDSet.SetGUID
- ATL::CDBPropIDSet::SetGUID
- ATL.CDBPropIDSet.SetGUID
- CDBPropIDSet::SetGUID
helpviewer_keywords:
- CDBPropIDSet class
- AddPropertyID method
- CDBPropIDSet class, constructor
- operator =, property sets
- = operator, with OLE DB templates
- operator=, property sets
- SetGUID method
ms.assetid: 52bb806c-9581-494d-9af7-50d8a4834805
ms.openlocfilehash: e2fced2ed0e32af15e75c7290733fdc2b4b34dc9
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79546122"
---
# <a name="cdbpropidset-class"></a>CDBPropIDSet-Klasse

Erbt von der `DBPROPIDSET` Struktur und fügt einen Konstruktor hinzu, der Schlüsselfelder und die [addpropertyid](../../data/oledb/cdbpropidset-addpropertyid.md) -Zugriffsmethode initialisiert.

## <a name="syntax"></a>Syntax

```cpp
class CDBPropIDSet : public tagDBPROPIDSET
```

## <a name="requirements"></a>Voraussetzungen

**Header:** atldbcli.h

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|||
|-|-|
|[AddPropertyID](#addpropertyid)|Fügt dem Eigenschaften-ID-Satz eine Eigenschaft hinzu.|
|[CDBPropIDSet](#cdbpropidset)|Konstruktor.|
|[SetGUID](#setguid)|Legt die GUID für den festgelegten Eigenschaften-ID-Wert fest.|

### <a name="operators"></a>Operatoren

|||
|-|-|
|[Operator =](#op_equal)|Weist den Inhalt von einer eigen schafts-ID einem anderen Satz zu.|

## <a name="remarks"></a>Hinweise

OLE DB Consumer verwenden `DBPROPIDSET` Strukturen, um ein Array von Eigenschaften-IDs zu übergeben, für die der Consumer Eigenschafts Informationen erhalten möchte. Die in einer einzelnen [DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85)) -Struktur identifizierten Eigenschaften gehören zu einem Eigenschaften Satz.

## <a name="cdbpropidsetaddpropertyid"></a><a name="addpropertyid"></a>Cdbpropidset:: addpropertyid

Fügt dem Eigenschaften-ID-Satz eine eigen schafts-ID hinzu.

### <a name="syntax"></a>Syntax

```cpp
bool AddPropertyID(DBPROPID propid) throw();
```

#### <a name="parameters"></a>Parameter

*PROPID*<br/>
in Die eigen schafts-ID, die dem Eigenschaften-ID-Satz hinzugefügt werden soll.

## <a name="cdbpropidsetcdbpropidset"></a><a name="cdbpropidset"></a>Cdbpropidset:: cdbpropidset

Der Konstruktor. Initialisiert die `rgProperties`, `cProperties`und (optional) `guidPropertySet` Felder der [DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85)) -Struktur.

### <a name="syntax"></a>Syntax

```cpp
CDBPropIDSet(const GUID& guid);

CDBPropIDSet(const CDBPropIDSet& propidset);

CDBPropIDSet();
```

#### <a name="parameters"></a>Parameter

*guid*<br/>
in Eine GUID, die verwendet wird, um das `guidPropertySet` Feld zu initialisieren.

*propidset*<br/>
in Ein weiteres `CDBPropIDSet` Objekt für die Kopier Konstruktion.

## <a name="cdbpropidsetsetguid"></a><a name="setguid"></a>Cdbpropidset:: SetGuid

Legt das GUID-Feld in der `DBPROPIDSET` Struktur fest.

### <a name="syntax"></a>Syntax

```cpp
void SetGUID(const GUID& guid) throw();
```

#### <a name="parameters"></a>Parameter

*guid*<br/>
in Eine GUID, die verwendet wird, um das `guidPropertySet`-Feld der [DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85)) -Struktur festzulegen.

### <a name="remarks"></a>Hinweise

Dieses Feld kann auch durch den- [Konstruktor](../../data/oledb/cdbpropidset-cdbpropidset.md) festgelegt werden. Diese Funktion wird aufgerufen, wenn Sie den Standardkonstruktor für diese Klasse verwenden.

## <a name="cdbpropidsetoperator-"></a><a name="op_equal"></a>Cdbpropidset:: Operator =

Weist den Inhalt einer eigen schafts-ID einem anderen ID-Eigenschaften Satz zu.

### <a name="syntax"></a>Syntax

```cpp
CDBPropIDSet& operator =(CDBPropIDSet& propset) throw();
```

## <a name="see-also"></a>Siehe auch

[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenz der OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-reference.md)