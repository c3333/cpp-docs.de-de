---
title: Cfont-Klasse
ms.date: 11/04/2016
f1_keywords:
- CFont
- AFXWIN/CFont
- AFXWIN/CFont::CFont
- AFXWIN/CFont::CreateFont
- AFXWIN/CFont::CreateFontIndirect
- AFXWIN/CFont::CreatePointFont
- AFXWIN/CFont::CreatePointFontIndirect
- AFXWIN/CFont::FromHandle
- AFXWIN/CFont::GetLogFont
helpviewer_keywords:
- CFont [MFC], CFont
- CFont [MFC], CreateFont
- CFont [MFC], CreateFontIndirect
- CFont [MFC], CreatePointFont
- CFont [MFC], CreatePointFontIndirect
- CFont [MFC], FromHandle
- CFont [MFC], GetLogFont
ms.assetid: 3fad6bfe-d6ce-4ab9-967a-5ce0aa102800
ms.openlocfilehash: c37b2f657105e0065e0cddb2c508424bd6c89b0a
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424392"
---
# <a name="cfont-class"></a>Cfont-Klasse

Kapselt eine Schriftart der Windows GDI (Graphics Device Interface) und stellt Memberfunktionen zum Bearbeiten der Schriftart bereit.

## <a name="syntax"></a>Syntax

```
class CFont : public CGdiObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[CFont:: CFont](#cfont)|Erstellt ein `CFont`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[CFont:: kreatefont](#createfont)|Initialisiert eine `CFont` mit den angegebenen Merkmalen.|
|[CFont:: kreatefontindirekte](#createfontindirect)|Initialisiert ein `CFont`-Objekt mit den in einer `LOGFONT`-Struktur angegebenen Merkmalen.|
|[CFont:: kreatepointfont](#createpointfont)|Initialisiert eine `CFont` mit der angegebenen Höhe, gemessen in Zehntel eines Punkts und Schriftart.|
|[CFont:: kreatepointfontindirekte](#createpointfontindirect)|Identisch mit `CreateFontIndirect`, mit der Ausnahme, dass die Schrift Höhe in Zehntel eines Punkts und nicht in logischen Einheiten gemessen wird.|
|[CFont:: FromHandle](#fromhandle)|Gibt einen Zeiger auf ein `CFont` Objekt zurück, wenn ein Windows-hFont angegeben ist.|
|[CFont:: getlogfont](#getlogfont)|Füllt eine `LOGFONT` mit Informationen über die logische Schriftart, die an das `CFont` Objekt angefügt ist.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|Beschreibung|
|----------|-----------------|
|[CFont:: Operator hFont](#operator_hfont)|Gibt das an das `CFont` Objekt angefügte Windows GDI-Schriftart Handle zurück.|

## <a name="remarks"></a>Hinweise

Wenn Sie ein `CFont` Objekt verwenden möchten, erstellen Sie ein `CFont` Objekt, und fügen Sie ihm eine Windows-Schriftart mit " [anatefont](#createfont)", " [kreatefontindirekte](#createfontindirect)", " [anatepointfont](#createpointfont)" oder " [kreatepointfontindirekte](#createpointfontindirect)" hinzu, und verwenden Sie dann die Member-Funktionen des Objekts, um die Schriftart

Die Funktionen `CreatePointFont` und `CreatePointFontIndirect` sind häufig einfacher zu verwenden als `CreateFont` oder `CreateFontIndirect`, da Sie die Konvertierung für die Höhe der Schriftart von einer Punktgröße in logische Einheiten automatisch durchführen.

Weitere Informationen zu `CFont`finden Sie unter [Graphic Objects](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CFont`

## <a name="requirements"></a>Voraussetzungen

**Header:** afxwin.h

##  <a name="cfont"></a>CFont:: CFont

Erstellt ein `CFont`-Objekt.

```
CFont();
```

### <a name="remarks"></a>Hinweise

Das resultierende Objekt muss mit `CreateFont`, `CreateFontIndirect`, `CreatePointFont`oder `CreatePointFontIndirect` initialisiert werden, bevor es verwendet werden kann.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#70](../../mfc/codesnippet/cpp/cfont-class_1.cpp)]

##  <a name="createfont"></a>CFont:: kreatefont

Initialisiert ein `CFont`-Objekt mit den angegebenen Merkmalen.

```
BOOL CreateFont(
    int nHeight,
    int nWidth,
    int nEscapement,
    int nOrientation,
    int nWeight,
    BYTE bItalic,
    BYTE bUnderline,
    BYTE cStrikeOut,
    BYTE nCharSet,
    BYTE nOutPrecision,
    BYTE nClipPrecision,
    BYTE nQuality,
    BYTE nPitchAndFamily,
    LPCTSTR lpszFacename);
```

### <a name="parameters"></a>Parameter

*nheight*<br/>
Gibt die gewünschte Höhe (in logischen Einheiten) der Schriftart an. Eine Beschreibung finden Sie in der `lfHeight`-Member der [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)-Struktur im Windows SDK. Der absolute Wert von *nheight* darf 16.384 Geräte Einheiten nicht überschreiten, nachdem er konvertiert wurde. Bei allen Höhen vergleichen sucht die Schriftart Mapper nach der größten Schriftart, die die angeforderte Größe nicht überschreitet, oder die kleinste Schriftart, wenn alle Schriftarten die angeforderte Größe überschreiten.

*nwidth*<br/>
Gibt die durchschnittliche Breite (in logischen Einheiten) der Zeichen in der Schriftart an. Wenn *nwidth* gleich 0 ist, wird das Seitenverhältnis des Geräts mit dem Seitenverhältnis für die Digitalisierung der verfügbaren Schriftarten abgeglichen, um die nächstgelegene Übereinstimmung zu ermitteln, die durch den absoluten Wert der Differenz bestimmt wird.

*nescapeselement*<br/>
Gibt den Winkel (in 0,1-Grad-Einheiten) zwischen dem escapesvevektor und der x-Achse der Anzeige Oberfläche an. Der escapevektor ist die Linie durch die Ursprünge der ersten und letzten Zeichen in einer Zeile. Der Winkel wird gegen den Uhrzeigersinn von der x-Achse aus gemessen. Weitere Informationen finden Sie in der `lfEscapement`-Member in der `LOGFONT`-Struktur im Windows SDK.

*nausrichtung*<br/>
Gibt den Winkel (in Einheiten von 0,1 Grad) zwischen der Baseline eines Zeichens und der x-Achse an. Der Winkel wird gegen den Uhrzeigersinn von der x-Achse für Koordinatensysteme gemessen, bei denen die y-Richtung nach unten und im Uhrzeigersinn von der x-Achse für Koordinatensysteme liegt, in denen die y-Richtung aktiv ist.

*ngewichtung*<br/>
Gibt die Schrift Breite an (in gezeichneten Pixel pro 1000). Weitere Informationen finden Sie unter *lfWeight* -Member in der `LOGFONT` Struktur in der Windows SDK. Die beschriebenen Werte sind ungefähre Werte. die tatsächliche Darstellung hängt von der Schriftart ab. Einige Schriftarten haben nur FW_NORMAL, FW_REGULAR und FW_BOLD Gewichtungen. Wenn FW_DONTCARE angegeben wird, wird eine Standard Gewichtung verwendet.

*bitalic*<br/>
Gibt an, ob die Schriftart kursiv formatiert ist.

*bunter Streichung*<br/>
Gibt an, ob die Schriftart unterstrichen ist.

*cstrikeout*<br/>
Gibt an, ob Zeichen in der Schriftart abgeblendet werden. Gibt eine durchgestrichen festgelegte Schriftart an, wenn Sie auf einen Wert ungleich NULL festgelegt ist.

*ncharset*<br/>
Gibt das Zeichen der Schriftart an setsee das `lfCharSet` Element in der `LOGFONT` Struktur im Windows SDK für eine Liste von Werten.

Der OEM-Zeichensatz ist System abhängig.

Schriftarten mit anderen Zeichensätzen können im System vorhanden sein. Eine Anwendung, die eine Schriftart mit einem unbekannten Zeichensatz verwendet, darf nicht versuchen, Zeichen folgen zu übersetzen oder zu interpretieren, die mit dieser Schriftart gerendert werden sollen. Stattdessen sollten die Zeichen folgen direkt an den Ausgabegeräte Treiber übermittelt werden.

Der Schriftart-Mapper verwendet nicht den DEFAULT_CHARSET Wert. Eine Anwendung kann diesen Wert verwenden, um den Namen und die Größe einer Schriftart zum vollständigen beschreiben der logischen Schriftart zuzulassen. Wenn keine Schriftart mit dem angegebenen Namen vorhanden ist, kann eine Schriftart eines beliebigen Zeichensatzes für die angegebene Schriftart ersetzt werden. Um unerwartete Ergebnisse zu vermeiden, sollten Anwendungen den DEFAULT_CHARSET Wert sparsam verwenden.

*noutprecision*<br/>
Gibt die gewünschte Ausgabe Genauigkeit an. Die Ausgabe Genauigkeit definiert, wie genau die Ausgabe mit der Höhe, Breite, Zeichen Ausrichtung, dem Escapezeichen und der Tonhöhe der angeforderten Schriftart übereinstimmen muss. Eine Liste der Werte und weitere Informationen finden Sie in der `lfOutPrecision`-Member in der `LOGFONT`-Struktur im Windows SDK.

*nclipprecision*<br/>
Gibt die gewünschte clippinggenauigkeit an. Die clippinggenauigkeit definiert, wie Zeichen abgeschnitten werden, die sich teilweise außerhalb des Clippingbereichs befinden. Eine Liste mit Werten finden Sie in der `lfClipPrecision`-Element in der `LOGFONT`-Struktur im Windows SDK.

Um eine eingebettete schreibgeschützte Schriftart zu verwenden, muss eine Anwendung CLIP_ENCAPSULATE angeben.

Um eine konsistente Drehung von Gerät, TrueType und Vektor Schriftarten zu erreichen, kann eine Anwendung den-Operator oder den-Operator verwenden, um den CLIP_LH_ANGLES Wert mit einem der anderen *nclipprecision* -Werte zu kombinieren. Wenn das CLIP_LH_ANGLES Bit festgelegt ist, hängt die Drehung für alle Schriftarten davon ab, ob die Ausrichtung des Koordinatensystems Links oder rechts übergeben ist. (Weitere Informationen zur Ausrichtung von Koordinatensystemen finden Sie in der Beschreibung des *norientation* -Parameters.) Wenn CLIP_LH_ANGLES nicht festgelegt ist, drehen sich Geräte Schriftarten immer gegen den Uhrzeigersinn, aber die Drehung anderer Schriftarten hängt von der Ausrichtung des Koordinatensystems ab.

*nqualität*<br/>
Gibt die Ausgabequalität der Schriftart an, mit der definiert wird, wie sorgfältig der GDI versuchen muss, die Attribute der logischen Schriftart mit denen einer tatsächlichen physischen Schriftart abzugleichen. Eine Liste mit Werten finden Sie in der `lfQuality`-Element in der `LOGFONT`-Struktur im Windows SDK.

*npitchandfamily*<br/>
Gibt Dichte und Familie der Schriftart an. Eine Liste der Werte und weitere Informationen finden Sie in der `lfPitchAndFamily`-Member in der `LOGFONT`-Struktur im Windows SDK.

*lpszfakename*<br/>
Ein `CString` oder Zeiger auf eine mit NULL endenden Zeichenfolge, die den Schriftart Namen der Schriftart angibt. Die Länge dieser Zeichenfolge darf nicht länger als 30 Zeichen sein. Die Windows [EnumFontFamilies](/windows/win32/api/wingdi/nf-wingdi-enumfontfamiliesw) -Funktion kann verwendet werden, um alle zurzeit verfügbaren Schriftarten aufzulisten. Wenn *lpszfakename* den Wert NULL hat, verwendet der GDI eine geräteunabhängige Schriftart.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Anschließend kann die Schriftart als Schriftart für beliebige Geräte Kontexte ausgewählt werden.

Die `CreateFont`-Funktion erstellt keine neue Windows-GDI-Schriftart. Es wählt lediglich die nächstgelegene Übereinstimmung der physischen Schriftarten aus, die für das GDI verfügbar sind.

Anwendungen können beim Erstellen einer logischen Schriftart die Standardeinstellungen für die meisten Parameter verwenden. Die Parameter, die immer bestimmte Werte erhalten sollten, sind *nheight* und *lpszfakename*. Wenn *nheight* und *lpszfakename* nicht von der Anwendung festgelegt werden, ist die erstellte logische Schriftart Geräte abhängig.

Wenn Sie mit dem `CFont` Objekt fertig sind, das von der `CreateFont`-Funktion erstellt wurde, verwenden Sie `CDC::SelectObject`, um eine andere Schriftart in den Gerätekontext auszuwählen, und löschen Sie dann das `CFont` Objekt, das nicht mehr benötigt wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#71](../../mfc/codesnippet/cpp/cfont-class_2.cpp)]

##  <a name="createfontindirect"></a>CFont:: kreatefontindirekte

Initialisiert ein `CFont`-Objekt mit den in einer [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)-Struktur angegebenen Merkmalen.

```
BOOL CreateFontIndirect(const LOGFONT* lpLogFont);
```

### <a name="parameters"></a>Parameter

*lplogfont*<br/>
Verweist auf eine `LOGFONT`-Struktur, die die Merkmale der logischen Schriftart definiert.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Die Schriftart kann anschließend als aktuelle Schriftart für ein beliebiges Gerät ausgewählt werden.

Diese Schriftart verfügt über die Eigenschaften, die in der [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) -Struktur angegeben sind. Wenn die Schriftart mithilfe der [CDC:: SelectObject](../../mfc/reference/cdc-class.md#selectobject) -Member-Funktion ausgewählt wird, versucht der GDI-Schriftart-Mapper, die logische Schriftart mit einer vorhandenen physischen Schriftart abzugleichen. Wenn der Schriftart-Mapper keine genaue Entsprechung für die logische Schriftart findet, stellt er eine Alternative Schriftart bereit, deren Merkmale so viele der angeforderten Merkmale wie möglich entsprechen.

Wenn Sie das `CFont` Objekt, das von der `CreateFontIndirect`-Funktion erstellt wurde, nicht mehr benötigen, verwenden Sie `CDC::SelectObject`, um eine andere Schriftart in den Gerätekontext auszuwählen, und löschen Sie dann das `CFont` Objekt, das nicht mehr benötigt wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#72](../../mfc/codesnippet/cpp/cfont-class_3.cpp)]

##  <a name="createpointfont"></a>CFont:: kreatepointfont

Diese Funktion bietet eine einfache Möglichkeit, eine Schriftart einer angegebenen Schriftart und Punktgröße zu erstellen.

```
BOOL CreatePointFont(
    int nPointSize,
    LPCTSTR lpszFaceName,
    CDC* pDC = NULL);
```

### <a name="parameters"></a>Parameter

*npointsize*<br/>
Die angeforderte Schrift Höhe in Zehntel eines Punkts. (Geben Sie beispielsweise 120 ein, um eine Schriftart mit 12 Punkten anzufordern.)

*lpszfakename*<br/>
Ein `CString` oder Zeiger auf eine mit NULL endenden Zeichenfolge, die den Schriftart Namen der Schriftart angibt. Die Länge dieser Zeichenfolge darf nicht länger als 30 Zeichen sein. Die Windows ' EnumFontFamilies-Funktion kann verwendet werden, um alle zurzeit verfügbaren Schriftarten aufzulisten. Wenn *lpszfakename* den Wert NULL hat, verwendet der GDI eine geräteunabhängige Schriftart.

*pDC*<br/>
Zeiger auf das [CDC](../../mfc/reference/cdc-class.md) -Objekt, das zum Konvertieren der Höhe in *npointsize* in logische Einheiten verwendet werden soll. Wenn der Wert NULL ist, wird ein Bildschirm-Gerätekontext für die Konvertierung verwendet.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Hinweise

Die Höhe in *npointsize* wird automatisch in logische Einheiten konvertiert, indem das CDC-Objekt verwendet wird, auf das *PDC*verweist.

Wenn Sie mit dem `CFont` Objekt fertig sind, das von der `CreatePointFont`-Funktion erstellt wurde, wählen Sie zunächst die Schriftart aus dem Gerätekontext aus, und löschen Sie dann das `CFont`-Objekt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#73](../../mfc/codesnippet/cpp/cfont-class_4.cpp)]

##  <a name="createpointfontindirect"></a>CFont:: kreatepointfontindirekte

Diese Funktion ist mit dem Wert von " [kreatefontindirekte](#createfontindirect) " identisch, mit der Ausnahme, dass der `lfHeight` Member des `LOGFONT` in den zehntelpunkten statt in den Geräte Einheiten interpretiert wird.

```
BOOL CreatePointFontIndirect(
    const LOGFONT* lpLogFont,
    CDC* pDC = NULL);
```

### <a name="parameters"></a>Parameter

*lplogfont*<br/>
Verweist auf eine [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) -Struktur, die die Merkmale der logischen Schriftart definiert. Der `lfHeight` Member der `LOGFONT` Struktur wird in Zehntel eines Punkts gemessen, nicht als logische Einheiten. (Legen Sie beispielsweise `lfHeight` auf 120 fest, um eine Schriftart mit 12 Punkten anzufordern.)

*pDC*<br/>
Zeiger auf das [CDC](../../mfc/reference/cdc-class.md) -Objekt, das zum Konvertieren der Höhe in `lfHeight` in logische Einheiten verwendet werden soll. Wenn der Wert NULL ist, wird ein Bildschirm-Gerätekontext für die Konvertierung verwendet.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Hinweise

Diese Funktion konvertiert die Höhe in `lfHeight` automatisch in logische Einheiten, indem das CDC-Objekt verwendet wird, auf das *PDC* verweist, bevor die `LOGFONT` Struktur an Windows übergeben wird.

Wenn Sie mit dem `CFont` Objekt fertig sind, das von der `CreatePointFontIndirect`-Funktion erstellt wurde, wählen Sie zunächst die Schriftart aus dem Gerätekontext aus, und löschen Sie dann das `CFont`-Objekt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#74](../../mfc/codesnippet/cpp/cfont-class_5.cpp)]

##  <a name="fromhandle"></a>CFont:: FromHandle

Gibt einen Zeiger auf ein `CFont` Objekt zurück, wenn ein hFont-Handle für ein Windows-GDI-Schriftart Objekt angegeben wird.

```
static CFont* PASCAL FromHandle(HFONT hFont);
```

### <a name="parameters"></a>Parameter

*hFont*<br/>
Ein hFont-Handle für eine Windows-Schriftart.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein `CFont` Objekt, wenn erfolgreich. andernfalls NULL.

### <a name="remarks"></a>Hinweise

Wenn ein `CFont` Objekt noch nicht an das Handle angefügt ist, wird ein temporäres `CFont` Objekt erstellt und angefügt. Dieses temporäre `CFont` Objekt ist nur gültig, bis das nächste Mal die Leerlaufzeit der Anwendung in der Ereignisschleife liegt. zu diesem Zeitpunkt werden alle temporären Grafik Objekte gelöscht. Eine andere Möglichkeit, dies zu sagen, besteht darin, dass das temporäre Objekt nur während der Verarbeitung einer Fenster Nachricht gültig ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#75](../../mfc/codesnippet/cpp/cfont-class_6.cpp)]

##  <a name="getlogfont"></a>CFont:: getlogfont

Rufen Sie diese Funktion auf, um eine Kopie der `LOGFONT` Struktur für `CFont`abzurufen.

```
int GetLogFont(LOGFONT* pLogFont);
```

### <a name="parameters"></a>Parameter

*plogfont*<br/>
Ein Zeiger auf die [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) -Struktur zum Empfangen der Schriftart Informationen.

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn die Funktion erfolgreich ausgeführt wird, andernfalls 0.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#76](../../mfc/codesnippet/cpp/cfont-class_7.cpp)]

##  <a name="operator_hfont"></a>CFont:: Operator hFont

Verwenden Sie diesen Operator, um das Windows-GDI-Handle der an das `CFont` Objekt angefügten Schriftart zu erhalten.

```
operator HFONT() const;
```

### <a name="return-value"></a>Rückgabewert

Das Handle des Windows GDI-Schriftart Objekts, das an `CFont` angefügt ist, wenn erfolgreich. andernfalls NULL.

### <a name="remarks"></a>Hinweise

Da dieser Operator automatisch für Konvertierungen von `CFont` in [Schriftarten und Text](/windows/win32/gdi/fonts-and-text)verwendet wird, können Sie `CFont` Objekte an Funktionen übergeben, die hfonts erwarten.

Weitere Informationen zum Verwenden von Grafikobjekten finden Sie unter [Graphic Objects](/windows/win32/gdi/graphic-objects) in the Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#77](../../mfc/codesnippet/cpp/cfont-class_8.cpp)]

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel Hierarchien](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject-Klasse](../../mfc/reference/cgdiobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
