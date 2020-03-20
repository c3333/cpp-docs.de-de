---
title: CDBPropSet-Klasse
ms.date: 11/04/2016
f1_keywords:
- CDBPropSet
- ATL.CDBPropSet
- ATL::CDBPropSet
- CDBPropSet::AddProperty
- CDBPropSet.AddProperty
- AddProperty
- ATL::CDBPropSet::AddProperty
- ATL.CDBPropSet.AddProperty
- CDBPropSet.CDBPropSet
- CDBPropSet::CDBPropSet
- ATL::CDBPropSet::CDBPropSet
- ATL.CDBPropSet.CDBPropSet
- CDBPropSet.operator=
- ATL::CDBPropSet::operator=
- ATL.CDBPropSet.operator=
- CDBPropSet::operator=
- ATL.CDBPropSet.SetGUID
- CDBPropSet.SetGUID
- ATL::CDBPropSet::SetGUID
- CDBPropSet::SetGUID
helpviewer_keywords:
- CDBPropSet class
- AddProperty method
- CDBPropSet class, constructor
- operator =, property sets
- = operator, with OLE DB templates
- operator=, property sets
- SetGUID method
- AddProperty method
ms.assetid: 54190149-c277-4679-b81a-ef484d4d1c00
ms.openlocfilehash: 08cab967fbfbd4b3207e96a4fdbd2d2dbc6da793
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79546116"
---
# <a name="cdbpropset-class"></a>CDBPropSet-Klasse

Erbt von der `DBPROPSET` Struktur und fügt einen Konstruktor hinzu, der Schlüsselfelder und die `AddProperty` Zugriffsmethode initialisiert.

## <a name="syntax"></a>Syntax

```cpp
class CDBPropSet : public tagDBPROPSET
```

## <a name="requirements"></a>Voraussetzungen

**Header:** atldbcli.h

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|||
|-|-|
|[AddProperty](#addproperty)|Fügt dem Eigenschaften Satz eine Eigenschaft hinzu.|
|[CDBPropSet](#cdbpropset)|Konstruktor.|
|[SetGUID](#setguid)|Legt das `guidPropertySet`-Feld der `DBPROPSET` Struktur fest.|

### <a name="operators"></a>Operatoren

|||
|-|-|
|[Operator =](#op_equal)|Weist den Inhalt einer Eigenschaft einem anderen Satz zu.|

## <a name="remarks"></a>Hinweise

OLE DB Anbieter und Consumer verwenden `DBPROPSET` Strukturen, um Arrays von `DBPROP` Strukturen zu übergeben. Jede `DBPROP` Struktur stellt eine einzelne Eigenschaft dar, die festgelegt werden kann.

## <a name="cdbpropsetaddproperty"></a><a name="addproperty"></a>CDBPropSet:: AddProperty

Fügt dem Eigenschaften Satz eine Eigenschaft hinzu.

### <a name="syntax"></a>Syntax

```cpp
bool AddProperty(DWORD dwPropertyID,
   constVARIANT& var,
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   LPCSTR szValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   LPCWSTR szValue,DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   bool bValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   BYTE bValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,
   short nValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,
   long nValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,
   float fltValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,
   double dblValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   CY cyValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();
```

#### <a name="parameters"></a>Parameter

*dwpropertyid*<br/>
in Die ID der Eigenschaft, die hinzugefügt werden soll. Wird verwendet, um den `dwPropertyID` der `DBPROP` Struktur zu initialisieren, die dem Eigenschaften Satz hinzugefügt wurde.

*var*<br/>
in Ein Variant, mit dem der Eigenschafts Wert für die `DBPROP` Struktur initialisiert wird, die dem Eigenschaften Satz hinzugefügt wurde.

*szvalue*<br/>
in Eine Zeichenfolge, mit der der Eigenschafts Wert für die `DBPROP` Struktur initialisiert wird, die dem Eigenschaften Satz hinzugefügt wurde.

*bValue*<br/>
in Ein `BYTE` oder boolescher Wert, der verwendet wird, um den Eigenschafts Wert für die `DBPROP` Struktur zu initialisieren, die dem Eigenschaften Satz hinzugefügt wurde.

*nWert*<br/>
in Ein ganzzahliger Wert, mit dem der Eigenschafts Wert für die `DBPROP` Struktur initialisiert wird, die dem Eigenschaften Satz hinzugefügt wurde.

*fltvalue*<br/>
in Ein Gleit Komma Wert, der verwendet wird, um den Eigenschafts Wert für die `DBPROP` Struktur zu initialisieren, die dem Eigenschaften Satz hinzugefügt wurde.

*dblvalue*<br/>
in Ein Gleit Komma Wert mit doppelter Genauigkeit, der verwendet wird, um den Eigenschafts Wert für die `DBPROP` Struktur zu initialisieren, die dem Eigenschaften Satz hinzugefügt wurde.

*cyvalue*<br/>
in Ein CY Currency-Wert, mit dem der Eigenschafts Wert für die `DBPROP` Struktur initialisiert wird, die dem Eigenschaften Satz hinzugefügt wurde.

### <a name="return-value"></a>Rückgabewert

**true** , wenn die Eigenschaft erfolgreich hinzugefügt wurde. Andernfalls lautet der Wert **false**.

## <a name="cdbpropsetcdbpropset"></a><a name="cdbpropset"></a>CDBPropSet:: CDBPropSet

Der Konstruktor. Initialisiert die Felder `rgProperties`, `cProperties`und `guidPropertySet` der [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) -Struktur.

### <a name="syntax"></a>Syntax

```cpp
CDBPropSet(const GUID& guid);

CDBPropSet(const CDBPropSet& propset);

CDBPropSet();
```

#### <a name="parameters"></a>Parameter

*guid*<br/>
in Eine GUID, die verwendet wird, um das `guidPropertySet` Feld zu initialisieren.

*propset*<br/>
in Ein weiteres `CDBPropSet` Objekt für die Kopier Konstruktion.

## <a name="cdbpropsetsetguid"></a><a name="setguid"></a>CDBPropSet:: SetGuid

Legt das `guidPropertySet` Feld in der `DBPROPSET`-Struktur fest.

### <a name="syntax"></a>Syntax

```cpp
void SetGUID(const GUID& guid) throw();
```

#### <a name="parameters"></a>Parameter

*guid*<br/>
in Eine GUID, die verwendet wird, um das `guidPropertySet`-Feld der [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) -Struktur festzulegen.

### <a name="remarks"></a>Hinweise

Dieses Feld kann auch durch den- [Konstruktor](../../data/oledb/cdbpropset-cdbpropset.md) festgelegt werden.

## <a name="cdbpropsetoperator-"></a><a name="op_equal"></a>CDBPropSet:: Operator =

Weist den Inhalt einer Eigenschaften Gruppe einem anderen Eigenschaften Satz zu.

### <a name="syntax"></a>Syntax

```cpp
CDBPropSet& operator =(CDBPropSet& propset) throw();
```

## <a name="see-also"></a>Siehe auch

[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenz der OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CDBPropIDSet-Klasse](../../data/oledb/cdbpropidset-class.md)<br/>
[DBPROPSET-Struktur](/previous-versions/windows/desktop/ms714367(v=vs.85))
[DBPROP-Struktur](/previous-versions/windows/desktop/ms717970(v=vs.85))