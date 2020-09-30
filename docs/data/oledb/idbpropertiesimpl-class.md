---
title: IDBPropertiesImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- IDBPropertiesImpl
- ATL.IDBPropertiesImpl
- ATL.IDBPropertiesImpl<T>
- ATL::IDBPropertiesImpl<T>
- ATL::IDBPropertiesImpl
- IDBPropertiesImpl::GetProperties
- IDBPropertiesImpl.GetProperties
- IDBPropertiesImpl::GetPropertyInfo
- IDBPropertiesImpl.GetPropertyInfo
- GetPropertyInfo
- IDBPropertiesImpl.SetProperties
- IDBPropertiesImpl::SetProperties
helpviewer_keywords:
- IDBPropertiesImpl class
- GetProperties method
- GetPropertyInfo method
- SetProperties method
ms.assetid: a7f15a8b-95b2-4316-b944-d5d03f8d74ab
ms.openlocfilehash: d94c5d121386989d223a55b8ce7626444c3f8950
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509064"
---
# <a name="idbpropertiesimpl-class"></a>IDBPropertiesImpl-Klasse

Stellt eine Implementierung für die- `IDBProperties` Schnittstelle bereit.

## <a name="syntax"></a>Syntax

```cpp
template <class T>
class ATL_NO_VTABLE IDBPropertiesImpl
   : public IDBProperties, public CUtlProps<T>
```

### <a name="parameters"></a>Parameter

*T*<br/>
Die von abgeleitete Klasse `IDBPropertiesImpl` .

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** „atldb.h“

## <a name="members"></a>Members

### <a name="interface-methods"></a>Schnittstellenmethoden

| Name | Beschreibung |
|-|-|
|[GetProperties](#getproperties)|Gibt die Werte der Eigenschaften in der Datenquelle, Datenquellen Informationen und Initialisierungs Eigenschaften Gruppen zurück, die derzeit für das Datenquellen Objekt festgelegt sind, oder die Werte der Eigenschaften in der Initialisierungs Eigenschaften Gruppe, die derzeit für den Enumerator festgelegt sind.|
|[GetPropertyInfo](#getpropertyinfo)|Gibt Informationen zu allen Eigenschaften zurück, die vom Anbieter unterstützt werden.|
|[SetProperties](#setproperties)|Legt Eigenschaften in den Eigenschaften Gruppendaten Quelle und Initialisierung für Datenquellen Objekte oder die Initialisierungs Eigenschaften Gruppe für Enumeratoren fest.|

## <a name="remarks"></a>Bemerkungen

[IDBProperties](/previous-versions/windows/desktop/ms719607(v=vs.85)) ist eine erforderliche Schnittstelle für Datenquellen Objekte und eine optionale Schnittstelle für Enumeratoren. Wenn jedoch ein Enumerator [IDBInitialize](/previous-versions/windows/desktop/ms713706(v=vs.85))verfügbar macht, muss er verfügbar machen `IDBProperties` . `IDBPropertiesImpl` implementiert, `IDBProperties` indem eine durch [BEGIN_PROPSET_MAP](./macros-for-ole-db-provider-templates.md#begin_propset_map)definierte statische Funktion verwendet wird.

## <a name="idbpropertiesimplgetproperties"></a><a name="getproperties"></a> Idbpropertiesimpl:: GetProperties

Gibt die Werte der Eigenschaften in der Datenquelle, Datenquellen Informationen und Initialisierungs Eigenschaften Gruppen zurück, die derzeit für das Datenquellen Objekt festgelegt sind, oder die Werte der Eigenschaften in der Initialisierungs Eigenschaften Gruppe, die derzeit für den Enumerator festgelegt sind.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD(GetProperties)(ULONG cPropertySets,
   const DBPROPIDSET rgPropertySets[],
   ULONG * pcProperties,
   DBPROPSET ** prgProperties);
```

#### <a name="parameters"></a>Parameter

Siehe [IDBProperties:: GetProperties](/previous-versions/windows/desktop/ms714344(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

Einige Parameter entsprechen *OLE DB Programmier Verweis* Parametern mit unterschiedlichen Namen, die in beschrieben werden `IDBProperties::GetProperties` :

|Parameter für OLE DB Vorlage|*Verweis Parameter für OLE DB Programmierer*|
|--------------------------------|------------------------------------------------|
|*cPropertySets*|*cpropertyidsets*|
|*rgPropertySets*|*rgPropertyIDSets*|
|*pcProperties*|*pcpropertysets*|
|*prgproperties*|*prgPropertySets*|

### <a name="remarks"></a>Bemerkungen

Wenn der Anbieter initialisiert wird, gibt diese Methode die Werte der Eigenschaften in den Eigenschaften Gruppen DBPROPSET_DATASOURCE, DBPROPSET_DATASOURCEINFO DBPROPSET_DBINIT, die derzeit für das Datenquellen Objekt festgelegt sind. Wenn der Anbieter nicht initialisiert ist, werden nur DBPROPSET_DBINIT Gruppen Eigenschaften zurückgegeben.

## <a name="idbpropertiesimplgetpropertyinfo"></a><a name="getpropertyinfo"></a> Idbpropertiesimpl:: GetPropertyInfo

Gibt Eigenschaften Informationen zurück, die von der Datenquelle unterstützt werden.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD(GetPropertyInfo)(ULONG cPropertySets,
   const DBPROPIDSET rgPropertySets[],
   ULONG * pcPropertyInfoSets,
   DBPROPINFOSET ** prgPropertyInfoSets,
   OLECHAR ** ppDescBuffer);
```

#### <a name="parameters"></a>Parameter

Siehe [IDBProperties:: GetPropertyInfo](/previous-versions/windows/desktop/ms718175(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

Einige Parameter entsprechen *OLE DB Programmier Verweis* Parametern mit unterschiedlichen Namen, die in beschrieben werden `IDBProperties::GetPropertyInfo` :

|Parameter für OLE DB Vorlage|*Verweis Parameter für OLE DB Programmierer*|
|--------------------------------|------------------------------------------------|
|*cPropertySets*|*cpropertyidsets*|
|*rgPropertySets*|*rgPropertyIDSets*|

### <a name="remarks"></a>Bemerkungen

Verwendet [idbinitializeimpl:: m_pCUtlPropInfo](./idbinitializeimpl-class.md#pcutlpropinfo) , um diese Funktion zu implementieren.

## <a name="idbpropertiesimplsetproperties"></a><a name="setproperties"></a> Idbpropertiesimpl:: SetProperties

Legt Eigenschaften in den Eigenschaften Gruppendaten Quelle und Initialisierung für Datenquellen Objekte oder die Initialisierungs Eigenschaften Gruppe für Enumeratoren fest.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets,
   DBPROPSET rgPropertySets[]);
```

#### <a name="parameters"></a>Parameter

Siehe [IDBProperties:: SetProperties](/previous-versions/windows/desktop/ms723049(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

### <a name="remarks"></a>Bemerkungen

Wenn der Anbieter initialisiert wird, legt diese Methode die Werte der Eigenschaften in den DBPROPSET_DATASOURCE-, DBPROPSET_DATASOURCEINFO DBPROPSET_DBINIT-Eigenschaften Gruppen für das Datenquellen Objekt fest. Wenn der Anbieter nicht initialisiert ist, werden nur DBPROPSET_DBINIT Gruppen Eigenschaften festgelegt.

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektur der OLE DB-Anbieter Vorlage](../../data/oledb/ole-db-provider-template-architecture.md)
