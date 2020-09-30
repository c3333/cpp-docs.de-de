---
title: ICommandPropertiesImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- ICommandPropertiesImpl
- ATL.ICommandPropertiesImpl
- ATL::ICommandPropertiesImpl
- ICommandPropertiesImpl::GetProperties
- ICommandPropertiesImpl.GetProperties
- ICommandPropertiesImpl.SetProperties
- ICommandPropertiesImpl::SetProperties
helpviewer_keywords:
- ICommandPropertiesImpl class
- GetProperties method
- SetProperties method
ms.assetid: b3cf6aea-527e-4f0d-96e0-669178b021a2
ms.openlocfilehash: bd4dd73c79085a2c2d85a5dbacbfd20bc920108e
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501757"
---
# <a name="icommandpropertiesimpl-class"></a>ICommandPropertiesImpl-Klasse

Stellt eine Implementierung der [ICommandProperties](/previous-versions/windows/desktop/ms723044(v=vs.85)) -Schnittstelle bereit.

## <a name="syntax"></a>Syntax

```cpp
template <class T, class PropClass = T>
class ATL_NO_VTABLE ICommandPropertiesImpl
   : public ICommandProperties, public CUtlProps<PropClass>
```

### <a name="parameters"></a>Parameter

*T*<br/>
Ihre Klasse, abgeleitet von

*Propclass*<br/>
Ihre Properties-Klasse.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** „atldb.h“

## <a name="members"></a>Members

### <a name="interface-methods"></a>Schnittstellenmethoden

| Name | Beschreibung |
|-|-|
|[GetProperties](#getproperties)|Gibt die Liste der Eigenschaften in der Rowset-Eigenschaften Gruppe zurück, die derzeit für das Rowset angefordert werden.|
|[SetProperties](#setproperties)|Legt Eigenschaften in der Rowset-Eigenschaften Gruppe fest.|

## <a name="remarks"></a>Bemerkungen

Dies ist für-Befehle obligatorisch. Die-Implementierung wird von einer statischen Funktion bereitgestellt, die durch das [BEGIN_PROPSET_MAP](./macros-for-ole-db-provider-templates.md#begin_propset_map) -Makro definiert wird.

## <a name="icommandpropertiesimplgetproperties"></a><a name="getproperties"></a> Icommandpropertiesimpl:: GetProperties

Gibt alle angeforderten Eigenschaften Sätze zurück, indem die Eigenschaften Zuordnung des Befehls verwendet wird.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD(GetProperties)(const ULONG cPropertyIDSets,
   const DBPROPIDSET rgPropertyIDSets[],
   ULONG * pcPropertySets,
   DBPROPSET ** prgPropertySets);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [ICommandProperties:: GetProperties](/previous-versions/windows/desktop/ms723119(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

### <a name="remarks"></a>Bemerkungen

Siehe [BEGIN_PROPSET_MAP](./macros-for-ole-db-provider-templates.md#begin_propset_map).

## <a name="icommandpropertiesimplsetproperties"></a><a name="setproperties"></a> Icommandpropertiesimpl:: SetProperties

Legt Eigenschaften für das Command-Objekt fest.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets,
   DBPROPSET rgPropertySets[]);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [ICommandProperties:: SetProperties](/previous-versions/windows/desktop/ms711497(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektur der OLE DB-Anbieter Vorlage](../../data/oledb/ole-db-provider-template-architecture.md)
