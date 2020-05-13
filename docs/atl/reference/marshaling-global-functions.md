---
title: Marshalling globaler Funktionen
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlFreeMarshalStream
- atlbase/ATL::AtlMarshalPtrInProc
- atlbase/ATL::AtlUnmarshalPtr
ms.assetid: 877100b5-6ad9-44c5-a2e0-09414f1720d0
ms.openlocfilehash: b839e93b6251a09ce79df60a49b4054d1af76cc9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326266"
---
# <a name="marshaling-global-functions"></a>Marshalling globaler Funktionen

Diese Funktionen bieten Unterstützung für das Marshallen und Konvertieren von Marshallingdaten in Schnittstellenzeiger.

> [!IMPORTANT]
> Die in der folgenden Tabelle aufgeführten Funktionen können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

|||
|-|-|
|[AtlFreeMarshalStream](#atlfreemarshalstream)|Gibt die Marshalldaten `IStream` und den Zeiger frei.|
|[AtlMarshalPtrInProc](#atlmarshalptrinproc)|Erstellt ein neues Streamobjekt und marshallt den angegebenen Schnittstellenzeiger.|
|[AtlUnmarshalPtr](#atlunmarshalptr)|Konvertiert die Marshallingdaten eines Streams in einen Schnittstellenzeiger.|

## <a name="requirements"></a>Anforderungen:

**Kopfzeile:** atlbase.h

## <a name="atlfreemarshalstream"></a><a name="atlfreemarshalstream"></a>AtlFreeMarshalStream

Gibt die Marschalldaten im Stream und anschließend den Streamzeiger frei.

```
HRESULT AtlFreeMarshalStream(IStream* pStream);
```

### <a name="parameters"></a>Parameter

*pStream*<br/>
[in] Ein Zeiger auf `IStream` die Schnittstelle auf dem Stream, der zum Marshallen verwendet wird.

### <a name="example"></a>Beispiel

Siehe Beispiel für [AtlMarshalPtrInProc](#atlmarshalptrinproc).

## <a name="atlmarshalptrinproc"></a><a name="atlmarshalptrinproc"></a>AtlMarshalPtrInProc

Erstellt ein neues Streamobjekt, schreibt die CLSID des Proxys in den Stream und marshallt den angegebenen Schnittstellenzeiger durch Schreiben der für die Initialisierung des Proxys erforderlichen Daten in den Stream.

```
HRESULT AtlMarshalPtrInProc(
    IUnknown* pUnk,
    const IID& iid,
    IStream** ppStream);
```

### <a name="parameters"></a>Parameter

*Punk*<br/>
[in] Ein Zeiger auf die zu marshallende Schnittstelle.

*Iid*<br/>
[in] Die GUID der gemarshallten Schnittstelle.

*ppStream*<br/>
[out] Ein Zeiger auf `IStream` die Schnittstelle des neuen Streamobjekts, das zum Marshallen verwendet wird.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Das MSHLFLAGS_TABLESTRONG-Flag wird so gesetzt, dass der Zeiger in mehrere Streams gemarshallt werden kann. Der Zeiger kann auch mehrmals gemarshallt werden.

Wenn das Marshalling fehlschlägt, wird der Streamzeiger freigegeben.

`AtlMarshalPtrInProc`kann nur für einen Zeiger auf ein In-Process-Objekt verwendet werden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_COM#50](../../atl/codesnippet/cpp/marshaling-global-functions_1.cpp)]

## <a name="atlunmarshalptr"></a><a name="atlunmarshalptr"></a>AtlUnmarshalPtr

Konvertiert die Marshallingdaten des Streams in einen Schnittstellenzeiger, der vom Client verwendet werden kann.

```
HRESULT AtlUnmarshalPtr(
    IStream* pStream,
    const IID& iid,
    IUnknown** ppUnk);
```

### <a name="parameters"></a>Parameter

*pStream*<br/>
[in] Ein Zeiger auf den Nichtgemarshallungsstrom.

*Iid*<br/>
[in] Die GUID der Schnittstelle, die nicht gemarshallt wird.

*ppUnk*<br/>
[out] Ein Zeiger auf die nicht gemarshallte Schnittstelle.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="example"></a>Beispiel

Siehe Beispiel für [AtlMarshalPtrInProc](#atlmarshalptrinproc).

## <a name="see-also"></a>Siehe auch

[Functions](../../atl/reference/atl-functions.md)
