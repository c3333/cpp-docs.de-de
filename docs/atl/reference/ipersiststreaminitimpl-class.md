---
title: IPersistStreamInitImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- IPersistStreamInitImpl
- ATLCOM/ATL::IPersistStreamInitImpl
- ATLCOM/ATL::IPersistStreamInitImpl::GetClassID
- ATLCOM/ATL::IPersistStreamInitImpl::GetSizeMax
- ATLCOM/ATL::IPersistStreamInitImpl::InitNew
- ATLCOM/ATL::IPersistStreamInitImpl::IsDirty
- ATLCOM/ATL::IPersistStreamInitImpl::Load
- ATLCOM/ATL::IPersistStreamInitImpl::Save
helpviewer_keywords:
- IPersistStreamInit ATL implementation
- IPersistStreamInitImpl class
- streams, ATL
ms.assetid: ef217c3c-020f-4cf8-871e-ef68e57865b8
ms.openlocfilehash: 0d6ac4639ac0cfb97416ca80b7a2ec3903d7b8e6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326459"
---
# <a name="ipersiststreaminitimpl-class"></a>IPersistStreamInitImpl-Klasse

Diese Klasse `IUnknown` implementiert und stellt eine Standardimplementierung der [IPersistStreamInit-Schnittstelle](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) bereit.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template<class T>
class ATL_NO_VTABLE IPersistStreamInitImpl
   : public IPersistStreamInit
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Ihre Klasse, `IPersistStreamInitImpl`abgeleitet von .

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IPersistStreamInitImpl::GetClassID](#getclassid)|Ruft die CLSID des Objekts ab.|
|[IPersistStreamInitImpl::GetSizeMax](#getsizemax)|Ruft die Größe des Streams ab, der zum Speichern der Objektdaten erforderlich ist. Die ATL-Implementierung gibt E_NOTIMPL zurück.|
|[IPersistStreamInitImpl::InitNeu](#initnew)|Initialisiert ein neu erstelltes Objekt.|
|[IPersistStreamInitImpl::IsDirty](#isdirty)|Überprüft, ob sich die Daten des Objekts seit dem letzten Speichern geändert haben.|
|[IPersistStreamInitImpl::Laden](#load)|Lädt die Eigenschaften des Objekts aus dem angegebenen Stream.|
|[IPersistStreamInitImpl::Speichern](#save)|Speichert die Eigenschaften des Objekts im angegebenen Stream.|

## <a name="remarks"></a>Bemerkungen

Die [IPersistStreamInit-Schnittstelle](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) ermöglicht es einem Client, anzufordern, dass das Objekt seine persistenten Daten lädt und in einem einzelnen Stream speichert. Die `IPersistStreamInitImpl` Klasse stellt eine Standardimplementierung `IUnknown` dieser Schnittstelle bereit und implementiert, indem Informationen in Debugbuilds an das Dumpgerät gesendet werden.

**Verwandte Artikel** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Erstellen eines [ATL-Projekts](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IPersistStreamInit`

`IPersistStreamInitImpl`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="ipersiststreaminitimplgetclassid"></a><a name="getclassid"></a>IPersistStreamInitImpl::GetClassID

Ruft die CLSID des Objekts ab.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>Bemerkungen

Siehe [IPersist::GetClassID](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid) im Windows SDK.

## <a name="ipersiststreaminitimplgetsizemax"></a><a name="getsizemax"></a>IPersistStreamInitImpl::GetSizeMax

Ruft die Größe des Streams ab, der zum Speichern der Objektdaten erforderlich ist.

```
STDMETHOD(GetSizeMax)(ULARGE_INTEGER FAR* pcbSize);
```

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

### <a name="remarks"></a>Bemerkungen

Siehe [IPersistStreamInit::GetSizeMax](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-getsizemax) im Windows SDK.

## <a name="ipersiststreaminitimplinitnew"></a><a name="initnew"></a>IPersistStreamInitImpl::InitNeu

Initialisiert ein neu erstelltes Objekt.

```
STDMETHOD(InitNew)();
```

### <a name="remarks"></a>Bemerkungen

Siehe [IPersistStreamInit::InitNew](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-initnew) im Windows SDK.

## <a name="ipersiststreaminitimplisdirty"></a><a name="isdirty"></a>IPersistStreamInitImpl::IsDirty

Überprüft, ob sich die Daten des Objekts seit dem letzten Speichern geändert haben.

```
STDMETHOD(IsDirty)();
```

### <a name="remarks"></a>Bemerkungen

Siehe [IPersistStreamInit::IsDirty](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-isdirty) im Windows SDK.

## <a name="ipersiststreaminitimplload"></a><a name="load"></a>IPersistStreamInitImpl::Laden

Lädt die Eigenschaften des Objekts aus dem angegebenen Stream.

```
STDMETHOD(Load)(LPSTREAM pStm);
```

### <a name="remarks"></a>Bemerkungen

ATL verwendet die Eigenschaftenzuordnung des Objekts, um diese Informationen abzurufen.

Siehe [IPersistStreamInit::Load](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-load) im Windows SDK.

## <a name="ipersiststreaminitimplsave"></a><a name="save"></a>IPersistStreamInitImpl::Speichern

Speichert die Eigenschaften des Objekts im angegebenen Stream.

```
STDMETHOD(Save)(LPSTREAM pStm, BOOL fClearDirty);
```

### <a name="remarks"></a>Bemerkungen

ATL verwendet die Eigenschaftenzuordnung des Objekts, um diese Informationen zu speichern.

Siehe [IPersistStreamInit::Speichern](/windows/win32/api/ocidl/nf-ocidl-ipersiststreaminit-save) im Windows SDK.

## <a name="see-also"></a>Siehe auch

[Speicher und Streams](/windows/win32/Stg/storages-and-streams)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
