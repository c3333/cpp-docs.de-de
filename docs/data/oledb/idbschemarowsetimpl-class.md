---
title: IDBSchemaRowsetImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- IDBSchemaRowsetImpl
- CheckRestrictions
- IDBSchemaRowsetImpl::CheckRestrictions
- IDBSchemaRowsetImpl.CheckRestrictions
- IDBSchemaRowsetImpl::CreateSchemaRowset
- ATL::IDBSchemaRowsetImpl::CreateSchemaRowset
- CreateSchemaRowset
- IDBSchemaRowsetImpl.CreateSchemaRowset
- ATL.IDBSchemaRowsetImpl.CreateSchemaRowset
- IDBSchemaRowsetImpl::SetRestrictions
- SetRestrictions
- IDBSchemaRowsetImpl.SetRestrictions
- ATL::IDBSchemaRowsetImpl::GetRowset
- ATL.IDBSchemaRowsetImpl.GetRowset
- IDBSchemaRowsetImpl<SessionClass>::GetRowset
- IDBSchemaRowsetImpl.GetRowset
- IDBSchemaRowsetImpl::GetRowset
- ATL::IDBSchemaRowsetImpl<SessionClass>::GetRowset
- GetRowset
- ATL::IDBSchemaRowsetImpl::GetSchemas
- GetSchemas
- IDBSchemaRowsetImpl<SessionClass>::GetSchemas
- ATL.IDBSchemaRowsetImpl.GetSchemas
- ATL::IDBSchemaRowsetImpl<SessionClass>::GetSchemas
- IDBSchemaRowsetImpl.GetSchemas
- IDBSchemaRowsetImpl::GetSchemas
helpviewer_keywords:
- IDBSchemaRowsetImpl class
- CheckRestrictions method
- CreateSchemaRowset method
- SetRestrictions method
- GetRowset method
- GetSchemas method
ms.assetid: bd7bf0d7-a1c6-4afa-88e3-cfdbdf560703
ms.openlocfilehash: d78aa23469cc0fa94498f93e9a6975e0a7c827e9
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509039"
---
# <a name="idbschemarowsetimpl-class"></a>IDBSchemaRowsetImpl-Klasse

Bietet die Implementierung für Schemarowsets.

## <a name="syntax"></a>Syntax

```cpp
template <class SessionClass>
class ATL_NO_VTABLE IDBSchemaRowsetImpl : public IDBSchemaRowset
```

### <a name="parameters"></a>Parameter

*Sessionclass*<br/>
Die Klasse, mit der `IDBSchemaRowsetImpl` geerbt wird. Diese Klasse ist in der Regel die Sitzungsklasse des Benutzers.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** „atldb.h“

## <a name="members"></a>Members

### <a name="methods"></a>Methoden

| Name | Beschreibung |
|-|-|
|[CheckRestrictions](#checkrestrictions)|Überprüft die Gültigkeit von Einschränkungen für ein Schemarowset.|
|[CreateSchemaRowset](#createschemarowset)|Implementiert eine COM-Objekterstellerfunktion für das mit dem Vorlagenparameter angegebene Objekt.|
|[SetRestrictions](#setrestrictions)|Gibt an, welche Einschränkungen Sie für ein bestimmtes Schemarowset unterstützen.|

### <a name="interface-methods"></a>Schnittstellenmethoden

| Name | Beschreibung |
|-|-|
|[GetRowset](#getrowset)|Gibt ein Schemarowset zurück.|
|[GetSchemas](#getschemas)|Gibt eine Liste der Schemarowsets zurück, auf die [IDBSchemaRowsetImpl::GetRowset](#getrowset)zugreifen kann.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse implementiert die [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) -Schnittstelle und die vorlagenbasierte Erstellerfunktion [CreateSchemaRowset](#createschemarowset).

OLE DB verwendet die Schemarowsets, um Daten zu den Daten in einem Anbieter zurückzugeben. Solche Daten werden häufig als „Metadaten“ bezeichnet. Standardmäßig muss ein Anbieter immer `DBSCHEMA_TABLES` , und unterstützen `DBSCHEMA_COLUMNS` `DBSCHEMA_PROVIDER_TYPES` , wie in [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) in der *OLE DB Programmierer-Referenz*beschrieben. Schemarowsets werden in einer Schemazuordnung festgelegt. Informationen zu den Schemazuordnungseinträgen finden Sie unter [SCHEMA_ENTRY](./macros-for-ole-db-provider-templates.md#schema_entry).

Der OLE DB-Anbieterassistent im ATL-Objektassistenten generiert automatisch Code für die Schemarowsets in Ihrem Projekt. (Standardmäßig unterstützt der Assistent die zuvor erwähnten obligatorischen Schemarowsets.) Wenn Sie einen Consumer mit dem ATL-Objekt-Assistenten erstellen, verwendet der Assistent Schemarowsets, um die richtigen Daten an einen Anbieter zu binden. Wenn Sie die Schemarowsets nicht implementieren, um die richtigen Metadaten bereitzustellen, bindet der Assistent nicht die richtigen Daten.

Informationen über die Unterstützung für Schemarowsets in Ihrem Anbieter finden Sie unter [Supporting Schema Rowsets](../../data/oledb/supporting-schema-rowsets.md)(Unterstützen von Schemarowsets).

Weitere Informationen zu Schemarowsets finden Sie unter [Schema Rowsets](/previous-versions/windows/desktop/ms712921(v=vs.85)) (Schemarowsets) in der *OLE DB-Programmiererreferenz*.

## <a name="idbschemarowsetimplcheckrestrictions"></a><a name="checkrestrictions"></a> Idbschemarowabtimpl:: Check Restrictions

Überprüft die Gültigkeit von Einschränkungen für ein Schemarowset.

### <a name="syntax"></a>Syntax

```cpp
HRESULT CheckRestrictions(REFGUID rguidSchema,
   ULONG cRestrictions,  const VARIANT rgRestrictions[]);
```

#### <a name="parameters"></a>Parameter

*rguidschema*<br/>
[in] Ein Verweis auf die angeforderte Schemarowset-GUID (z. B. `DBSCHEMA_TABLES`).

*cRestrictions*<br/>
[in] Die Anzahl der Einschränkungen, die der Consumer für das Schemarowset übergeben hat.

*rgrestriktionen*<br/>
[in] Ein Längenarray von *cRestrictions* von festzulegenden Einschränkungswerten. Weitere Informationen finden [Sie in der](#setrestrictions)Beschreibung des *rgRestrictions* -Parameters in "".

### <a name="remarks"></a>Bemerkungen

Verwenden Sie `CheckRestrictions` , um die Gültigkeit von Einschränkungen für ein Schemarowset zu überprüfen. Es überprüft die Einschränkungen für die `DBSCHEMA_TABLES` `DBSCHEMA_COLUMNS` `DBSCHEMA_PROVIDER_TYPES` Schemarowsets, und. Nennen Sie ihn, um zu bestimmen, ob der-Rückruf eines Consumers `IDBSchemaRowset::GetRowset` korrekt ist. Wenn Sie andere als die oben aufgeführten Schemarowsets unterstützen möchten, sollten Sie Ihre eigene Funktion zum Ausführen dieser Aufgabe erstellen.

`CheckRestrictions` bestimmt, ob der Consumer [GetRowset](#getrowset) mit der richtigen Einschränkung und dem richtigen Einschränkungstyp (z. b. einer VT_BSTR für eine Zeichenfolge), die der Anbieter unterstützt, anruft. Es bestimmt außerdem, ob die richtige Anzahl von Einschränkungen unterstützt werden. Standardmäßig fragt `CheckRestrictions` den Anbieter mittels des Aufrufs von [SetRestrictions](#setrestrictions) , welche Einschränkungen für ein angegebenes Rowset unterstützt werden. Es vergleicht dann die Einschränkungen vom Consumer mit den vom Anbieter unterstützten, wobei der Vergleich entweder erfolgreich ist oder fehlschlägt.

Weitere Informationen zu [Schemarowsets finden Sie unter IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) in der *OLE DB-Programmier Referenz* im Windows SDK.

## <a name="idbschemarowsetimplcreateschemarowset"></a><a name="createschemarowset"></a> IDBSchemaRowsetImpl:: kreateschemarowset

Implementiert eine COM-Objekterstellerfunktion für das mit dem Vorlagenparameter angegebene Objekt.

### <a name="syntax"></a>Syntax

```cpp
template template <class SchemaRowsetClass>
HRESULT CreateSchemaRowset(IUnknown *pUnkOuter,
   ULONG cRestrictions,
   const VARIANT rgRestrictions[],
   REFIID riid,
   ULONG cPropertySets,
   DBPROPSET rgPropertySets[],
   IUnknown** ppRowset,
   SchemaRowsetClass*& pSchemaRowset);
```

#### <a name="parameters"></a>Parameter

*pUnkOuter*<br/>
in Ein äußeres [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) beim aggregierten, andernfalls NULL.

*cRestrictions*<br/>
[in] Die Anzahl der Einschränkungen für das Schemarowset.

*rgrestriktionen*<br/>
[in] Ein Array auf das Rowset anzuwendender `cRestrictions`**VARIANT**en.

*riid*<br/>
in Die Schnittstelle zu [QueryInterface](../../atl/queryinterface.md) für in der Ausgabe `IUnknown` .

*cPropertySets*<br/>
[in] Die Anzahl der festzulegenden Eigenschaftensätze.

*rgPropertySets*<br/>
[in] Ein Array von [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) -Strukturen, die die festzulegenden Eigenschaften angeben.

*ppRowset*<br/>
vorgenommen Der `IUnknown` von *riid*angeforderte ausgehende. Dies `IUnknown` ist eine Schnittstelle für das Schemarowsetobjekt.

*pschemarowset*<br/>
[out] Ein Zeiger auf eine Instanz der Schemarowsetklasse. Dieser Parameter wird in der Regel nicht verwendet, kann jedoch verwendet werden, wenn Sie mehr Arbeit in das Schemarowset investieren müssen, bevor Sie es einem COM-Objekt übergeben. Die Lebensdauer von *pschemarowset* wird durch *ppRowset*gebunden.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Bemerkungen

Diese Funktion implementiert einen generischen Ersteller für alle Typen von Schemarowsets. In der Regel ruft der Benutzer diese Funktion nicht auf. Sie wird durch die Implementierung der Schemazuordnung aufgerufen.

## <a name="idbschemarowsetimplsetrestrictions"></a><a name="setrestrictions"></a> Idbschemarowabtimpl:: abtrestrictions

Gibt an, welche Einschränkungen Sie für ein bestimmtes Schemarowset unterstützen.

### <a name="syntax"></a>Syntax

```cpp
void SetRestrictions(ULONG cRestrictions,
   GUID* /* rguidSchema */,
   ULONG* rgRestrictions);
```

#### <a name="parameters"></a>Parameter

*cRestrictions*<br/>
in Die Anzahl der Einschränkungen im *rgRestrictions* -Array und die Anzahl von GUIDs im *rguidschema* -Array.

*rguidschema*<br/>
[in] Ein Array von GUIDs der Schemarowsets, für die Einschränkungen abgerufen werden sollen. Jedes Arrayelement enthält die GUID eines Schemarowsets (z. B. `DBSCHEMA_TABLES`).

*rgrestriktionen*<br/>
[in] Ein Längenarray von *cRestrictions* von festzulegenden Einschränkungswerten. Jedes Element entspricht den Einschränkungen für das Schemarowset, das mit der GUID identifiziert wird. Wenn ein Schemarowset nicht vom Anbieter unterstützt wird, wird das Element auf 0 (null) festgelegt. Andernfalls enthält der **ULONG** -Wert eine Bitmaske, die die Einschränkungen darstellt, die für dieses Schemarowset unterstützt werden. Weitere Informationen darüber, welche Einschränkungen einem bestimmten Schemarowset entsprechen, finden Sie in der Tabelle der [Schemarowset-GUIDs in IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) in der *OLE DB Programmierer-Referenz* im Windows SDK.

### <a name="remarks"></a>Bemerkungen

Das- `IDBSchemaRowset` Objekt ruft `SetRestrictions` auf, um zu bestimmen, welche Einschränkungen Sie für ein bestimmtes Schemarowset unterstützen (es wird von [GetSchemas](#getschemas) über einen upcasted-Zeiger aufgerufen). Einschränkungen ermöglichen es Consumern, nur die übereinstimmende Zeilen abzurufen (z. B. Suche nach allen Spalten in der Tabelle „MyTable“). Einschränkungen sind optional, und wenn keine unterstützt werden (Standardeinstellung), werden immer alle Daten zurückgegeben.

Die Standard Implementierung dieser Methode legt die *rgRestrictions* -Array Elemente auf 0 fest. Überschreiben Sie die Standardeinstellung in Ihrer Sitzungsklasse, um Einschränkungen festzulegen, die vom Standard abweichen.

Informationen zum Implementieren der Schemarowset-Unterstützung finden Sie unter [Unterstützen von Schemarowsets](../../data/oledb/supporting-schema-rowsets.md).

Ein Beispiel für einen Anbieter, der Schemarowsets unterstützt, finden Sie unter dem Beispiel [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) .

Weitere Informationen zu [Schemarowsets finden Sie unter IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) in der *OLE DB-Programmier Referenz* im Windows SDK.

## <a name="idbschemarowsetimplgetrowset"></a><a name="getrowset"></a> IDBSchemaRowsetImpl:: GetRowset

Gibt ein Schemarowset zurück.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD (GetRowset)(IUnknown *pUnkOuter,
   REFGUID rguidSchema,
   ULONG cRestrictions,
   const VARIANT rgRestrictions[],
   REFIID riid,
   ULONG cPropertySets,
   DBPROPSET rgPropertySets[],
   IUnknown **ppRowset);
```

#### <a name="parameters"></a>Parameter

*pUnkOuter*<br/>
in Ein äußerer `IUnknown` beim aggregierten; andernfalls NULL.

*rguidschema*<br/>
[in] Ein Verweis auf die angeforderte Schemarowset-GUID (z. B. `DBSCHEMA_TABLES`).

*cRestrictions*<br/>
[in] Die Anzahl der Einschränkungen, die auf das Schemarowset angewendet werden sollen.

*rgrestriktionen*<br/>
[in] Ein Array von `cRestrictions`**VARIANT**s, die die Einschränkungen darstellen.

*riid*<br/>
[in] Die anzufordernde IID des neu erstellten Schemarowsets.

*cPropertySets*<br/>
[in] Die Anzahl der festzulegenden Eigenschaftensätze.

*rgPropertySets*<br/>
[in/out] Ein Array von [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) -Strukturen, die für das neu erstellte Schemarowset festgelegt werden sollen.

*ppRowset*<br/>
[out] Ein Zeiger auf die angeforderte Schnittstelle für das neu erstellte Schemarowset.

### <a name="remarks"></a>Bemerkungen

Für diese Methode muss der Benutzer eine Schemazuordnung in der Sitzungsklasse haben. Erstellt mithilfe der Schema Zuordnungs Informationen ein angegebenes `GetRowset` Rowsetobjekt, wenn der *rguidschema* -Parameter mit einem der Karten Einträge-GUIDs identisch ist. Unter [SCHEMA_ENTRY](./macros-for-ole-db-provider-templates.md#schema_entry) finden Sie eine Beschreibung des Zuordnungseintrags.

Siehe [IDBSchemaRowset:: GetRowset](/previous-versions/windows/desktop/ms722634(v=vs.85)) im Windows SDK.

## <a name="idbschemarowsetimplgetschemas"></a><a name="getschemas"></a> Idbschemarowabtimpl:: GetSchemas

Gibt eine Liste der Schemarowsets zurück, auf die [IDBSchemaRowsetImpl::GetRowset](#getrowset)zugreifen kann.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD (GetSchema s )(ULONG * pcSchemas,
   GUID ** prgSchemas,
   ULONG** prgRest);
```

#### <a name="parameters"></a>Parameter

*pcSchemas*<br/>
[out] Ein Zeiger auf eine **ULONG** , die mit der Anzahl von Schemas gefüllt ist.

*prgSchemas*<br/>
[out] Ein Zeiger auf ein Array von GUIDs, das mit einem Zeiger auf ein Array von Schemarowset-GUIDs gefüllt ist.

*prgRest*<br/>
[out] Ein Zeiger auf ein Array von **ULONG**s, das mit dem Einschränkungsarray gefüllt werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Methode gibt ein Array aller Schemarowsets zurück, die vom Anbieter unterstützt werden. Weitere Informationen finden Sie im Windows SDK unter [IDBSchemaRowset:: GetSchemas](/previous-versions/windows/desktop/ms719605(v=vs.85)) .

Für die Implementierung dieser Funktion muss der Benutzer eine Schemazuordnung in der Sitzungsklasse haben. Mithilfe der Schemazuordnungsinformationen antwortet die Funktion dann mit dem Array von GUIDs für die Schemas in der Zuordnung. Dies stellt die Schemas dar, die vom Anbieter unterstützt werden.

## <a name="see-also"></a>Weitere Informationen

[Schemarowset-Klassen und typedef-Klassen](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)<br/>
[Unterstützen von Schemarowsets](../../data/oledb/supporting-schema-rowsets.md)<br/>
[SCHEMA_ENTRY](./macros-for-ole-db-provider-templates.md#schema_entry)<br/>
[UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider)
