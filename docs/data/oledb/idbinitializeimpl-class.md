---
title: IDBInitializeImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- ATL.IDBInitializeImpl<T>
- ATL::IDBInitializeImpl<T>
- IDBInitializeImpl
- ATL::IDBInitializeImpl
- ATL.IDBInitializeImpl
- IDBInitializeImpl.IDBInitializeImpl
- IDBInitializeImpl::IDBInitializeImpl
- Initialize
- IDBInitializeImpl::Initialize
- IDBInitializeImpl.Initialize
- IDBInitializeImpl.Uninitialize
- Uninitialize
- IDBInitializeImpl::Uninitialize
- ATL::IDBInitializeImpl::m_dwStatus
- IDBInitializeImpl.m_dwStatus
- ATL.IDBInitializeImpl.m_dwStatus
- IDBInitializeImpl::m_dwStatus
- IDBInitializeImpl<T>::m_dwStatus
- ATL.IDBInitializeImpl<T>.m_dwStatus
- ATL::IDBInitializeImpl<T>::m_dwStatus
- m_dwStatus
- ATL::IDBInitializeImpl<T>::m_pCUtlPropInfo
- m_pCUtlPropInfo
- IDBInitializeImpl::m_pCUtlPropInfo
- ATL.IDBInitializeImpl.m_pCUtlPropInfo
- IDBInitializeImpl<T>::m_pCUtlPropInfo
- IDBInitializeImpl.m_pCUtlPropInfo
- ATL::IDBInitializeImpl::m_pCUtlPropInfo
helpviewer_keywords:
- IDBInitializeImpl class
- IDBInitializeImpl constructor
- Initialize method
- Uninitialize method
- m_dwStatus
- m_pCUtlPropInfo
ms.assetid: e4182f81-0443-44f5-a0d3-e7e075d6f883
ms.openlocfilehash: aff02e812d2806201a08164aeb4a8ef290550725
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845535"
---
# <a name="idbinitializeimpl-class"></a>IDBInitializeImpl-Klasse

Stellt eine Implementierung für die [IDBInitialize](/previous-versions/windows/desktop/ms713706(v=vs.85)) -Schnittstelle bereit.

## <a name="syntax"></a>Syntax

```cpp
template <class T>
class ATL_NO_VTABLE IDBInitializeImpl : public IDBInitialize
```

### <a name="parameters"></a>Parameter

*T*<br/>
Die von abgeleitete Klasse `IDBInitializeImpl` .

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** „atldb.h“

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

| Name | Beschreibung |
|-|-|
|[IDBInitializeImpl](#idbinitializeimpl)|Der Konstruktor.|

### <a name="interface-methods"></a>Schnittstellenmethoden

| Name | Beschreibung |
|-|-|
|[Initialisieren](#initialize)|Startet den Anbieter.|
|[Uninitialize](#uninitialize)|Beendet den Anbieter.|

### <a name="data-members"></a>Datenelemente

| Name | Beschreibung |
|-|-|
|[m_dwStatus](#dwstatus)|Datenquellenflags.|
|[m_pCUtlPropInfo](#pcutlpropinfo)|Ein Zeiger auf die Implementierung von DB-Eigenschaften Informationen.|

## <a name="remarks"></a>Bemerkungen

Eine erforderliche Schnittstelle für Datenquellen Objekte und eine optionale Schnittstelle für Enumeratoren.

## <a name="idbinitializeimplidbinitializeimpl"></a><a name="idbinitializeimpl"></a> Idbinitializeimpl:: idbinitializeimpl

Der Konstruktor.

### <a name="syntax"></a>Syntax

```cpp
IDBInitializeImpl();
```

### <a name="remarks"></a>Bemerkungen

Initialisiert alle Datenmember.

## <a name="idbinitializeimplinitialize"></a><a name="initialize"></a> Idbinitializeimpl:: Initialize

Initialisiert das Datenquellen Objekt, indem seine Eigenschafts Unterstützung vorbereitet wird.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD(Initialize)(void);
```

### <a name="remarks"></a>Bemerkungen

Siehe [IDBInitialize:: Initialize](/previous-versions/windows/desktop/ms718026(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

## <a name="idbinitializeimpluninitialize"></a><a name="uninitialize"></a> Idbinitializeimpl:: Uninitialize

Fügt das Datenquellen Objekt in einen nicht initialisierten Zustand ein, indem interne Ressourcen wie z. b. die Eigenschafts Unterstützung freigegeben werden.

### <a name="syntax"></a>Syntax

```cpp
STDMETHOD(Uninitialize)(void);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [IDBInitialize:: Uninitialize](/previous-versions/windows/desktop/ms719648(v=vs.85)) in der *OLE DB Programmierer-Referenz*.

## <a name="idbinitializeimplm_dwstatus"></a><a name="dwstatus"></a> Idbinitializeimpl:: m_dwStatus

Datenquellenflags.

### <a name="syntax"></a>Syntax

```cpp
DWORD m_dwStatus;
```

### <a name="remarks"></a>Bemerkungen

Diese Flags geben den Status verschiedener Attribute für das Datenquellen Objekt an oder geben ihn an. Enthält einen oder mehrere der folgenden **`enum`** Werte:

```cpp
enum DATASOURCE_FLAGS {
    DSF_MASK_INIT     = 0xFFFFF00F,
    DSF_PERSIST_DIRTY = 0x00000001,
    DSF_INITIALIZED   = 0x00000010,
};
```

| Wert | Beschreibung |
|-|-|
|`DSF_MASK_INIT`|Eine Maske, die die Wiederherstellung des nicht initialisierten Zustands ermöglicht.|
|`DSF_PERSIST_DIRTY`|Legen Sie fest, ob das Datenquellen Objekt Persistenz erfordert (d. h., wenn Änderungen vorgenommen wurden).|
|`DSF_INITIALIZED`|Legen Sie fest, ob die Datenquelle initialisiert wurde.|

## <a name="idbinitializeimplm_pcutlpropinfo"></a><a name="pcutlpropinfo"></a> Idbinitializeimpl:: m_pCUtlPropInfo

Ein Zeiger auf das Implementierungs Objekt für Informationen zu Daten Bank Eigenschaften.

### <a name="syntax"></a>Syntax

```cpp
CUtlPropInfo< T >* m_pCUtlPropInfo;
```

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektur der OLE DB-Anbieter Vorlage](../../data/oledb/ole-db-provider-template-architecture.md)
