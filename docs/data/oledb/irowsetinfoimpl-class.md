---
title: IRowsetInfoImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- ATL.IRowsetInfoImpl
- IRowsetInfoImpl
- ATL::IRowsetInfoImpl
- ATL.IRowsetInfoImpl.GetProperties
- IRowsetInfoImpl.GetProperties
- ATL::IRowsetInfoImpl::GetProperties
- IRowsetInfoImpl::GetProperties
- ATL::IRowsetInfoImpl::GetReferencedRowset
- GetReferencedRowset
- ATL.IRowsetInfoImpl.GetReferencedRowset
- IRowsetInfoImpl.GetReferencedRowset
- IRowsetInfoImpl::GetReferencedRowset
- IRowsetInfoImpl::GetSpecification
- ATL.IRowsetInfoImpl.GetSpecification
- IRowsetInfoImpl.GetSpecification
- GetSpecification
- ATL::IRowsetInfoImpl::GetSpecification
helpviewer_keywords:
- IRowsetInfoImpl class
- GetProperties method
- GetReferencedRowset method
- GetSpecification method
ms.assetid: 9c654155-7727-464e-bd31-143e68391a47
ms.openlocfilehash: 691871bfc4a9e63167611a3228807fb12e32d1cb
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077866"
---
# <a name="irowsetinfoimpl-class"></a>IRowsetInfoImpl-Klasse

Stellt eine Implementierung für die [IRow-tinfo](/previous-versions/windows/desktop/ms724541(v=vs.85)) -Schnittstelle bereit.

## <a name="syntax"></a>Syntax

```cpp
template <class T, class PropClass = T>
class ATL_NO_VTABLE IRowsetInfoImpl :
   public IRowsetInfo,
   public CUtlProps<PropClass>
```

### <a name="parameters"></a>Parameter

*T*<br/>
Die von `IRowsetInfoImpl`abgeleitete Klasse.

*Propclass*<br/>
Eine benutzerdefinierbare Eigenschaften Klasse, bei der es sich standardmäßig um *T*handelt.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** altdb. h

## <a name="members"></a>Members

### <a name="interface-methods"></a>Schnittstellenmethoden

|||
|-|-|
|[GetProperties](#getproperties)|Gibt die aktuellen Einstellungen aller vom Rowset unterstützten Eigenschaften zurück.|
|[GetReferencedRowset](#getreferencedrowset)|Gibt einen Schnittstellen Zeiger auf das Rowset zurück, für das ein Lesezeichen gilt.|
|[GetSpecification](#getspecification)|Gibt einen Schnittstellenzeiger auf das Objekt (Befehl oder Sitzung) zurück, das dieses Rowset erstellt hat.|

## <a name="remarks"></a>Bemerkungen

Eine erforderliche Schnittstelle für Rowsets. Diese Klasse implementiert die Rowseteigenschaften mithilfe der in der Befehls Klasse definierten Eigenschaften [Satz](../../data/oledb/begin-propset-map.md) Zuordnung. Obwohl die Rowsetklasse anscheinend die Eigenschaften Sätze der Befehls Klasse verwendet, wird das Rowset mit einer eigenen Kopie der Lauf Zeiteigenschaften bereitgestellt, wenn es von einem Befehl oder einem Sitzungs Objekt erstellt wird.

## <a name="irowsetinfoimplgetproperties"></a><a name="getproperties"></a>Irowctinfoimpl:: GetProperties

Gibt die aktuellen Einstellungen für Eigenschaften in der `DBPROPSET_ROWSET` Gruppe zurück.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD (GetProperties )(const ULONG cPropertyIDSets,
   const DBPROPIDSET rgPropertyIDSets[],
   ULONG* pcPropertySets,
   DBPROPSET** prgPropertySets);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [irowctinfo:: GetProperties](/previous-versions/windows/desktop/ms719611(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

## <a name="irowsetinfoimplgetreferencedrowset"></a><a name="getreferencedrowset"></a>Irowsetinfoimpl:: GetReferencedRowset

Gibt einen Schnittstellen Zeiger auf das Rowset zurück, für das ein Lesezeichen gilt.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD (GetReferencedRowset )(DBORDINAL iOrdinal,
   REFIID riid,
   IUnknown** ppReferencedRowset);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [IRowsetInfo:: GetReferencedRowset](/previous-versions/windows/desktop/ms721145(v=vs.85)) in der *OLE DB-Programmier Referenz*. Der *iOrdinal* -Parameter muss eine Lesezeichen Spalte sein.

## <a name="irowsetinfoimplgetspecification"></a><a name="getspecification"></a>Irowantinfoimpl:: GetSpecification

Gibt einen Schnittstellenzeiger auf das Objekt (Befehl oder Sitzung) zurück, das dieses Rowset erstellt hat.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD (GetSpecification )(REFIID riid,
   IUnknown** ppSpecification);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [irowctinfo:: GetSpecification](/previous-versions/windows/desktop/ms716746(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode mit [igetdatasourceimpl](../../data/oledb/igetdatasourceimpl-class.md) zum Abrufen von Eigenschaften aus dem Datenquellen Objekt.

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektur von OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-template-architecture.md)