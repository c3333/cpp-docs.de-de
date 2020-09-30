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
ms.openlocfilehash: 45772896cac520eba35ec475f8b6ae7bd2993045
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502460"
---
# <a name="cdbpropset-class"></a>CDBPropSet-Klasse

Erbt von der `DBPROPSET` -Struktur und fügt einen Konstruktor hinzu, mit dem Schlüsselfelder und die `AddProperty` Zugriffsmethode initialisiert werden.

## <a name="syntax"></a>Syntax

```cpp
class CDBPropSet : public tagDBPROPSET
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atldbcli.h

## <a name="members"></a>Members

### <a name="methods"></a>Methoden

| Name | Beschreibung |
|-|-|
|[AddProperty](#addproperty)|Fügt dem Eigenschaften Satz eine Eigenschaft hinzu.|
|[CDBPropSet](#cdbpropset)|Konstruktor.|
|[SetGUID](#setguid)|Legt das- `guidPropertySet` Feld der- `DBPROPSET` Struktur fest.|

### <a name="operators"></a>Operatoren

| Name | Beschreibung |
|-|-|
|[Operator =](#op_equal)|Weist den Inhalt einer Eigenschaft einem anderen Satz zu.|

## <a name="remarks"></a>Bemerkungen

OLE DB Anbieter und Consumer verwenden `DBPROPSET` Strukturen, um Arrays von `DBPROP` Strukturen zu übergeben. Jede- `DBPROP` Struktur stellt eine einzelne Eigenschaft dar, die festgelegt werden kann.

## <a name="cdbpropsetaddproperty"></a><a name="addproperty"></a> CDBPropSet:: AddProperty

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
in Die ID der Eigenschaft, die hinzugefügt werden soll. Wird verwendet, um die `dwPropertyID` der `DBPROP` Struktur zu initialisieren, die dem Eigenschaften Satz hinzugefügt wurde.

*var*<br/>
in Eine Variante, die verwendet wird, um den Eigenschafts Wert für die dem `DBPROP` Eigenschaften Satz hinzugefügte Struktur zu initialisieren.

*szvalue*<br/>
in Eine Zeichenfolge, mit der der Eigenschafts Wert für die dem `DBPROP` Eigenschaften Satz hinzugefügte Struktur initialisiert wird.

*bValue*<br/>
in Ein `BYTE` boolescher Wert oder ein boolescher Wert, mit dem der Eigenschafts Wert für die dem `DBPROP` Eigenschaften Satz hinzugefügte Struktur initialisiert wird

*nWert*<br/>
in Ein ganzzahliger Wert, mit dem der Eigenschafts Wert für die dem `DBPROP` Eigenschaften Satz hinzugefügte Struktur initialisiert wird.

*fltvalue*<br/>
in Ein Gleit Komma Wert, der verwendet wird, um den Eigenschafts Wert für die `DBPROP` Struktur zu initialisieren, die dem Eigenschaften Satz hinzugefügt wurde.

*dblvalue*<br/>
in Ein Gleit Komma Wert mit doppelter Genauigkeit, der verwendet wird, um den Eigenschafts Wert für die `DBPROP` Struktur zu initialisieren, die dem Eigenschaften Satz hinzugefügt wurde.

*cyvalue*<br/>
in Ein CY Currency-Wert, der verwendet wird, um den Eigenschafts Wert für die dem `DBPROP` Eigenschaften Satz hinzugefügte Struktur zu initialisieren.

### <a name="return-value"></a>Rückgabewert

**`true`** , wenn die Eigenschaft erfolgreich hinzugefügt wurde. Andernfalls **`false`** .

## <a name="cdbpropsetcdbpropset"></a><a name="cdbpropset"></a> CDBPropSet:: CDBPropSet

Der Konstruktor. Initialisiert die `rgProperties` `cProperties` Felder, und `guidPropertySet` der [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) -Struktur.

### <a name="syntax"></a>Syntax

```cpp
CDBPropSet(const GUID& guid);

CDBPropSet(const CDBPropSet& propset);

CDBPropSet();
```

#### <a name="parameters"></a>Parameter

*guid*<br/>
in Eine GUID, die verwendet wird, um das Feld zu initialisieren `guidPropertySet` .

*propset*<br/>
in Ein weiteres `CDBPropSet` Objekt für die Kopier Erstellung.

## <a name="cdbpropsetsetguid"></a><a name="setguid"></a> CDBPropSet:: SetGuid

Legt das `guidPropertySet` Feld in der- `DBPROPSET` Struktur fest.

### <a name="syntax"></a>Syntax

```cpp
void SetGUID(const GUID& guid) throw();
```

#### <a name="parameters"></a>Parameter

*guid*<br/>
in Eine GUID, die verwendet wird, um das- `guidPropertySet` Feld der [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) -Struktur festzulegen.

### <a name="remarks"></a>Bemerkungen

Dieses Feld kann auch durch den- [Konstruktor](#cdbpropset) festgelegt werden.

## <a name="cdbpropsetoperator-"></a><a name="op_equal"></a> CDBPropSet:: Operator =

Weist den Inhalt einer Eigenschaften Gruppe einem anderen Eigenschaften Satz zu.

### <a name="syntax"></a>Syntax

```cpp
CDBPropSet& operator =(CDBPropSet& propset) throw();
```

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenz zu OLE DB Consumervorlagen](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[Cdbpropidset-Klasse](../../data/oledb/cdbpropidset-class.md)<br/>
[DBPROPSET-Struktur](/previous-versions/windows/desktop/ms714367(v=vs.85)) 
 [DBPROP-Struktur](/previous-versions/windows/desktop/ms717970(v=vs.85))
