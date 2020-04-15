---
title: IRunnableObjectImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- IRunnableObjectImpl
- ATLCTL/ATL::IRunnableObjectImpl
- ATLCTL/ATL::IRunnableObjectImpl::GetRunningClass
- ATLCTL/ATL::IRunnableObjectImpl::IsRunning
- ATLCTL/ATL::IRunnableObjectImpl::LockRunning
- ATLCTL/ATL::IRunnableObjectImpl::Run
- ATLCTL/ATL::IRunnableObjectImpl::SetContainedObject
helpviewer_keywords:
- containers, running controls
- IRunnableObjectImpl class
- IRunnableObject, ATL implementation
- controls [ATL], running
- controls [C++], container running in ATL
ms.assetid: 305c7c3b-889e-49dd-aca1-34379c1b9931
ms.openlocfilehash: 2843c0c25a5c104ffbdff72255ac5d85cf53b1ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329445"
---
# <a name="irunnableobjectimpl-class"></a>IRunnableObjectImpl-Klasse

Diese Klasse `IUnknown` implementiert und stellt eine Standardimplementierung der [IRunnableObject-Schnittstelle](/windows/win32/api/objidl/nn-objidl-irunnableobject) bereit.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template<class T>
class IRunnableObjectImpl
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Ihre Klasse, `IRunnableObjectImpl`abgeleitet von .

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IRunnableObjectImpl::GetRunningClass](#getrunningclass)|Gibt die CLSID des ausgeführten Steuerelements zurück. Die ATL-Implementierung legt die CLSID auf GUID_NULL fest und gibt E_UNEXPECTED zurück.|
|[IRunnableObjectImpl::IsRunning](#isrunning)|Bestimmt, ob das Steuerelement ausgeführt wird. Die ATL-Implementierung gibt TRUE zurück.|
|[IRunnableObjectImpl::LockRunning](#lockrunning)|Sperrt das Steuerelement in den ausgeführten Zustand. Die ATL-Implementierung gibt S_OK zurück.|
|[IRunnableObjectImpl::Ausführen](#run)|Erzwingt die Ausführung des Steuerelements. Die ATL-Implementierung gibt S_OK zurück.|
|[IRunnableObjectImpl::SetContainedObject](#setcontainedobject)|Gibt an, dass das Steuerelement eingebettet ist. Die ATL-Implementierung gibt S_OK zurück.|

## <a name="remarks"></a>Bemerkungen

Die [IRunnableObject-Schnittstelle](/windows/win32/api/objidl/nn-objidl-irunnableobject) ermöglicht es einem Container, zu bestimmen, ob ein Steuerelement ausgeführt wird, es zum Ausführen zu zwingen oder in den ausgeführten Zustand zu sperren. Die `IRunnableObjectImpl` Klasse stellt eine Standardimplementierung `IUnknown` dieser Schnittstelle bereit und implementiert, indem Informationen in Debugbuilds an das Dumpgerät gesendet werden.

**Verwandte Artikel** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Erstellen eines [ATL-Projekts](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IRunnableObject`

`IRunnableObjectImpl`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlctl.h

## <a name="irunnableobjectimplgetrunningclass"></a><a name="getrunningclass"></a>IRunnableObjectImpl::GetRunningClass

Gibt die CLSID des ausgeführten Steuerelements zurück.

```
HRESULT GetRunningClass(LPCLSID lpClsid);
```

### <a name="return-value"></a>Rückgabewert

Die ATL-Implementierung legt fest, dass \* *lpClsid* GUID_NULL und gibt E_UNEXPECTED zurück.

### <a name="remarks"></a>Bemerkungen

Siehe [IRunnableObject::GetRunningClass](/windows/win32/api/objidl/nf-objidl-irunnableobject-getrunningclass) im Windows SDK.

## <a name="irunnableobjectimplisrunning"></a><a name="isrunning"></a>IRunnableObjectImpl::IsRunning

Bestimmt, ob das Steuerelement ausgeführt wird.

```
virtual BOOL IsRunning();
```

### <a name="return-value"></a>Rückgabewert

Die ATL-Implementierung gibt TRUE zurück.

### <a name="remarks"></a>Bemerkungen

Siehe [IRunnableObject::IsRunning](/windows/win32/api/objidl/nf-objidl-irunnableobject-isrunning) im Windows SDK.

## <a name="irunnableobjectimpllockrunning"></a><a name="lockrunning"></a>IRunnableObjectImpl::LockRunning

Sperrt das Steuerelement in den ausgeführten Zustand.

```
HRESULT LockRunning(BOOL fLock, BOOL fLastUnlockCloses);
```

### <a name="return-value"></a>Rückgabewert

Die ATL-Implementierung gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Siehe [IRunnableObject::LockRunning](/windows/win32/api/objidl/nf-objidl-irunnableobject-lockrunning) im Windows SDK.

## <a name="irunnableobjectimplrun"></a><a name="run"></a>IRunnableObjectImpl::Ausführen

Erzwingt die Ausführung des Steuerelements.

```
HRESULT Run(LPBINDCTX lpbc);
```

### <a name="return-value"></a>Rückgabewert

Die ATL-Implementierung gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Siehe [IRunnableObject::Ausführen](/windows/win32/api/objidl/nf-objidl-irunnableobject-run) im Windows SDK.

## <a name="irunnableobjectimplsetcontainedobject"></a><a name="setcontainedobject"></a>IRunnableObjectImpl::SetContainedObject

Gibt an, dass das Steuerelement eingebettet ist.

```
HRESULT SetContainedObject(BOOL fContained);
```

### <a name="return-value"></a>Rückgabewert

Die ATL-Implementierung gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Siehe [IRunnableObject::SetContainedObject](/windows/win32/api/objidl/nf-objidl-irunnableobject-setcontainedobject) im Windows SDK.

## <a name="see-also"></a>Siehe auch

[CComControl-Klasse](../../atl/reference/ccomcontrol-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
