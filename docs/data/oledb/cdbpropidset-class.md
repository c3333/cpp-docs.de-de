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
ms.openlocfilehash: 24cc621e522ed1939fe3127d97e8d54b75fa1618
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838294"
---
# <a name="cdbpropidset-class"></a>CDBPropIDSet-Klasse

Erbt von der `DBPROPIDSET` -Struktur und fügt einen Konstruktor hinzu, der Schlüsselfelder und die [addpropertyid](../../data/oledb/cdbpropidset-addpropertyid.md) -Zugriffsmethode initialisiert.

## <a name="syntax"></a>Syntax

```cpp
class CDBPropIDSet : public tagDBPROPIDSET
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atldbcli.h

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

| Name | Beschreibung |
|-|-|
|[AddPropertyID](#addpropertyid)|Fügt dem Eigenschaften-ID-Satz eine Eigenschaft hinzu.|
|[CDBPropIDSet](#cdbpropidset)|Konstruktor.|
|[SetGUID](#setguid)|Legt die GUID für den festgelegten Eigenschaften-ID-Wert fest.|

### <a name="operators"></a>Operatoren

| Name | Beschreibung |
|-|-|
|[Operator =](#op_equal)|Weist den Inhalt von einer eigen schafts-ID einem anderen Satz zu.|

## <a name="remarks"></a>Bemerkungen

OLE DB Consumer verwenden `DBPROPIDSET` Strukturen, um ein Array von Eigenschaften-IDs zu übergeben, für die der Consumer Eigenschafts Informationen erhalten möchte. Die in einer einzelnen [DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85)) -Struktur identifizierten Eigenschaften gehören zu einem Eigenschaften Satz.

## <a name="cdbpropidsetaddpropertyid"></a><a name="addpropertyid"></a> Cdbpropidset:: addpropertyid

Fügt dem Eigenschaften-ID-Satz eine eigen schafts-ID hinzu.

### <a name="syntax"></a>Syntax

```cpp
bool AddPropertyID(DBPROPID propid) throw();
```

#### <a name="parameters"></a>Parameter

*PROPID*<br/>
in Die eigen schafts-ID, die dem Eigenschaften-ID-Satz hinzugefügt werden soll.

## <a name="cdbpropidsetcdbpropidset"></a><a name="cdbpropidset"></a> Cdbpropidset:: cdbpropidset

Der Konstruktor. Initialisiert die `rgProperties` `cProperties` Felder, und (optional) `guidPropertySet` der [DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85)) -Struktur.

### <a name="syntax"></a>Syntax

```cpp
CDBPropIDSet(const GUID& guid);

CDBPropIDSet(const CDBPropIDSet& propidset);

CDBPropIDSet();
```

#### <a name="parameters"></a>Parameter

*guid*<br/>
in Eine GUID, die verwendet wird, um das Feld zu initialisieren `guidPropertySet` .

*propidset*<br/>
in Ein weiteres `CDBPropIDSet` Objekt für die Kopier Erstellung.

## <a name="cdbpropidsetsetguid"></a><a name="setguid"></a> Cdbpropidset:: SetGuid

Legt das GUID-Feld in der- `DBPROPIDSET` Struktur fest.

### <a name="syntax"></a>Syntax

```cpp
void SetGUID(const GUID& guid) throw();
```

#### <a name="parameters"></a>Parameter

*guid*<br/>
in Eine GUID, die verwendet wird, um das- `guidPropertySet` Feld der [DBPROPIDSET](/previous-versions/windows/desktop/ms717981(v=vs.85)) -Struktur festzulegen.

### <a name="remarks"></a>Bemerkungen

Dieses Feld kann auch durch den- [Konstruktor](../../data/oledb/cdbpropidset-cdbpropidset.md) festgelegt werden. Diese Funktion wird aufgerufen, wenn Sie den Standardkonstruktor für diese Klasse verwenden.

## <a name="cdbpropidsetoperator-"></a><a name="op_equal"></a> Cdbpropidset:: Operator =

Weist den Inhalt einer eigen schafts-ID einem anderen ID-Eigenschaften Satz zu.

### <a name="syntax"></a>Syntax

```cpp
CDBPropIDSet& operator =(CDBPropIDSet& propset) throw();
```

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenz zu OLE DB Consumervorlagen](../../data/oledb/ole-db-consumer-templates-reference.md)
