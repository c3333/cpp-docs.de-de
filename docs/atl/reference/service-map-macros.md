---
title: Service Map-Makros
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_SERVICE_MAP
- atlcom/ATL::END_SERVICE_MAP
- atlcom/ATL::SERVICE_ENTRY
- atlcom/ATL::SERVICE_ENTRY_CHAIN
ms.assetid: ca02a125-454a-4cf6-aac2-1c5585025ed4
ms.openlocfilehash: eb2fe41c79135a7ac2ced9bc3242b070170716b9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325941"
---
# <a name="service-map-macros"></a>Service Map-Makros

Diese Makros definieren Dienstzuordnungen und Einträge.

|||
|-|-|
|[BEGIN_SERVICE_MAP](#begin_service_map)|Markiert den Anfang einer ATL-Servicezuordnung.|
|[END_SERVICE_MAP](#end_service_map)|Markiert das Ende einer ATL-Servicezuordnung.|
|[SERVICE_ENTRY](#service_entry)|Gibt an, dass das Objekt eine bestimmte Dienst-ID unterstützt.|
|[SERVICE_ENTRY_CHAIN](#service_entry_chain)|Weist [IServiceProviderImpl::QueryService](#queryservice) an, das angegebene Objekt zu verketten.|

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="begin_service_map"></a><a name="begin_service_map"></a>BEGIN_SERVICE_MAP

Markiert den Anfang der Servicezuordnung.

```
BEGIN_SERVICE_MAP(theClass)
```

### <a name="parameters"></a>Parameter

*theClass*<br/>
[in] Gibt die Klasse an, die die Servicezuordnung enthält.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie die Servicezuordnung, um die Service provider-Funktionalität für Ihr COM-Objekt zu implementieren. Zuerst müssen Sie Ihre Klasse von [IServiceProviderImpl](../../atl/reference/iserviceproviderimpl-class.md)ableiten. Es gibt zwei Arten von Einträgen:

- [SERVICE_ENTRY](#service_entry)   Gibt die Unterstützung für die angegebene Dienst-ID (SID) an.

- [SERVICE_ENTRY_CHAIN](#service_entry_chain)   Weist [IServiceProviderImpl::QueryService](#queryservice) an, eine Verkettung an ein anderes, angegebenes Objekt zu verwenden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_COM#57](../../atl/codesnippet/cpp/service-map-macros_1.h)]

## <a name="end_service_map"></a><a name="end_service_map"></a>END_SERVICE_MAP

Markiert das Ende der Servicezuordnung.

```
END_SERVICE_MAP()
```

### <a name="example"></a>Beispiel

Siehe Beispiel für [BEGIN_SERVICE_MAP](#begin_service_map).

## <a name="service_entry"></a><a name="service_entry"></a>SERVICE_ENTRY

Gibt an, dass das Objekt die von *SID*angegebene Dienst-ID unterstützt.

```
SERVICE_ENTRY( SID )
```

### <a name="parameters"></a>Parameter

*Sid*<br/>
Die Dienst-ID.

### <a name="example"></a>Beispiel

Siehe Beispiel für [BEGIN_SERVICE_MAP](#begin_service_map).

## <a name="service_entry_chain"></a><a name="service_entry_chain"></a>SERVICE_ENTRY_CHAIN

Weist [IServiceProviderImpl::QueryService](#queryservice) an, das von *punk*angegebene Objekt zu verketten.

```
SERVICE_ENTRY_CHAIN( punk )
```

### <a name="parameters"></a>Parameter

*Punk*<br/>
Ein Zeiger auf die **IUnknown-Schnittstelle,** an die gekettet werden soll.

### <a name="example"></a>Beispiel

Siehe Beispiel für [BEGIN_SERVICE_MAP](#begin_service_map).

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

[Makros](../../atl/reference/atl-macros.md)
