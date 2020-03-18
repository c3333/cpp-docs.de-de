---
title: Dienstzuordnung Makros
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_SERVICE_MAP
- atlcom/ATL::END_SERVICE_MAP
- atlcom/ATL::SERVICE_ENTRY
- atlcom/ATL::SERVICE_ENTRY_CHAIN
ms.assetid: ca02a125-454a-4cf6-aac2-1c5585025ed4
ms.openlocfilehash: ab130b2401dc9885f82fd5668a2d722a96dd289b
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422931"
---
# <a name="service-map-macros"></a>Dienstzuordnung Makros

Diese Makros definieren Dienst Zuordnungen und Einträge.

|||
|-|-|
|[BEGIN_SERVICE_MAP](#begin_service_map)|Markiert den Anfang einer ATL-Dienst Zuordnung.|
|[END_SERVICE_MAP](#end_service_map)|Markiert das Ende einer ATL-Dienst Zuordnung.|
|[SERVICE_ENTRY](#service_entry)|Gibt an, dass das Objekt eine bestimmte Dienst-ID unterstützt.|
|[SERVICE_ENTRY_CHAIN](#service_entry_chain)|Weist [IServiceProviderImpl:: QueryService](#queryservice) an, an das angegebene Objekt zu verketten.|

## <a name="requirements"></a>Voraussetzungen

**Header:** Atlcom. h

##  <a name="begin_service_map"></a>BEGIN_SERVICE_MAP

Markiert den Anfang der Service Map.

```
BEGIN_SERVICE_MAP(theClass)
```

### <a name="parameters"></a>Parameter

*spiegeln*<br/>
in Gibt die Klasse an, die die Dienst Zuordnung enthält.

### <a name="remarks"></a>Hinweise

Verwenden Sie die Dienst Zuordnung, um Dienstanbieter Funktionen für Ihr COM-Objekt zu implementieren. Zuerst müssen Sie die Klasse von [IServiceProviderImpl](../../atl/reference/iserviceproviderimpl-class.md)ableiten. Es gibt zwei Arten von Einträgen:

- [SERVICE_ENTRY](#service_entry)   Gibt die Unterstützung für die angegebene Dienst-ID (SID) an.

- [SERVICE_ENTRY_CHAIN](#service_entry_chain)   Weist [IServiceProviderImpl:: QueryService](#queryservice) an, an ein anderes angegebenes Objekt zu verketten.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_COM#57](../../atl/codesnippet/cpp/service-map-macros_1.h)]

##  <a name="end_service_map"></a>END_SERVICE_MAP

Markiert das Ende der Dienst Zuordnung.

```
END_SERVICE_MAP()
```

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [BEGIN_SERVICE_MAP](#begin_service_map).

##  <a name="service_entry"></a>SERVICE_ENTRY

Gibt an, dass das Objekt die von der *sid*angegebene Dienst-ID unterstützt.

```
SERVICE_ENTRY( SID )
```

### <a name="parameters"></a>Parameter

*SID*<br/>
Die Dienst-ID.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [BEGIN_SERVICE_MAP](#begin_service_map).

##  <a name="service_entry_chain"></a>SERVICE_ENTRY_CHAIN

Weist [IServiceProviderImpl:: QueryService](#queryservice) an, an das von *Punk*angegebene Objekt zu verketten.

```
SERVICE_ENTRY_CHAIN( punk )
```

### <a name="parameters"></a>Parameter

*Kro*<br/>
Ein Zeiger auf die **IUnknown** -Schnittstelle, zu der verkettet werden soll.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [BEGIN_SERVICE_MAP](#begin_service_map).

##  <a name="queryservice"></a>IServiceProviderImpl:: QueryService

Erstellt oder greift auf den angegebenen Dienst zu und gibt einen Schnittstellen Zeiger auf die angegebene Schnittstelle für den Dienst zurück.

```
STDMETHOD(QueryService)(
    REFGUID guidService,
    REFIID riid,
    void** ppvObject);
```

### <a name="parameters"></a>Parameter

*guidservice*<br/>
in Zeiger auf einen Dienst Bezeichner (SID).

*riid*<br/>
in Der Bezeichner der Schnittstelle, auf die der Aufrufer Zugriff erhalten soll.

*ppvObj*<br/>
vorgenommen Indirekter Zeiger auf die angeforderte Schnittstelle.

### <a name="return-value"></a>Rückgabewert

Der zurückgegebene HRESULT-Wert ist einer der folgenden:

|Rückgabewert|Bedeutung|
|------------------|-------------|
|S_OK|Der Dienst wurde erfolgreich erstellt oder abgerufen.|
|E_INVALIDARG|Mindestens eines der Argumente ist ungültig.|
|E_OUTOFMEMORY|Der Speicher reicht nicht aus, um den Dienst zu erstellen.|
|E_UNEXPECTED|Unbekannter Fehler.|
|E_NOINTERFACE|Die angeforderte Schnittstelle gehört nicht zum Dienst, oder der Dienst ist unbekannt.|

### <a name="remarks"></a>Hinweise

`QueryService` gibt einen indirekten Zeiger auf die angeforderte Schnittstelle im angegebenen Dienst zurück. Der Aufrufer ist dafür verantwortlich, diesen Zeiger freizugeben, wenn er nicht mehr benötigt wird.

Wenn Sie `QueryService`aufgerufen haben, übergeben Sie sowohl einen Dienst Bezeichner (*guidservice*) als auch einen Schnittstellen Bezeichner (*riid*). Der *guidservice* gibt den Dienst an, auf den Sie zugreifen möchten, und die *riid* identifiziert eine Schnittstelle, die Teil des Dienstanbieter ist. In der Rückgabe erhalten Sie einen indirekten Zeiger auf die-Schnittstelle.

Das Objekt, das die-Schnittstelle implementiert, kann auch Schnittstellen implementieren, die Teil anderer Dienste sind. Berücksichtigen Sie die folgenden Aspekte:

- Einige dieser Schnittstellen sind möglicherweise optional. Nicht alle Schnittstellen, die in der Dienst Beschreibung definiert sind, sind notwendigerweise für jede Implementierung des Dienstanbieter oder für jedes zurückgegebene Objekt vorhanden.

- Anders als bei Aufrufen von `QueryInterface`bedeutet das Übergeben eines anderen Dienst Bezeichners nicht notwendigerweise, dass ein anderes Component Object Model (com)-Objekt zurückgegeben wird.

- Das zurückgegebene Objekt verfügt möglicherweise über zusätzliche Schnittstellen, die nicht Teil der Definition des Dienstanbieter sind.

Zwei verschiedene Dienste, wie z. b. SID_SMyService und SID_SYourService, können die Verwendung der gleichen Schnittstelle angeben, obwohl die Implementierung der Schnittstelle möglicherweise keine gemeinsame Verwendung der beiden Dienste hat. Dies funktioniert, weil ein `QueryService` (SID_SMyService, IID_IDispatch) ein anderes Objekt als `QueryService` (SID_SYourService, IID_IDispatch) zurückgeben kann. Die Objekt Identität wird nicht angenommen, wenn Sie einen anderen Dienst Bezeichner angeben.

## <a name="see-also"></a>Siehe auch

[Makros](../../atl/reference/atl-macros.md)
