---
title: IPersistStorageImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- IPersistStorageImpl
- ATLCOM/ATL::IPersistStorageImpl
- ATLCOM/ATL::IPersistStorageImpl::GetClassID
- ATLCOM/ATL::IPersistStorageImpl::HandsOffStorage
- ATLCOM/ATL::IPersistStorageImpl::InitNew
- ATLCOM/ATL::IPersistStorageImpl::IsDirty
- ATLCOM/ATL::IPersistStorageImpl::Load
- ATLCOM/ATL::IPersistStorageImpl::Save
- ATLCOM/ATL::IPersistStorageImpl::SaveCompleted
helpviewer_keywords:
- storage, ATL
- IPersistStorageImpl class
ms.assetid: d652f02c-239c-47c7-9a50-3e9fc3014fff
ms.openlocfilehash: b235b190f237293932705e4d290ac963088722f3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326469"
---
# <a name="ipersiststorageimpl-class"></a>IPersistStorageImpl-Klasse

Diese Klasse implementiert die [IPersistStorage-Schnittstelle.](/windows/win32/api/objidl/nn-objidl-ipersiststorage)

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template <class T>
class ATL_NO_VTABLE IPersistStorageImpl : public IPersistStorage
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Ihre Klasse, `IPersistStorageImpl`abgeleitet von .

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IPersistStorageImpl::GetClassID](#getclassid)|Ruft die CLSID des Objekts ab.|
|[IPersistStorageImpl::HandsOffStorage](#handsoffstorage)|Weist das Objekt an, alle Speicherobjekte freizugeben und in den HandsOff-Modus zu wechseln. Die ATL-Implementierung gibt S_OK zurück.|
|[IPersistStorageImpl::InitNew](#initnew)|Initialisiert einen neuen Speicher.|
|[IPersistStorageImpl::IsDirty](#isdirty)|Überprüft, ob sich die Daten des Objekts seit dem letzten Speichern geändert haben.|
|[IPersistStorageImpl::Laden](#load)|Lädt die Eigenschaften des Objekts aus dem angegebenen Speicher.|
|[IPersistStorageImpl::Speichern](#save)|Speichert die Eigenschaften des Objekts im angegebenen Speicher.|
|[IPersistStorageImpl::SaveCompleted](#savecompleted)|Benachrichtigt ein Objekt, dass es in den Normalmodus zurückkehren kann, um in sein Speicherobjekt zu schreiben. Die ATL-Implementierung gibt S_OK zurück.|

## <a name="remarks"></a>Bemerkungen

`IPersistStorageImpl`implementiert die [IPersistStorage-Schnittstelle,](/windows/win32/api/objidl/nn-objidl-ipersiststorage) die es einem Client ermöglicht, anzufordern, dass das Objekt geladen wird, und seine persistenten Daten mithilfe eines Speichers zu speichern.

Die Implementierung dieser Klasse `T` erfordert, dass `IPersistStreamInit` die Klasse `QueryInterface`eine Implementierung der Schnittstelle über zur Verfügung stellt. In der Regel `T` bedeutet dies, dass die Klasse von [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)ableiten sollte, einen Eintrag für `IPersistStreamInit` in der [COM-Zuordnung](com-map-macros.md)bereitstellen und eine [Eigenschaftenzuordnung](property-map-macros.md) verwenden sollte, um die persistenten Daten der Klasse zu beschreiben.

**Verwandte Artikel** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Erstellen eines [ATL-Projekts](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IPersistStorage`

`IPersistStorageImpl`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="ipersiststorageimplgetclassid"></a><a name="getclassid"></a>IPersistStorageImpl::GetClassID

Ruft die CLSID des Objekts ab.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>Bemerkungen

Siehe [IPersist::GetClassID](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid) im Windows SDK.

## <a name="ipersiststorageimplhandsoffstorage"></a><a name="handsoffstorage"></a>IPersistStorageImpl::HandsOffStorage

Weist das Objekt an, alle Speicherobjekte freizugeben und in den HandsOff-Modus zu wechseln.

```
STDMETHOD(HandsOffStorage)(void);
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Siehe [IPersistStorage::HandsOffStorage](/windows/win32/api/objidl/nf-objidl-ipersiststorage-handsoffstorage) im Windows SDK.

## <a name="ipersiststorageimplinitnew"></a><a name="initnew"></a>IPersistStorageImpl::InitNew

Initialisiert einen neuen Speicher.

```
STDMETHOD(InitNew)(IStorage*);
```

### <a name="remarks"></a>Bemerkungen

Die ATL-Implementierung delegiert die [IPersistStreamInit-Schnittstelle.](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit)

Siehe [IPersistStorage:InitNew](/windows/win32/api/objidl/nf-objidl-ipersiststorage-initnew) im Windows SDK.

## <a name="ipersiststorageimplisdirty"></a><a name="isdirty"></a>IPersistStorageImpl::IsDirty

Überprüft, ob sich die Daten des Objekts seit dem letzten Speichern geändert haben.

```
STDMETHOD(IsDirty)(void);
```

### <a name="remarks"></a>Bemerkungen

Die ATL-Implementierung delegiert die [IPersistStreamInit-Schnittstelle.](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit)

Siehe [IPersistStorage:IsDirty](/windows/win32/api/objidl/nf-objidl-ipersiststorage-isdirty) im Windows SDK.

## <a name="ipersiststorageimplload"></a><a name="load"></a>IPersistStorageImpl::Laden

Lädt die Eigenschaften des Objekts aus dem angegebenen Speicher.

```
STDMETHOD(Load)(IStorage* pStorage);
```

### <a name="remarks"></a>Bemerkungen

Die ATL-Implementierung delegiert die [IPersistStreamInit-Schnittstelle.](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) `Load`verwendet einen Stream mit dem Namen "Contents", um die Daten des Objekts abzurufen. Die [Save-Methode](#save) erstellt diesen Stream ursprünglich.

Siehe [IPersistStorage:Load](/windows/win32/api/objidl/nf-objidl-ipersiststorage-load) im Windows SDK.

## <a name="ipersiststorageimplsave"></a><a name="save"></a>IPersistStorageImpl::Speichern

Speichert die Eigenschaften des Objekts im angegebenen Speicher.

```
STDMETHOD(Save)(IStorage* pStorage, BOOL fSameAsLoad);
```

### <a name="remarks"></a>Bemerkungen

Die ATL-Implementierung delegiert die [IPersistStreamInit-Schnittstelle.](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit) Beim `Save` ersten Aufruf wird ein Stream mit dem Namen "Contents" auf dem angegebenen Speicher erstellt. Dieser Stream wird dann in `Save` späteren Aufrufen von und in Aufrufen von [Load](#load)verwendet.

Siehe [IPersistStorage:Speichern](/windows/win32/api/objidl/nf-objidl-ipersiststorage-save) im Windows SDK.

## <a name="ipersiststorageimplsavecompleted"></a><a name="savecompleted"></a>IPersistStorageImpl::SaveCompleted

Benachrichtigt ein Objekt, dass es in den Normalmodus zurückkehren kann, um in sein Speicherobjekt zu schreiben.

```
STDMETHOD(SaveCompleted)(IStorage*);
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Siehe [IPersistStorage:SaveCompleted](/windows/win32/api/objidl/nf-objidl-ipersiststorage-savecompleted) im Windows SDK.

## <a name="see-also"></a>Siehe auch

[Speicher und Streams](/windows/win32/Stg/storages-and-streams)<br/>
[IPersistStreamInitImpl-Klasse](../../atl/reference/ipersiststreaminitimpl-class.md)<br/>
[IPersistPropertyBagImpl-Klasse](../../atl/reference/ipersistpropertybagimpl-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
