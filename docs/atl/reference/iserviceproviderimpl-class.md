---
title: IServiceProviderImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- IServiceProviderImpl
- ATLCOM/ATL::IServiceProviderImpl
- ATLCOM/ATL::IServiceProviderImpl::QueryService
helpviewer_keywords:
- IServiceProviderImpl class
- IServiceProvider interface, ATL implementation
ms.assetid: 251254d3-c4ce-40d7-aee0-3d676d1d72f2
ms.openlocfilehash: ef0ee4f77441cb8d19ea2d6dcada1fed9faf2782
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329417"
---
# <a name="iserviceproviderimpl-class"></a>IServiceProviderImpl-Klasse

Diese Klasse stellt eine `IServiceProvider` Standardimplementierung der Schnittstelle bereit.

## <a name="syntax"></a>Syntax

```
template <class T>
class ATL_NO_VTABLE IServiceProviderImpl : public IServiceProvider
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Ihre Klasse, `IServiceProviderImpl`abgeleitet von .

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IServiceProviderImpl::QueryService](#queryservice)|Erstellt oder greift auf den angegebenen Dienst zu und gibt einen Schnittstellenzeiger an die angegebene Schnittstelle für den Dienst zurück.|

## <a name="remarks"></a>Bemerkungen

Die `IServiceProvider` Schnittstelle sucht einen Dienst, der von der GUID angegeben wird, und gibt den Schnittstellenzeiger für die angeforderte Schnittstelle im Dienst zurück. Die `IServiceProviderImpl` Klasse stellt eine Standardimplementierung dieser Schnittstelle bereit.

`IServiceProviderImpl`gibt eine Methode an: [QueryService](#queryservice), die den angegebenen Dienst erstellt oder darauf zugreift und einen Schnittstellenzeiger an die angegebene Schnittstelle für den Dienst zurückgibt.

`IServiceProviderImpl`verwendet eine Servicezuordnung, beginnend mit [BEGIN_SERVICE_MAP](service-map-macros.md#begin_service_map) und endet mit [END_SERVICE_MAP](service-map-macros.md#end_service_map).

Die Servicezuordnung enthält zwei Einträge: [SERVICE_ENTRY](service-map-macros.md#service_entry), die eine vom Objekt unterstützte Service-ID (SID) angibt, und [SERVICE_ENTRY_CHAIN](service-map-macros.md#service_entry_chain), die eine Kette an ein anderes Objekt aufruft. `QueryService`

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IServiceProvider`

`IServiceProviderImpl`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="iserviceproviderimplqueryservice"></a><a name="queryservice"></a>IServiceProviderImpl::QueryService

Erstellt oder greift auf den angegebenen Dienst zu und gibt einen Schnittstellenzeiger an die angegebene Schnittstelle für den Dienst zurück.

```
STDMETHOD(QueryService)(
    REFGUID guidService,
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>Parameter

*guidService*<br/>
[in] Zeiger auf einen Dienstbezeichner (SID).

*riid*<br/>
[in] Bezeichner der Schnittstelle, auf die der Aufrufer zugreifen soll.

*ppvObj*<br/>
[out] Indirekter Zeiger auf die angeforderte Schnittstelle.

### <a name="return-value"></a>Rückgabewert

Der zurückgegebene HRESULT-Wert ist einer der folgenden:

|Rückgabewert|Bedeutung|
|------------------|-------------|
|S_OK|Der Dienst wurde erfolgreich erstellt oder abgerufen.|
|E_INVALIDARG|Mindestens eines der Argumente ist ungültig.|
|E_OUTOFMEMORY|Der Arbeitsspeicher reicht nicht aus, um den Dienst zu erstellen.|
|E_UNEXPECTED|Es ist ein unbekannter Fehler aufgetreten.|
|E_NOINTERFACE|Die angeforderte Schnittstelle ist nicht Teil dieses Dienstes, oder der Dienst ist unbekannt.|

### <a name="remarks"></a>Bemerkungen

`QueryService`gibt einen indirekten Zeiger auf die angeforderte Schnittstelle im angegebenen Dienst zurück. Der Aufrufer ist für die Freigabe dieses Zeigers verantwortlich, wenn er nicht mehr benötigt wird.

Wenn Sie `QueryService`aufrufen, übergeben Sie sowohl einen Dienstbezeichner (*guidService*) als auch einen Schnittstellenbezeichner (*riid*). Der *guidService* gibt den Dienst an, auf den Sie zugreifen möchten, und die *riid* identifiziert eine Schnittstelle, die Teil des Dienstes ist. Im Gegenzug erhalten Sie einen indirekten Zeiger auf die Schnittstelle.

Das Objekt, das die Schnittstelle implementiert, kann auch Schnittstellen implementieren, die Teil anderer Dienste sind. Beachten Sie Folgendes:

- Einige dieser Schnittstellen sind möglicherweise optional. Nicht alle in der Dienstbeschreibung definierten Schnittstellen sind notwendigerweise bei jeder Implementierung des Dienstes oder bei jedem zurückgegebenen Objekt vorhanden.

- Im Gegensatz `QueryInterface`zu Aufrufen von bedeutet das Übergeben eines anderen Dienstbezeichners nicht notwendigerweise, dass ein anderes COM-Objekt (Component Object Model) zurückgegeben wird.

- Das zurückgegebene Objekt verfügt möglicherweise über zusätzliche Schnittstellen, die nicht Teil der Definition des Dienstes sind.

Zwei verschiedene Dienste, z. B. SID_SMyService und SID_SYourService, können beide die Verwendung derselben Schnittstelle angeben, auch wenn die Implementierung der Schnittstelle zwischen den beiden Diensten möglicherweise nichts gemeinsam hat. Dies funktioniert, da `QueryService` ein Aufruf von (SID_SMyService, `QueryService` IID_IDispatch) ein anderes Objekt als (SID_SYourService, IID_IDispatch) zurückgeben kann. Die Objektidentität wird nicht angenommen, wenn Sie einen anderen Dienstbezeichner angeben.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)
