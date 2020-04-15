---
title: COleDataObject-Klasse
ms.date: 11/04/2016
f1_keywords:
- COleDataObject
- AFXOLE/COleDataObject
- AFXOLE/COleDataObject::COleDataObject
- AFXOLE/COleDataObject::Attach
- AFXOLE/COleDataObject::AttachClipboard
- AFXOLE/COleDataObject::BeginEnumFormats
- AFXOLE/COleDataObject::Detach
- AFXOLE/COleDataObject::GetData
- AFXOLE/COleDataObject::GetFileData
- AFXOLE/COleDataObject::GetGlobalData
- AFXOLE/COleDataObject::GetNextFormat
- AFXOLE/COleDataObject::IsDataAvailable
- AFXOLE/COleDataObject::Release
helpviewer_keywords:
- COleDataObject [MFC], COleDataObject
- COleDataObject [MFC], Attach
- COleDataObject [MFC], AttachClipboard
- COleDataObject [MFC], BeginEnumFormats
- COleDataObject [MFC], Detach
- COleDataObject [MFC], GetData
- COleDataObject [MFC], GetFileData
- COleDataObject [MFC], GetGlobalData
- COleDataObject [MFC], GetNextFormat
- COleDataObject [MFC], IsDataAvailable
- COleDataObject [MFC], Release
ms.assetid: d1cc84be-2e1c-4bb3-a8a0-565eb08aaa34
ms.openlocfilehash: 5e1545a033ab482e838fbc944b0ca9b3e543d651
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366134"
---
# <a name="coledataobject-class"></a>COleDataObject-Klasse

Wird in Datenübertragungen zum Abrufen von Daten in unterschiedlichen Formaten aus der Zwischenablage, per Drag & Drop oder von einem eingebetteten OLE-Element verwendet.

## <a name="syntax"></a>Syntax

```
class COleDataObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleDataObject::COleDataObject](#coledataobject)|Erstellt ein `COleDataObject`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleDataObject::Anfügen](#attach)|Fügt das angegebene OLE-Datenobjekt an die `COleDataObject`an.|
|[COleDataObject::AttachClipboard](#attachclipboard)|Fügt das Datenobjekt an, das sich in der Zwischenablage befindet.|
|[COleDataObject::BeginEnumFormats](#beginenumformats)|Bereitet sich auf einen `GetNextFormat` oder mehrere nachfolgende Anrufe vor.|
|[COleDataObject::Detach](#detach)|Trennt das zugeordnete `IDataObject` Objekt.|
|[COleDataObject::GetData](#getdata)|Kopiert Daten aus dem angehängten OLE-Datenobjekt in einem angegebenen Format.|
|[COleDataObject::GetFileData](#getfiledata)|Kopiert Daten aus dem angehängten OLE-Datenobjekt in einen `CFile` Zeiger im angegebenen Format.|
|[COleDataObject::GetGlobalData](#getglobaldata)|Kopiert Daten aus dem angehängten OLE-Datenobjekt in ein `HGLOBAL` im angegebenen Format.|
|[COleDataObject::GetNextFormat](#getnextformat)|Gibt das nächste verfügbare Datenformat zurück.|
|[COleDataObject::IsDataverfügbar](#isdataavailable)|Überprüft, ob Daten in einem angegebenen Format verfügbar sind.|
|[COleDataObject::Release](#release)|Trennt das zugeordnete `IDataObject` Objekt und gibt es frei.|

## <a name="remarks"></a>Bemerkungen

`COleDataObject`hat keine Basisklasse.

Diese Arten von Datenübertragungen umfassen eine Quelle und ein Ziel. Die Datenquelle wird als Objekt der [COleDataSource-Klasse](../../mfc/reference/coledatasource-class.md) implementiert. Wenn eine Zielanwendung Daten enthält oder aufgefordert wird, einen Einfügevorgang aus `COleDataObject` der Zwischenablage auszuführen, muss ein Objekt der Klasse erstellt werden.

Mit dieser Klasse können Sie bestimmen, ob die Daten in einem angegebenen Format vorhanden sind. Sie können auch die verfügbaren Datenformate aufzählen oder überprüfen, ob ein bestimmtes Format verfügbar ist, und dann die Daten im bevorzugten Format abrufen. Der Objektabruf kann auf verschiedene Weise durchgeführt werden, einschließlich der Verwendung `STGMEDIUM` einer [CFile,](../../mfc/reference/cfile-class.md)eines HGLOBAL oder einer Struktur.

Weitere Informationen finden Sie in der [STGMEDIUM-Struktur](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) im Windows SDK.

Weitere Informationen zur Verwendung von Datenobjekten in Ihrer Anwendung finden Sie im Artikel [Datenobjekte und Datenquellen (OLE)](../../mfc/data-objects-and-data-sources-ole.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`COleDataObject`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxole.h

## <a name="coledataobjectattach"></a><a name="attach"></a>COleDataObject::Anfügen

Rufen Sie diese `COleDataObject` Funktion auf, um das Objekt einem OLE-Datenobjekt zuzuordnen.

```
void Attach(
    LPDATAOBJECT lpDataObject,
    BOOL bAutoRelease = TRUE);
```

### <a name="parameters"></a>Parameter

*lpDataObject*<br/>
Zeigt auf ein OLE-Datenobjekt.

*bAutoRelease*<br/>
TRUE, wenn das OLE-Datenobjekt `COleDataObject` freigegeben werden soll, wenn das Objekt zerstört wird; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) im Windows SDK.

## <a name="coledataobjectattachclipboard"></a><a name="attachclipboard"></a>COleDataObject::AttachClipboard

Rufen Sie diese Funktion auf, um das Datenobjekt, das sich derzeit in der Zwischenablage befindet, an das `COleDataObject` Objekt anzuhängen.

```
BOOL AttachClipboard();
```

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Wenn Sie diese Funktion aufrufen, wird die Zwischenablage gesperrt, bis dieses Datenobjekt freigegeben wird. Das Datenobjekt wird im Destruktor für die `COleDataObject`freigegeben. Weitere Informationen finden Sie unter [OpenClipboard](/windows/win32/api/winuser/nf-winuser-openclipboard) und [CloseClipboard](/windows/win32/api/winuser/nf-winuser-closeclipboard) in der Win32-Dokumentation.

## <a name="coledataobjectbeginenumformats"></a><a name="beginenumformats"></a>COleDataObject::BeginEnumFormats

Rufen Sie diese Funktion auf, um nachfolgende Aufrufe vorzubereiten, um `GetNextFormat` eine Liste von Datenformaten aus dem Element abzurufen.

```
void BeginEnumFormats();
```

### <a name="remarks"></a>Bemerkungen

Nach einem `BeginEnumFormats`Aufruf von wird die Position des ersten Formats, das von diesem Datenobjekt unterstützt wird, gespeichert. Aufeinanderfolgende `GetNextFormat` Aufrufe an werden die Liste der verfügbaren Formate im Datenobjekt auflisten.

Um die Verfügbarkeit von Daten in einem bestimmten Format zu überprüfen, verwenden Sie [COleDataObject::IsDataAvailable](#isdataavailable).

Weitere Informationen finden Sie unter [IDataObject::EnumFormatEtc](/windows/win32/api/objidl/nf-objidl-idataobject-enumformatetc) im Windows SDK.

## <a name="coledataobjectcoledataobject"></a><a name="coledataobject"></a>COleDataObject::COleDataObject

Erstellt ein `COleDataObject`-Objekt.

```
COleDataObject();
```

### <a name="remarks"></a>Bemerkungen

Ein Aufruf von [COleDataObject::Attach](#attach) oder [COleDataObject::AttachClipboard](#attachclipboard) `COleDataObject` muss vor dem Aufruf anderer Funktionen erfolgen.

> [!NOTE]
> Da einer der Parameter für die Drag-and-Drop-Handler `COleDataObject`ein Zeiger auf ein ist, ist es nicht erforderlich, diesen Konstruktor aufzurufen, um Drag & Drop zu unterstützen.

## <a name="coledataobjectdetach"></a><a name="detach"></a>COleDataObject::Detach

Rufen Sie diese Funktion `COleDataObject` auf, um das Objekt vom zugehörigen OLE-Datenobjekt zu trennen, ohne das Datenobjekt freizugeben.

```
LPDATAOBJECT Detach();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das OLE-Datenobjekt, das getrennt wurde.

### <a name="remarks"></a>Bemerkungen

## <a name="coledataobjectgetdata"></a><a name="getdata"></a>COleDataObject::GetData

Rufen Sie diese Funktion auf, um Daten aus dem Element im angegebenen Format abzurufen.

```
BOOL GetData(
    CLIPFORMAT cfFormat,
    LPSTGMEDIUM lpStgMedium,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parameter

*cfFormat*<br/>
Das Format, in dem Daten zurückgegeben werden sollen. Dieser Parameter kann eines der vordefinierten Zwischenablageformate oder der von der nativen Windows [RegisterClipboardFormat-Funktion](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) zurückgegebene Wert sein.

*lpStgMedium*<br/>
Verweist auf eine [STGMEDIUM-Struktur,](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) die Daten empfängt.

*lpFormatEtc*<br/>
Verweist auf eine [FORMATETC-Struktur,](/windows/win32/api/objidl/ns-objidl-formatetc) die das Format beschreibt, in dem Daten zurückgegeben werden sollen. Geben Sie einen Wert für diesen Parameter an, wenn Sie zusätzliche Formatinformationen angeben möchten, die über das von *cfFormat*angegebene Zwischenablageformat hinausgehen. Wenn es NULL ist, werden die Standardwerte `FORMATETC` für die anderen Felder in der Struktur verwendet.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [IDataObject::GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata), [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)und [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) im Windows SDK.

Weitere Informationen finden Sie unter [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) im Windows SDK.

## <a name="coledataobjectgetfiledata"></a><a name="getfiledata"></a>COleDataObject::GetFileData

Rufen Sie diese `CFile` Funktion `CFile`auf, um ein oder -abgeleitetes `CFile` Objekt zu erstellen und Daten im angegebenen Format in einen Zeiger abzurufen.

```
CFile* GetFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parameter

*cfFormat*<br/>
Das Format, in dem Daten zurückgegeben werden sollen. Dieser Parameter kann eines der vordefinierten Zwischenablageformate oder der von der nativen Windows [RegisterClipboardFormat-Funktion](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) zurückgegebene Wert sein.

*lpFormatEtc*<br/>
Verweist auf eine [FORMATETC-Struktur,](/windows/win32/api/objidl/ns-objidl-formatetc) die das Format beschreibt, in dem Daten zurückgegeben werden sollen. Geben Sie einen Wert für diesen Parameter an, wenn Sie zusätzliche Formatinformationen angeben möchten, die über das von *cfFormat*angegebene Zwischenablageformat hinausgehen. Wenn es NULL ist, werden die Standardwerte `FORMATETC` für die anderen Felder in der Struktur verwendet.

### <a name="return-value"></a>Rückgabewert

Zeiger auf das `CFile` `CFile`neue oder -abgeleitete Objekt, das die Daten enthält, wenn erfolgreich; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Je nach Medium, in dem die Daten gespeichert werden, kann `CFile` `CSharedFile`der `COleStreamFile`tatsächliche Typ, auf den der Rückgabewert zeigt, , oder sein.

> [!NOTE]
> Das `CFile` Objekt, auf das über den Rückgabewert dieser Funktion zugegriffen wird, gehört dem Aufrufer. Es liegt in der Verantwortung **delete** des `CFile` Aufrufers, das Objekt zu löschen und damit die Datei zu schließen.

Weitere Informationen finden Sie unter [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) im Windows SDK.

Weitere Informationen finden Sie unter [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) im Windows SDK.

## <a name="coledataobjectgetglobaldata"></a><a name="getglobaldata"></a>COleDataObject::GetGlobalData

Rufen Sie diese Funktion auf, um einen globalen Speicherblock zuzuweisen und Daten im angegebenen Format in einem HGLOBAL abzurufen.

```
HGLOBAL GetGlobalData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parameter

*cfFormat*<br/>
Das Format, in dem Daten zurückgegeben werden sollen. Dieser Parameter kann eines der vordefinierten Zwischenablageformate oder der von der nativen Windows [RegisterClipboardFormat-Funktion](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) zurückgegebene Wert sein.

*lpFormatEtc*<br/>
Verweist auf eine [FORMATETC-Struktur,](/windows/win32/api/objidl/ns-objidl-formatetc) die das Format beschreibt, in dem Daten zurückgegeben werden sollen. Geben Sie einen Wert für diesen Parameter an, wenn Sie zusätzliche Formatinformationen angeben möchten, die über das von *cfFormat*angegebene Zwischenablageformat hinausgehen. Wenn es NULL ist, werden die Standardwerte `FORMATETC` für die anderen Felder in der Struktur verwendet.

### <a name="return-value"></a>Rückgabewert

Das Handle des globalen Speicherblocks, der die Daten enthält, wenn dies erfolgreich ist; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) im Windows SDK.

Weitere Informationen finden Sie unter [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) im Windows SDK.

## <a name="coledataobjectgetnextformat"></a><a name="getnextformat"></a>COleDataObject::GetNextFormat

Rufen Sie diese Funktion wiederholt auf, um alle Formate abzurufen, die zum Abrufen von Daten aus dem Element verfügbar sind.

```
BOOL GetNextFormat(LPFORMATETC lpFormatEtc);
```

### <a name="parameters"></a>Parameter

*lpFormatEtc*<br/>
Zeigt auf die [FORMATETC-Struktur,](/windows/win32/api/objidl/ns-objidl-formatetc) die die Formatinformationen empfängt, wenn der Funktionsaufruf zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn ein anderes Format verfügbar ist; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Nach einem Aufruf von [COleDataObject::BeginEnumFormats](#beginenumformats)wird die Position des ersten Formats gespeichert, das von diesem Datenobjekt unterstützt wird. Aufeinanderfolgende `GetNextFormat` Aufrufe an werden die Liste der verfügbaren Formate im Datenobjekt auflisten. Verwenden Sie diese Funktionen, um die verfügbaren Formate aufzulisten.

Um die Verfügbarkeit eines bestimmten Formats zu überprüfen, rufen Sie [COleDataObject::IsDataAvailable](#isdataavailable)auf.

Weitere Informationen finden Sie unter [IEnumXXXX::Next](/previous-versions//ms695273\(v=vs.85\)) im Windows SDK.

## <a name="coledataobjectisdataavailable"></a><a name="isdataavailable"></a>COleDataObject::IsDataverfügbar

Rufen Sie diese Funktion auf, um zu ermitteln, ob ein bestimmtes Format zum Abrufen von Daten aus dem OLE-Element verfügbar ist.

```
BOOL IsDataAvailable(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parameter

*cfFormat*<br/>
Das Datenformat zwischen der Ablage, das in der Struktur verwendet werden soll, auf die *lpFormatEtc*zeigt. Dieser Parameter kann eines der vordefinierten Zwischenablageformate oder der von der nativen Windows [RegisterClipboardFormat-Funktion](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) zurückgegebene Wert sein.

*lpFormatEtc*<br/>
Zeigt auf eine [FORMATETC-Struktur,](/windows/win32/api/objidl/ns-objidl-formatetc) die das gewünschte Format beschreibt. Geben Sie einen Wert für diesen Parameter nur an, wenn Sie zusätzliche Formatinformationen angeben möchten, die über das von *cfFormat*angegebene Zwischenablageformat hinausgehen. Wenn es NULL ist, werden die Standardwerte `FORMATETC` für die anderen Felder in der Struktur verwendet.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn Daten im angegebenen Format verfügbar sind; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Funktion ist `GetData`vor `GetFileData`dem `GetGlobalData`Aufrufen von , oder nützlich.

Weitere Informationen finden Sie unter [IDataObject::QueryGetData](/windows/win32/api/objidl/nf-objidl-idataobject-querygetdata) und [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) im Windows SDK.

Weitere Informationen finden Sie unter [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) im Windows SDK.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CRichEditView::QueryAcceptData](../../mfc/reference/cricheditview-class.md#queryacceptdata).

## <a name="coledataobjectrelease"></a><a name="release"></a>COleDataObject::Release

Rufen Sie diese Funktion auf, um den Besitz des `COleDataObject` [IDataObject-Objekts](/windows/win32/api/objidl/nn-objidl-idataobject) freizugeben, das zuvor dem Objekt zugeordnet war.

```
void Release();
```

### <a name="remarks"></a>Bemerkungen

Der `IDataObject` wurde dem `COleDataObject` durch `Attach` `AttachClipboard` Aufruf oder explizit oder durch das Framework zugeordnet. Wenn der *bAutoRelease-Parameter* `Attach` von `IDataObject` FALSE ist, wird das Objekt nicht freigegeben. In diesem Fall ist der Aufrufer `IDataObject` für die Freigabe der durch Aufrufen von [IUnknown::Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)verantwortlich.

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[COleDataSource-Klasse](../../mfc/reference/coledatasource-class.md)<br/>
[COleClientItem-Klasse](../../mfc/reference/coleclientitem-class.md)<br/>
[COleServerItem-Klasse](../../mfc/reference/coleserveritem-class.md)
