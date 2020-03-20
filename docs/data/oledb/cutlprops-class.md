---
title: CUtlProps-Klasse
ms.date: 11/04/2016
f1_keywords:
- CUtlProps
- CUtlProps::GetPropValue
- CUtlProps.GetPropValue
- GetPropValue
- CUtlProps::IsValidValue
- CUtlProps.IsValidValue
- IsValidValue
- OnPropertyChanged
- CUtlProps.OnPropertyChanged
- CUtlProps::OnPropertyChanged
- SetPropValue
- ATL::CUtlProps<T>::SetPropValue
- ATL.CUtlProps<T>.SetPropValue
- ATL.CUtlProps.SetPropValue
- CUtlProps::SetPropValue
- CUtlProps<T>::SetPropValue
- CUtlProps.SetPropValue
- CUtlProps<T>.SetPropValue
- ATL::CUtlProps::SetPropValue
helpviewer_keywords:
- CUtlProps class
- GetPropValue method
- IsValidValue method
- OnInterfaceRequested method
- OnPropertyChanged method
- SetPropValue method
ms.assetid: bb525178-765c-4e23-a110-c0fd70c05437
ms.openlocfilehash: bbeae4faad4d650d8dc44a61a22b1fcc63a0bc15
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79545552"
---
# <a name="cutlprops-class"></a>CUtlProps-Klasse

Implementiert Eigenschaften für eine Reihe von OLE DB Eigenschaften Schnittstellen (z. b. `IDBProperties`, `IDBProperties`und `IRowsetInfo`).

## <a name="syntax"></a>Syntax

```cpp
template < class T >
class ATL_NO_VTABLE CUtlProps : public CUtlPropsBase
```

### <a name="parameters"></a>Parameter

*T*<br/>
Die Klasse, die die `BEGIN_PROPSET_MAP`enthält.

## <a name="requirements"></a>Voraussetzungen

**Header:** atldb.h

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|||
|-|-|
|[GetPropValue](#getpropvalue)|Ruft eine Eigenschaft aus einem Eigenschaften Satz ab.|
|[IsValidValue](#isvalidvalue)|Wird zum Überprüfen eines Werts verwendet, bevor eine Eigenschaft festgelegt wird.|
|[OnInterfaceRequested](#oninterfacerequested)|Verarbeitet Anforderungen für eine optionale Schnittstelle, wenn ein Consumer eine Methode für eine Schnittstelle zum Erstellen von Objekten aufruft.|
|[OnPropertyChanged](#onpropertychanged)|Wird aufgerufen, nachdem eine Eigenschaft zum Verarbeiten verketteter Eigenschaften festgelegt wurde|
|[SetPropValue](#setpropvalue)|Legt eine Eigenschaft in einem Eigenschaften Satz fest.|

## <a name="remarks"></a>Hinweise

Der größte Teil dieser Klasse ist ein Implementierungsdetail.

`CUtlProps` enthält zwei Member zum internen Festlegen von Eigenschaften: [GetPropValue](../../data/oledb/cutlprops-getpropvalue.md) und [SetPropValue](../../data/oledb/cutlprops-setpropvalue.md).

Weitere Informationen zu den in einer Eigenschaften Satz Zuordnung verwendeten Makros finden Sie unter [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md) und [END_PROPSET_MAP](../../data/oledb/end-propset-map.md).

## <a name="cutlpropsgetpropvalue"></a><a name="getpropvalue"></a>Cutlrequips:: GetPropValue

Ruft eine Eigenschaft aus einem Eigenschaften Satz ab.

### <a name="syntax"></a>Syntax

```cpp
OUT_OF_LINE HRESULT GetPropValue(const GUID* pguidPropSet,
   DBPROPID dwPropId,
   VARIANT* pvValue);
```

#### <a name="parameters"></a>Parameter

*pguidpropset*<br/>
in Die GUID für das propset.

*dwPropId*<br/>
in Der Eigenschafts Index.

*pvvalue*<br/>
vorgenommen Ein Zeiger auf einen Variant-Wert, der den neuen Eigenschafts Wert enthält.

### <a name="return-value"></a>Rückgabewert

bei erfolgreicher S_OK `Failure`.

## <a name="cutlpropsisvalidvalue"></a><a name="isvalidvalue"></a>Cutlrequid:: IsValidValue

Wird zum Überprüfen eines Werts verwendet, bevor eine Eigenschaft festgelegt wird.

### <a name="syntax"></a>Syntax

```cpp
virtual HRESULT CUtlPropsBase::IsValidValue(ULONG /* iCurSet */,
   DBPROP* pDBProp);
```

#### <a name="parameters"></a>Parameter

*icurrset*<br/>
Der Index des Eigenschaften Satz Arrays. 0 (null), wenn nur ein Eigenschaften Satz vorhanden ist.

*pdbprop*<br/>
Die eigen schafts-ID und der neue Wert in einer [DBPROP](/previous-versions/windows/desktop/ms717970(v=vs.85)) -Struktur.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard. Der Standard Rückgabewert ist S_OK.

### <a name="remarks"></a>Hinweise

Wenn Sie über Validierungs Routinen verfügen, die Sie für einen Wert ausführen möchten, den Sie zum Festlegen einer Eigenschaft verwenden möchten, sollten Sie diese Funktion überschreiben. Beispielsweise können Sie DBPROP_AUTH_PASSWORD anhand einer Kenn Wort Tabelle validieren, um einen gültigen Wert zu bestimmen.

## <a name="cutlpropsoninterfacerequested"></a><a name="oninterfacerequested"></a>Cutl-Eigenschaften:: oninterfakerequessiert

Verarbeitet Anforderungen für eine optionale Schnittstelle, wenn ein Consumer eine Methode für eine der Schnittstellen zum Erstellen von Objekten aufruft.

### <a name="syntax"></a>Syntax

```cpp
virtual HRESULT CUtlPropsBase::OnInterfaceRequested(REFIID riid);
```

#### <a name="parameters"></a>Parameter

*riid*<br/>
in Die IID für die angeforderte Schnittstelle. Weitere Informationen finden Sie in der Beschreibung des *riid* -Parameters `ICommand::Execute` in der *OLE DB Programmierer-Referenz* (im *MDAC-SDK*).

### <a name="remarks"></a>Hinweise

`OnInterfaceRequested` behandelt Consumeranforderungen für eine optionale Schnittstelle, wenn ein Consumer eine Methode für eine der Objekt Erstellungs Schnittstellen (z. b. `IDBCreateSession`, `IDBCreateCommand`, `IOpenRowset`oder `ICommand`) aufruft. Die entsprechende OLE DB-Eigenschaft für die angeforderte Schnittstelle wird festgelegt. Wenn der Consumer z. b. `IID_IRowsetLocate`anfordert, legt `OnInterfaceRequested` die `DBPROP_IRowsetLocate`-Schnittstelle fest. Auf diese Weise wird der richtige Zustand während der Rowseterstellung beibehalten.

Diese Methode wird aufgerufen, wenn der Consumer `IOpenRowset::OpenRowset` oder `ICommand::Execute`aufruft.

Wenn ein Consumer ein Objekt öffnet und eine optionale Schnittstelle anfordert, sollte der Anbieter die Eigenschaft, die dieser Schnittstelle zugeordnet ist, VARIANT_TRUE festlegen. Um die Eigenschaften spezifische Verarbeitung zuzulassen, wird `OnInterfaceRequested` aufgerufen, bevor die `Execute`-Methode des Anbieters aufgerufen wird. Standardmäßig verarbeitet `OnInterfaceRequested` die folgenden Schnittstellen:

- `IRowsetLocate`

- `IRowsetChange`

- `IRowsetUpdate`

- `IConnectionPointContainer`

- `IRowsetScroll`

Wenn Sie andere Schnittstellen verarbeiten möchten, überschreiben Sie diese Funktion in der Datenquelle, der Sitzung, dem Befehl oder der Rowsetklasse, um Funktionen zu verarbeiten. Die außer Kraft Setzung sollte die normalen Eigenschaften der Eigenschaften "Set/Get" durchlaufen, um sicherzustellen, dass Einstellungs Eigenschaften auch alle verketteten Eigenschaften festlegen (siehe [OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md)).

## <a name="cutlpropsonpropertychanged"></a><a name="onpropertychanged"></a>Cutl-Eigenschaften:: OnPropertyChanged

Wird aufgerufen, nachdem eine Eigenschaft zum Verarbeiten verketteter Eigenschaften festgelegt wurde

### <a name="syntax"></a>Syntax

```cpp
virtual HRESULT OnPropertyChanged(ULONG /* iCurSet */,
   DBPROP* pDBProp);
```

#### <a name="parameters"></a>Parameter

*icurrset*<br/>
Der Index des Eigenschaften Satz Arrays. 0 (null), wenn nur ein Eigenschaften Satz vorhanden ist.

*pdbprop*<br/>
Die eigen schafts-ID und der neue Wert in einer [DBPROP](/previous-versions/windows/desktop/ms717970(v=vs.85)) -Struktur.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard. Der Standard Rückgabewert ist S_OK.

### <a name="remarks"></a>Hinweise

Wenn Sie verkettete Eigenschaften verarbeiten möchten, z. b. Lesezeichen oder Updates, deren Werte von einem anderen Eigenschafts Wert abhängen, sollten Sie diese Funktion überschreiben.

### <a name="example"></a>Beispiel

In dieser Funktion ruft der Benutzer die eigen schafts-ID aus dem `DBPROP*`-Parameter ab. Nun ist es möglich, die ID mit einer Eigenschaft mit einer Kette zu vergleichen. Wenn die-Eigenschaft gefunden wird, wird `SetProperties` mit der-Eigenschaft aufgerufen, die nun in Verbindung mit der anderen-Eigenschaft festgelegt wird. Wenn in diesem Fall die Eigenschaft `DBPROP_IRowsetLocate`, `DBPROP_LITERALBOOKMARKS`oder `DBPROP_ORDEREDBOOKMARKS` abgerufen wird, kann die `DBPROP_BOOKMARKS`-Eigenschaft festgelegt werden.

[!code-cpp[NVC_OLEDB_Provider#2](../../data/oledb/codesnippet/cpp/cutlprops-onpropertychanged_1.h)]

## <a name="cutlpropssetpropvalue"></a><a name="setpropvalue"></a>Cutlrequips:: SetPropValue

Legt eine Eigenschaft in einem Eigenschaften Satz fest.

### <a name="syntax"></a>Syntax

```cpp
HRESULT SetPropValue(const GUID* pguidPropSet,
   DBPROPID dwPropId,
   VARIANT* pvValue);
```

#### <a name="parameters"></a>Parameter

*pguidpropset*<br/>
in Die GUID für das propset.

*dwPropId*<br/>
in Der Eigenschafts Index.

*pvvalue*<br/>
in Ein Zeiger auf einen Variant-Wert, der den neuen Eigenschafts Wert enthält.

### <a name="return-value"></a>Rückgabewert

bei erfolgreicher S_OK `Failure`.

## <a name="see-also"></a>Siehe auch

[OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektur von OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-template-architecture.md)