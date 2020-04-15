---
title: CMonikerFile-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMonikerFile
- AFXOLE/CMonikerFile
- AFXOLE/CMonikerFile::CMonikerFile
- AFXOLE/CMonikerFile::Close
- AFXOLE/CMonikerFile::Detach
- AFXOLE/CMonikerFile::GetMoniker
- AFXOLE/CMonikerFile::Open
- AFXOLE/CMonikerFile::CreateBindContext
helpviewer_keywords:
- CMonikerFile [MFC], CMonikerFile
- CMonikerFile [MFC], Close
- CMonikerFile [MFC], Detach
- CMonikerFile [MFC], GetMoniker
- CMonikerFile [MFC], Open
- CMonikerFile [MFC], CreateBindContext
ms.assetid: 87be5966-f4f7-4235-bce2-1fa39e9417de
ms.openlocfilehash: fc74ad2499fcde63faa2c5859a87fd9ffd2846eb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319776"
---
# <a name="cmonikerfile-class"></a>CMonikerFile-Klasse

Stellt einen Datenstrom dar ( [IStream](/windows/win32/api/objidl/nn-objidl-istream)), der von einem [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker)benannt wird.

## <a name="syntax"></a>Syntax

```
class CMonikerFile : public COleStreamFile
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMonikerFile::CMonikerFile](#cmonikerfile)|Erstellt ein `CMonikerFile`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMonikerFile::Schließen](#close)|Detaches und gibt den Stream frei und gibt den Moniker frei.|
|[CMonikerFile::Detach](#detach)|Trennt die `IMoniker` von `CMonikerFile` diesem Objekt.|
|[CMonikerFile::GetMoniker](#getmoniker)|Gibt den aktuellen Moniker zurück.|
|[CMonikerFile::Öffnen](#open)|Öffnet die angegebene Datei, um einen Stream abzuerhalten.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMonikerFile::CreateBindContext](#createbindcontext)|Ruft den Bindungskontext ab oder erstellt einen standardmäßigen initialisierten Bindungskontext.|

## <a name="remarks"></a>Bemerkungen

Ein Moniker enthält Informationen, die einem Pfadnamen zu einer Datei ähnlich sind. Wenn Sie über einen Zeiger auf die `IMoniker` Schnittstelle eines Monikerobjekts verfügen, können Sie auf die identifizierte Datei zugreifen, ohne über andere spezifische Informationen darüber zu verfügen, wo sich die Datei tatsächlich befindet.

Abgeleitet `COleStreamFile`von `CMonikerFile` nimmt ein Moniker oder eine Zeichenfolgendarstellung, die er in einen Moniker umsetzen kann, und bindet an den Stream, für den der Moniker ein Name ist. Sie können dann lesen und in diesen Stream schreiben. Der eigentliche `CMonikerFile` Zweck von ist `IStream`es, `IMoniker`einfachen Zugriff auf s von s benannt, so `CFile` dass Sie nicht an einen Stream selbst binden müssen, aber Funktionalität für den Stream haben.

`CMonikerFile`kann nicht verwendet werden, um an etwas anderes als einen Stream zu binden. Wenn Sie eine Bindung an speicher- oder `IMoniker` ein Objekt verwenden möchten, müssen Sie die Schnittstelle direkt verwenden.

Weitere Informationen zu Streams und Monikern finden Sie unter [COleStreamFile](../../mfc/reference/colestreamfile-class.md) in der *MFC-Referenz* und [IStream](/windows/win32/api/objidl/nn-objidl-istream) und [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker) im Windows SDK.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

`CMonikerFile`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxole.h

## <a name="cmonikerfileclose"></a><a name="close"></a>CMonikerFile::Schließen

Rufen Sie diese Funktion auf, um den Stream zu trennen und freizugeben und den Moniker freizugeben.

```
virtual void Close();
```

### <a name="remarks"></a>Bemerkungen

Kann auf ungeöffnete oder bereits geschlossene Streams aufgerufen werden.

## <a name="cmonikerfilecmonikerfile"></a><a name="cmonikerfile"></a>CMonikerFile::CMonikerFile

Erstellt ein `CMonikerFile`-Objekt.

```
CMonikerFile();
```

## <a name="cmonikerfilecreatebindcontext"></a><a name="createbindcontext"></a>CMonikerFile::CreateBindContext

Rufen Sie diese Funktion auf, um einen standardmäßigen initialisierten Bindungskontext zu erstellen.

```
IBindCtx* CreateBindContext(CFileException* pError);
```

### <a name="parameters"></a>Parameter

*pError*<br/>
Ein Zeiger auf eine Dateiausnahme. Im Falle eines Fehlers wird er auf die Ursache festgelegt.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den Bindungskontext, mit [dem IBindCtx](/windows/win32/api/objidl/nn-objidl-ibindctx) gebunden werden soll, wenn erfolgreich; andernfalls NULL. Wenn die Instanz mit `IBindHost` einer Schnittstelle geöffnet wurde, `IBindHost`wird der Bindungskontext aus der abgerufen. Wenn keine `IBindHost` Schnittstelle vorhanden ist oder die Schnittstelle keinen Bindungskontext zurückgibt, wird ein Bindungskontext erstellt. Eine Beschreibung der [IBindHost-Schnittstelle](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775076\(v=vs.85\)) finden Sie im Windows SDK.

### <a name="remarks"></a>Bemerkungen

Ein Bindungskontext ist ein Objekt, das Informationen zu einem bestimmten Monikerbindungsvorgang speichert. Sie können diese Funktion überschreiben, um einen benutzerdefinierten Bindungskontext bereitzustellen.

## <a name="cmonikerfiledetach"></a><a name="detach"></a>CMonikerFile::Detach

Rufen Sie diese Funktion auf, um den Stream zu schließen.

```
BOOL Detach(CFileException* pError = NULL);
```

### <a name="parameters"></a>Parameter

*pError*<br/>
Ein Zeiger auf eine Dateiausnahme. Im Falle eines Fehlers wird er auf die Ursache festgelegt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

## <a name="cmonikerfilegetmoniker"></a><a name="getmoniker"></a>CMonikerFile::GetMoniker

Rufen Sie diese Funktion auf, um einen Zeiger auf den aktuellen Moniker abzurufen.

```
IMoniker* GetMoniker() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die aktuelle Monikerschnittstelle ( [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker)).

### <a name="remarks"></a>Bemerkungen

Da `CMonikerFile` es sich nicht um eine Schnittstelle handelt, erhöht der zurückgegebene Zeiger die Verweisanzahl nicht (über [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)), und der Moniker wird freigegeben, wenn das `CMonikerFile` Objekt freigegeben wird. Wenn Sie an dem Moniker festhalten oder ihn `AddRef` selbst freigeben möchten, müssen Sie ihn selbst freigeben.

## <a name="cmonikerfileopen"></a><a name="open"></a>CMonikerFile::Öffnen

Rufen Sie diese Memberfunktion auf, um eine Datei oder ein Monikerobjekt zu öffnen.

```
virtual BOOL Open(
    LPCTSTR lpszURL,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>Parameter

*lpszURL*<br/>
Eine URL oder ein Dateiname der zu öffnenden Datei.

*pError*<br/>
Ein Zeiger auf eine Dateiausnahme. Im Falle eines Fehlers wird er auf die Ursache festgelegt.

*pMoniker*<br/>
Ein Zeiger auf die `IMoniker` Monikerschnittstelle, die zum Abrufen eines Streams verwendet werden soll.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Der *Parameter lpszURL* kann auf einem Macintosh nicht verwendet werden. Nur die *pMoniker-Form* von `Open` kann auf einem Macintosh verwendet werden.

Sie können eine URL oder einen Dateinamen für den Parameter *lpszURL* verwenden. Beispiel:

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/cmonikerfile-class_1.cpp)]

\- oder -

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/cmonikerfile-class_2.cpp)]

## <a name="see-also"></a>Siehe auch

[COleStreamFile-Klasse](../../mfc/reference/colestreamfile-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CAsyncMonikerFile-Klasse](../../mfc/reference/casyncmonikerfile-class.md)
