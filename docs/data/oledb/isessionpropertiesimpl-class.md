---
title: ISessionPropertiesImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- ISessionPropertiesImpl
- ISessionPropertiesImpl::GetProperties
- ISessionPropertiesImpl.GetProperties
- ISessionPropertiesImpl.SetProperties
- ISessionPropertiesImpl::SetProperties
helpviewer_keywords:
- ISessionPropertiesImpl class
- GetProperties method
- SetProperties method
ms.assetid: ca0ba254-c7dc-4c52-abec-cf895a0c6a63
ms.openlocfilehash: d664f32226498326ffb092f1d3248fbdbf614d50
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509759"
---
# <a name="isessionpropertiesimpl-class"></a>ISessionPropertiesImpl-Klasse

Stellt eine Implementierung der [ISessionProperties](/previous-versions/windows/desktop/ms713721(v=vs.85)) -Schnittstelle bereit.

## <a name="syntax"></a>Syntax

```cpp
template <class T, class PropClass = T>
class ATL_NO_VTABLE ISessionPropertiesImpl :
   public ISessionProperties,
   public CUtlProps<PropClass>
```

### <a name="parameters"></a>Parameter

*T*<br/>
Die von abgeleitete Klasse `ISessionPropertiesImpl` .

*Propclass*<br/>
Eine benutzerdefinierbare Eigenschaften Klasse, bei der es sich standardmäßig um *T*handelt.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** „atldb.h“

## <a name="members"></a>Members

### <a name="interface-methods"></a>Schnittstellenmethoden

| Name | Beschreibung |
|-|-|
|[GetProperties](#getproperties)|Gibt die Liste der Eigenschaften in der Sitzungs Eigenschaften Gruppe zurück, die derzeit für die Sitzung festgelegt sind.|
|[SetProperties](#setproperties)|Legt Eigenschaften in der Sitzungs Eigenschaften Gruppe fest.|

## <a name="remarks"></a>Bemerkungen

Eine erforderliche Schnittstelle für Sitzungen. Diese Klasse implementiert Sitzungs Eigenschaften durch Aufrufen einer statischen Funktion, die durch die [Eigenschaften Satz](./macros-for-ole-db-provider-templates.md#begin_propset_map)Zuordnung definiert ist. Die Eigenschaften Satz Zuordnung sollte in ihrer Sitzungs Klasse angegeben werden.

## <a name="isessionpropertiesimplgetproperties"></a><a name="getproperties"></a> Isessionpropertiesimpl:: GetProperties

Gibt die Liste der Eigenschaften in der Eigenschaften `DBPROPSET_SESSION` Gruppe zurück, die derzeit für die Sitzung festgelegt sind.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD(GetProperties)(ULONG cPropertyIDSets,
   const DBPROPIDSET rgPropertyIDSets[],
   ULONG * pcPropertySets,
   DBPROPSET ** prgPropertySets);
```

#### <a name="parameters"></a>Parameter

Siehe [ISessionProperties:: GetProperties](/previous-versions/windows/desktop/ms723643(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

## <a name="isessionpropertiesimplsetproperties"></a><a name="setproperties"></a> Isessionpropertiesimpl:: SetProperties

Legt Eigenschaften in der Eigenschaften `DBPROPSET_SESSION` Gruppe fest.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD(SetProperties)(ULONG cPropertySets,
   DBPROPSET rgPropertySets[]);
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie in der *OLE DB Programmierer-Referenz*unter [ISessionProperties:: SetProperties](/previous-versions/windows/desktop/ms714405(v=vs.85)) .

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektur der OLE DB-Anbieter Vorlage](../../data/oledb/ole-db-provider-template-architecture.md)
