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
ms.openlocfilehash: e9cb8c452cc3eea32b6eed9bf23fb454344c105d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214086"
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
|[COleDataObject:: COleDataObject](#coledataobject)|Erstellt ein `COleDataObject`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[COleDataObject:: Attach](#attach)|Fügt das angegebene OLE-Datenobjekt an das-Objekt an `COleDataObject` .|
|[COleDataObject:: AttachClipboard](#attachclipboard)|Fügt das Datenobjekt an, das sich in der Zwischenablage befindet.|
|[COleDataObject:: BeginEnumFormats](#beginenumformats)|Bereitet mindestens einen nachfolgenden `GetNextFormat` Aufruf vor.|
|[COleDataObject::D Etach](#detach)|Trennt das zugeordnete- `IDataObject` Objekt.|
|[COleDataObject:: GetData](#getdata)|Kopiert Daten aus dem angefügten OLE-Datenobjekt in einem angegebenen Format.|
|[COleDataObject:: GetFileData](#getfiledata)|Kopiert Daten aus dem angefügten OLE-Datenobjekt in einen `CFile` Zeiger im angegebenen Format.|
|[COleDataObject:: getglobaldata](#getglobaldata)|Kopiert Daten aus dem angefügten OLE-Datenobjekt in ein-Objekt `HGLOBAL` im angegebenen Format.|
|[COleDataObject:: getnextformat](#getnextformat)|Gibt das nächste verfügbare Datenformat zurück.|
|[COleDataObject:: IsDataAvailable](#isdataavailable)|Überprüft, ob Daten in einem angegebenen Format verfügbar sind.|
|[COleDataObject:: Release](#release)|Trennt das zugeordnete-Objekt und gibt es frei `IDataObject` .|

## <a name="remarks"></a>Bemerkungen

`COleDataObject`weist keine Basisklasse auf.

Diese Arten von Datenübertragungen umfassen eine Quelle und ein Ziel. Die Datenquelle wird als Objekt der [COleDataSource](../../mfc/reference/coledatasource-class.md) -Klasse implementiert. Wenn in einer Zielanwendung Daten abgelegt werden oder Sie zur Ausführung eines Einfügevorgangs aus der Zwischenablage aufgefordert werden, muss ein Objekt der `COleDataObject` Klasse erstellt werden.

Mit dieser Klasse können Sie ermitteln, ob die Daten in einem angegebenen Format vorhanden sind. Sie können auch die verfügbaren Datenformate auflisten oder überprüfen, ob ein bestimmtes Format verfügbar ist, und dann die Daten im bevorzugten Format abrufen. Das Abrufen von Objekten kann auf verschiedene Weise durchgeführt werden, einschließlich der Verwendung einer [CFile](../../mfc/reference/cfile-class.md)-, einer HGLOBAL-oder einer- `STGMEDIUM` Struktur.

Weitere Informationen finden Sie unter der [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) -Struktur in der Windows SDK.

Weitere Informationen zum Verwenden von Datenobjekten in der Anwendung finden Sie im Artikel [Datenobjekte und Datenquellen (OLE)](../../mfc/data-objects-and-data-sources-ole.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`COleDataObject`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Afxole. h

## <a name="coledataobjectattach"></a><a name="attach"></a>COleDataObject:: Attach

Diese Funktion wird aufgerufen, um das `COleDataObject` Objekt einem OLE-Datenobjekt zuzuordnen.

```cpp
void Attach(
    LPDATAOBJECT lpDataObject,
    BOOL bAutoRelease = TRUE);
```

### <a name="parameters"></a>Parameter

*lpdataobject*<br/>
Verweist auf ein OLE-Datenobjekt.

*bautoriase*<br/>
TRUE, wenn das OLE-Datenobjekt freigegeben werden soll, wenn das `COleDataObject` Objekt zerstört wird; andernfalls false.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) in der Windows SDK.

## <a name="coledataobjectattachclipboard"></a><a name="attachclipboard"></a>COleDataObject:: AttachClipboard

Mit dieser Funktion wird das Datenobjekt, das sich derzeit in der Zwischenablage befindet, an das-Objekt angefügt `COleDataObject` .

```
BOOL AttachClipboard();
```

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Durch Aufrufen dieser Funktion wird die Zwischenablage gesperrt, bis dieses Datenobjekt freigegeben wird. Das Datenobjekt wird im Dekonstruktor für den freigegeben `COleDataObject` . Weitere Informationen finden Sie unter [OpenClipboard](/windows/win32/api/winuser/nf-winuser-openclipboard) und [CloseClipboard](/windows/win32/api/winuser/nf-winuser-closeclipboard) in der Win32-Dokumentation.

## <a name="coledataobjectbeginenumformats"></a><a name="beginenumformats"></a>COleDataObject:: BeginEnumFormats

Rufen Sie diese Funktion auf, um nachfolgende Aufrufe von `GetNextFormat` für das Abrufen einer Liste von Datenformaten aus dem Element vorzubereiten.

```cpp
void BeginEnumFormats();
```

### <a name="remarks"></a>Bemerkungen

Nach einem-Rückruf `BeginEnumFormats` wird die Position des ersten von diesem Datenobjekt unterstützten Formats gespeichert. Bei aufeinander folgenden Aufrufen `GetNextFormat` von wird die Liste der verfügbaren Formate im Datenobjekt aufgelistet.

Um die Verfügbarkeit von Daten in einem bestimmten Format zu überprüfen, verwenden Sie [COleDataObject:: IsDataAvailable](#isdataavailable).

Weitere Informationen finden Sie unter [IDataObject:: EnumFormatEtc](/windows/win32/api/objidl/nf-objidl-idataobject-enumformatetc) in der Windows SDK.

## <a name="coledataobjectcoledataobject"></a><a name="coledataobject"></a>COleDataObject:: COleDataObject

Erstellt ein `COleDataObject`-Objekt.

```
COleDataObject();
```

### <a name="remarks"></a>Bemerkungen

Ein Aufruf von [COleDataObject:: Attach](#attach) oder [COleDataObject:: AttachClipboard](#attachclipboard) muss erfolgen, bevor andere Funktionen aufgerufen werden `COleDataObject` .

> [!NOTE]
> Da einer der Parameter für die Drag & Drop-Handler ein Zeiger auf eine ist `COleDataObject` , ist es nicht erforderlich, diesen Konstruktor aufzurufen, um Drag & Drop zu unterstützen.

## <a name="coledataobjectdetach"></a><a name="detach"></a>COleDataObject::D Etach

Diese Funktion wird aufgerufen, um das `COleDataObject` Objekt vom zugeordneten OLE-Datenobjekt zu trennen, ohne das Datenobjekt freizugeben.

```
LPDATAOBJECT Detach();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das OLE-Datenobjekt, das getrennt wurde.

### <a name="remarks"></a>Bemerkungen

## <a name="coledataobjectgetdata"></a><a name="getdata"></a>COleDataObject:: GetData

Rufen Sie diese Funktion auf, um Daten aus dem Element im angegebenen Format abzurufen.

```
BOOL GetData(
    CLIPFORMAT cfFormat,
    LPSTGMEDIUM lpStgMedium,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parameter

*cfFormat*<br/>
Das Format, in dem Daten zurückgegeben werden sollen. Dieser Parameter kann eines der vordefinierten Zwischenablage Formate oder der Wert sein, der von der systemeigenen Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) -Funktion zurückgegeben wird.

*lpstgmedium*<br/>
Verweist auf eine [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) -Struktur, die Daten empfängt.

*lpformatusw.*<br/>
Verweist auf eine [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) -Struktur, die das Format beschreibt, in dem die Daten zurückgegeben werden sollen. Geben Sie einen Wert für diesen Parameter an, wenn Sie zusätzliche Formatierungsinformationen angeben möchten, die über das in *cfFormat*angegebene Zwischenablage Format hinausgehen. Wenn er NULL ist, werden die Standardwerte für die anderen Felder in der- `FORMATETC` Struktur verwendet.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata), [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)und [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) in der Windows SDK.

Weitere Informationen finden Sie unter [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) im Windows SDK.

## <a name="coledataobjectgetfiledata"></a><a name="getfiledata"></a>COleDataObject:: GetFileData

Rufen Sie diese Funktion auf, um ein `CFile` `CFile` -oder-abgeleitetes Objekt zu erstellen und um Daten im angegebenen Format in einen- `CFile` Zeiger abzurufen.

```
CFile* GetFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parameter

*cfFormat*<br/>
Das Format, in dem Daten zurückgegeben werden sollen. Dieser Parameter kann eines der vordefinierten Zwischenablage Formate oder der Wert sein, der von der systemeigenen Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) -Funktion zurückgegeben wird.

*lpformatusw.*<br/>
Verweist auf eine [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) -Struktur, die das Format beschreibt, in dem die Daten zurückgegeben werden sollen. Geben Sie einen Wert für diesen Parameter an, wenn Sie zusätzliche Formatierungsinformationen angeben möchten, die über das in *cfFormat*angegebene Zwischenablage Format hinausgehen. Wenn er NULL ist, werden die Standardwerte für die anderen Felder in der- `FORMATETC` Struktur verwendet.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das neue `CFile` oder von `CFile` abgeleitete Objekt, das die Daten enthält, wenn erfolgreich; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Abhängig vom Medium, in dem die Daten gespeichert werden, kann der tatsächliche Typ, auf den der Rückgabewert verweist, `CFile` , `CSharedFile` oder sein `COleStreamFile` .

> [!NOTE]
> Das Objekt, auf das der `CFile` Rückgabewert dieser Funktion zugreift, ist im Besitz des Aufrufers. Es liegt in der Verantwortung des Aufrufers des- **`delete`** `CFile` Objekts, die Datei zu schließen.

Weitere Informationen finden Sie unter [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) in der Windows SDK.

Weitere Informationen finden Sie unter [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) im Windows SDK.

## <a name="coledataobjectgetglobaldata"></a><a name="getglobaldata"></a>COleDataObject:: getglobaldata

Rufen Sie diese Funktion auf, um einen globalen Speicherblock zuzuordnen und Daten im angegebenen Format in einen HGLOBAL abzurufen.

```
HGLOBAL GetGlobalData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parameter

*cfFormat*<br/>
Das Format, in dem Daten zurückgegeben werden sollen. Dieser Parameter kann eines der vordefinierten Zwischenablage Formate oder der Wert sein, der von der systemeigenen Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) -Funktion zurückgegeben wird.

*lpformatusw.*<br/>
Verweist auf eine [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) -Struktur, die das Format beschreibt, in dem die Daten zurückgegeben werden sollen. Geben Sie einen Wert für diesen Parameter an, wenn Sie zusätzliche Formatierungsinformationen angeben möchten, die über das in *cfFormat*angegebene Zwischenablage Format hinausgehen. Wenn er NULL ist, werden die Standardwerte für die anderen Felder in der- `FORMATETC` Struktur verwendet.

### <a name="return-value"></a>Rückgabewert

Das Handle des globalen Speicherblocks, der die Daten enthält, wenn der Vorgang erfolgreich ist. andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) in der Windows SDK.

Weitere Informationen finden Sie unter [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) im Windows SDK.

## <a name="coledataobjectgetnextformat"></a><a name="getnextformat"></a>COleDataObject:: getnextformat

Rufen Sie diese Funktion wiederholt auf, um alle Formate abzurufen, die zum Abrufen von Daten aus dem Element verfügbar sind.

```
BOOL GetNextFormat(LPFORMATETC lpFormatEtc);
```

### <a name="parameters"></a>Parameter

*lpformatusw.*<br/>
Verweist auf die [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) -Struktur, die die Formatinformationen empfängt, wenn der Funktions Rückruf zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn ein anderes Format verfügbar ist. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Nach einem Aufrufen von [COleDataObject:: BeginEnumFormats](#beginenumformats)wird die Position des ersten Formats gespeichert, das von diesem Datenobjekt unterstützt wird. Bei aufeinander folgenden Aufrufen `GetNextFormat` von wird die Liste der verfügbaren Formate im Datenobjekt aufgelistet. Verwenden Sie diese Funktionen, um die verfügbaren Formate aufzulisten.

Um die Verfügbarkeit eines bestimmten Formats zu überprüfen, wenden Sie [COleDataObject:: IsDataAvailable](#isdataavailable)an.

Weitere Informationen finden Sie unter [IEnumXXXX:: Next](/previous-versions/ms695273\(v=vs.85\)) in der Windows SDK.

## <a name="coledataobjectisdataavailable"></a><a name="isdataavailable"></a>COleDataObject:: IsDataAvailable

Rufen Sie diese Funktion auf, um zu bestimmen, ob ein bestimmtes Format zum Abrufen von Daten aus dem OLE-Element verfügbar ist.

```
BOOL IsDataAvailable(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>Parameter

*cfFormat*<br/>
Das Datenformat der Zwischenablage, das in der Struktur verwendet werden soll, auf die von *lpformatetc*verwiesen wird. Dieser Parameter kann eines der vordefinierten Zwischenablage Formate oder der Wert sein, der von der systemeigenen Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) -Funktion zurückgegeben wird.

*lpformatusw.*<br/>
Verweist auf eine [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) -Struktur, die das gewünschte Format beschreibt. Geben Sie einen Wert für diesen Parameter nur an, wenn Sie zusätzliche Formatierungsinformationen über das in *cfFormat*angegebene Zwischenablage Format angeben möchten. Wenn er NULL ist, werden die Standardwerte für die anderen Felder in der- `FORMATETC` Struktur verwendet.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn Daten im angegebenen Format verfügbar sind. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Funktion ist nützlich, bevor `GetData` , `GetFileData` oder aufgerufen wird `GetGlobalData` .

Weitere Informationen finden Sie unter [IDataObject:: QueryGetData](/windows/win32/api/objidl/nf-objidl-idataobject-querygetdata) und [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) in der Windows SDK.

Weitere Informationen finden Sie unter [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) im Windows SDK.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CRichEditView:: queryakzeptdata](../../mfc/reference/cricheditview-class.md#queryacceptdata).

## <a name="coledataobjectrelease"></a><a name="release"></a>COleDataObject:: Release

Mit dieser Funktion wird der Besitz des [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) -Objekts, das zuvor dem-Objekt zugeordnet war, freigegeben `COleDataObject` .

```cpp
void Release();
```

### <a name="remarks"></a>Bemerkungen

Die `IDataObject` wurde dem zugeordnet, `COleDataObject` indem `Attach` oder `AttachClipboard` explizit oder durch das Framework aufgerufen wurde. Wenn der Parameter " *bautorelease* " von " `Attach` false" ist, `IDataObject` wird das Objekt nicht freigegeben. In diesem Fall ist der Aufrufer für das Freigeben `IDataObject` von durch Aufrufen von [IUnknown:: Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)verantwortlich.

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel Hierarchien](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[COleDataSource-Klasse](../../mfc/reference/coledatasource-class.md)<br/>
[COleClientItem-Klasse](../../mfc/reference/coleclientitem-class.md)<br/>
[COleServerItem-Klasse](../../mfc/reference/coleserveritem-class.md)
