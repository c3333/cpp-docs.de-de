---
title: Marshalling von globalen Funktionen
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlFreeMarshalStream
- atlbase/ATL::AtlMarshalPtrInProc
- atlbase/ATL::AtlUnmarshalPtr
ms.assetid: 877100b5-6ad9-44c5-a2e0-09414f1720d0
ms.openlocfilehash: 79b19b613fbae49c0f8338dcadd2225e092fb371
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835323"
---
# <a name="marshaling-global-functions"></a>Marshalling von globalen Funktionen

Diese Funktionen bieten Unterstützung für das Marshalling und das Umstellen von Marshallingdaten in Schnittstellen Zeiger.

> [!IMPORTANT]
> Die in der folgenden Tabelle aufgeführten Funktionen können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

|Name|Beschreibung|
|-|-|
|[AtlFreeMarshalStream](#atlfreemarshalstream)|Gibt die Mars Hall Daten und den- `IStream` Zeiger frei.|
|[AtlMarshalPtrInProc](#atlmarshalptrinproc)|Erstellt ein neues Streamobjekt und Marshalls den angegebenen Schnittstellen Zeiger.|
|[AtlUnmarshalPtr](#atlunmarshalptr)|Konvertiert die Marshallingdaten eines Streams in einen-Schnittstellen Zeiger.|

## <a name="requirements"></a>Anforderungen:

**Header:** atlbase. h

## <a name="atlfreemarshalstream"></a><a name="atlfreemarshalstream"></a> Atlfreemarshalstream

Gibt die Marschalldaten im Stream und anschließend den Streamzeiger frei.

```
HRESULT AtlFreeMarshalStream(IStream* pStream);
```

### <a name="parameters"></a>Parameter

*pStream*<br/>
in Ein Zeiger auf die- `IStream` Schnittstelle auf dem Stream, der für das Marshalling verwendet wird.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [atlmarshalptrinproc](#atlmarshalptrinproc).

## <a name="atlmarshalptrinproc"></a><a name="atlmarshalptrinproc"></a> Atlmarshalptrinproc

Erstellt ein neues Streamobjekt, schreibt die CLSID des Proxys in den Stream und marshallt den angegebenen Schnittstellenzeiger durch Schreiben der für die Initialisierung des Proxys erforderlichen Daten in den Stream.

```
HRESULT AtlMarshalPtrInProc(
    IUnknown* pUnk,
    const IID& iid,
    IStream** ppStream);
```

### <a name="parameters"></a>Parameter

*Kro*<br/>
in Ein Zeiger auf die-Schnittstelle, die gemarshallt werden soll.

*IID*<br/>
in Die GUID der Schnittstelle, die gemarshallt wird.

*ppStream*<br/>
vorgenommen Ein Zeiger auf die- `IStream` Schnittstelle für das neue Streamobjekt, das für das Marshalling verwendet wird.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="remarks"></a>Bemerkungen

Das MSHLFLAGS_TABLESTRONG-Flag ist festgelegt, sodass der Zeiger an mehrere Datenströme gemarshallt werden kann. Der Zeiger kann auch mehrmals gemarshallt werden.

Wenn das Marshalling fehlschlägt, wird der Streamzeiger freigegeben.

`AtlMarshalPtrInProc` kann nur für einen Zeiger auf ein Objekt vom Typ "in-Process" verwendet werden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_COM#50](../../atl/codesnippet/cpp/marshaling-global-functions_1.cpp)]

## <a name="atlunmarshalptr"></a><a name="atlunmarshalptr"></a> Atlunmarshalptr

Konvertiert die Marshallingdaten des Streams in einen Schnittstellenzeiger, der vom Client verwendet werden kann.

```
HRESULT AtlUnmarshalPtr(
    IStream* pStream,
    const IID& iid,
    IUnknown** ppUnk);
```

### <a name="parameters"></a>Parameter

*pStream*<br/>
in Ein Zeiger auf den Stream, der nicht gemarshallt wird.

*IID*<br/>
in Die GUID der Schnittstelle, die gemarshallt wird.

*ppUnk*<br/>
vorgenommen Ein Zeiger auf die nicht gemarshallte Schnittstelle.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [atlmarshalptrinproc](#atlmarshalptrinproc).

## <a name="see-also"></a>Siehe auch

[Funktionen](../../atl/reference/atl-functions.md)
