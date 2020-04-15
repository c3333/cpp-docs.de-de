---
title: CFont-Klasse
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
ms.openlocfilehash: 36fd469b182d5f3e0d3449112d04c1a8623d7526
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373845"
---
# <a name="cfont-class"></a>CFont-Klasse

Kapselt eine Schriftart der Windows GDI (Graphics Device Interface) und stellt Memberfunktionen zum Bearbeiten der Schriftart bereit.

## <a name="syntax"></a>Syntax

```
class CFont : public CGdiObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFont::CFont](#cfont)|Erstellt ein `CFont`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFont::CreateFont](#createfont)|Initialisiert eine `CFont` mit den angegebenen Merkmalen.|
|[CFont::CreateFontIndirect](#createfontindirect)|Initialisiert ein `CFont` Objekt mit den `LOGFONT` in einer Struktur angegebenen Merkmalen.|
|[CFont::CreatePointFont](#createpointfont)|Initialisiert eine `CFont` mit der angegebenen Höhe, gemessen in Zehntel eines Punktes, und Schriftart.|
|[CFont::CreatePointFontIndirect](#createpointfontindirect)|Genauso `CreateFontIndirect` wie die Schriftgröße in Zehntel eines Punktes und nicht in logischen Einheiten gemessen wird.|
|[Cfont::FromHandle](#fromhandle)|Gibt einen Zeiger `CFont` auf ein Objekt zurück, wenn ein Windows HFONT angegeben wird.|
|[CFont::GetLogFont](#getlogfont)|Füllt eine `LOGFONT` mit Informationen über die `CFont` logische Schriftart, die dem Objekt zugeordnet ist.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFont::operator HFONT](#operator_hfont)|Gibt das windows GDI-Schriftarthandle zurück, das an das `CFont` Objekt angefügt ist.|

## <a name="remarks"></a>Bemerkungen

Um ein `CFont` Objekt zu `CFont` verwenden, erstellen Sie ein Objekt und fügen Sie ihm mit [CreateFont](#createfont), [CreateFontIndirect](#createfontindirect), [CreatePointFont](#createpointfont)oder [CreatePointFontIndirect](#createpointfontindirect)eine Windows-Schriftart an, und verwenden Sie dann die Memberfunktionen des Objekts, um die Schriftart zu bearbeiten.

Die `CreatePointFont` `CreatePointFontIndirect` und Funktionen sind oft `CreateFont` `CreateFontIndirect` einfacher zu bedienen als oder da sie die Konvertierung für die Höhe der Schriftart von einer Punktgröße in logische Einheiten automatisch durchführen.

Weitere Informationen `CFont`zu finden Sie unter [Grafikobjekte](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CFont`

## <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="cfontcfont"></a><a name="cfont"></a>CFont::CFont

Erstellt ein `CFont`-Objekt.

```
CFont();
```

### <a name="remarks"></a>Bemerkungen

Das resultierende Objekt muss `CreateFont`mit `CreateFontIndirect` `CreatePointFont`initialisiert `CreatePointFontIndirect` werden, , , oder bevor es verwendet werden kann.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#70](../../mfc/codesnippet/cpp/cfont-class_1.cpp)]

## <a name="cfontcreatefont"></a><a name="createfont"></a>CFont::CreateFont

Initialisiert ein `CFont` Objekt mit den angegebenen Merkmalen.

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

*nHeight*<br/>
Gibt die gewünschte Höhe (in logischen Einheiten) der Schriftart an. Eine `lfHeight` Beschreibung finden Sie im Element der [LOGFONT-Struktur](/windows/win32/api/wingdi/ns-wingdi-logfontw)im Windows SDK. Der absolute Wert von *nHeight* darf 16.384 Geräteeinheiten nach der Konvertierung nicht überschreiten. Bei allen Höhenvergleichen sucht der Schriftart-Mapper nach der größten Schriftart, die die angeforderte Größe oder die kleinste Schriftart nicht überschreitet, wenn alle Schriftarten die angeforderte Größe überschreiten.

*nWidth*<br/>
Gibt die durchschnittliche Breite (in logischen Einheiten) von Zeichen in der Schriftart an. Wenn *nWidth* 0 ist, wird das Seitenverhältnis des Geräts mit dem Digitalisierungsseitenverhältnis der verfügbaren Schriftarten abgeglichen, um die nächste Übereinstimmung zu finden, die durch den absoluten Wert der Differenz bestimmt wird.

*nEscapement*<br/>
Gibt den Winkel (in 0,1-Grad-Einheiten) zwischen dem Hemmungsvektor und der x-Achse der Anzeigefläche an. Der Escapement-Vektor ist die Linie durch die Ursprünge des ersten und letzten Zeichens in einer Zeile. Der Winkel wird von der x-Achse gegen den Uhrzeigersinn gemessen. Weitere `lfEscapement` Informationen finden `LOGFONT` Sie unter dem Member in der Struktur im Windows SDK.

*nOrientierung*<br/>
Gibt den Winkel (in 0,1-Grad-Einheiten) zwischen der Grundlinie eines Zeichens und der x-Achse an. Der Winkel wird gegen den Uhrzeigersinn von der x-Achse für Koordinatensysteme gemessen, in denen die y-Richtung nach unten und im Uhrzeigersinn von der x-Achse für Koordinatensysteme, in denen die y-Richtung nach oben ist, erfolgt.

*nGewicht*<br/>
Gibt die Schriftgröße an (in eingefärbten Pixeln pro 1000). Weitere Informationen finden Sie `LOGFONT` unter dem *lfWeight-Member* in der Struktur im Windows SDK. Die beschriebenen Werte sind ungefähr; das tatsächliche Erscheinungsbild hängt von der Schrift ab. Einige Schriftarten haben nur FW_NORMAL, FW_REGULAR und FW_BOLD Gewichtungen. Wenn FW_DONTCARE angegeben ist, wird eine Standardgewichtung verwendet.

*bItalic*<br/>
Gibt an, ob die Schriftart kursiv ist.

*bUnderline*<br/>
Gibt an, ob die Schriftart unterstrichen ist.

*cStrikeOut*<br/>
Gibt an, ob Zeichen in der Schriftart ausgeschlagen werden. Gibt eine Strikeout-Schriftart an, wenn sie auf einen Wert ungleich Null festgelegt ist.

*nCharSet*<br/>
Gibt den Zeichensatz der Schriftart anSiehe das `lfCharSet` Element in der `LOGFONT` Struktur im Windows SDK für eine Liste von Werten.

Der OEM-Zeichensatz ist systemabhängig.

Schriftarten mit anderen Zeichensätzen können im System vorhanden sein. Eine Anwendung, die eine Schriftart mit einem unbekannten Zeichensatz verwendet, darf nicht versuchen, Zeichenfolgen zu übersetzen oder zu interpretieren, die mit dieser Schriftart gerendert werden sollen. Stattdessen sollten die Zeichenfolgen direkt an den Ausgabegerätetreiber übergeben werden.

Der Schriftmapper verwendet nicht den DEFAULT_CHARSET Wert. Eine Anwendung kann diesen Wert verwenden, um den Namen und die Größe einer Schriftart vollständig zu beschreiben. Wenn keine Schriftart mit dem angegebenen Namen vorhanden ist, kann eine Schriftart aus einem beliebigen Zeichensatz durch die angegebene Schriftart ersetzt werden. Um unerwartete Ergebnisse zu vermeiden, sollten Anwendungen den DEFAULT_CHARSET Wert sparsam verwenden.

*nOutPrecision*<br/>
Gibt die gewünschte Ausgabegenauigkeit an. Die Ausgabegenauigkeit legt fest, wie eng die Ausgabe mit der Höhe, Breite, Zeichenausrichtung, Hemmung und Tonhöhe der gewünschten Schriftart übereinstimmen muss. Eine `lfOutPrecision` Liste mit `LOGFONT` Werten und weiteren Informationen finden Sie unter dem Member in der Struktur im Windows SDK.

*nClipPrecision*<br/>
Gibt die gewünschte Schnittgenauigkeit an. Die Schnittgenauigkeit definiert, wie Zeichen abgeschnitten werden, die sich teilweise außerhalb des Clipping-Bereichs befinden. Eine `lfClipPrecision` Liste von `LOGFONT` Werten finden Sie unter dem Member in der Struktur im Windows SDK.

Um eine eingebettete schreibgeschützte Schriftart zu verwenden, muss eine Anwendung CLIP_ENCAPSULATE angeben.

Um eine konsistente Drehung von Geräte-, TrueType- und Vektorschriftarten zu erreichen, kann eine Anwendung den OR-Operator verwenden, um den CLIP_LH_ANGLESWert mit einem der anderen *nClipPrecision-Werte* zu kombinieren. Wenn das CLIP_LH_ANGLES Bit eingestellt ist, hängt die Drehung für alle Schriftarten davon ab, ob die Ausrichtung des Koordinatensystems Links- oder Rechtshänder ist. (Weitere Informationen zur Ausrichtung von Koordinatensystemen finden Sie in der Beschreibung des Parameters *nOrientation.)* Wenn CLIP_LH_ANGLES nicht festgelegt ist, drehen sich Geräteschriftarten immer gegen den Uhrzeigersinn, aber die Drehung anderer Schriftarten hängt von der Ausrichtung des Koordinatensystems ab.

*nQualität*<br/>
Gibt die Ausgabequalität der Schriftart an, die definiert, wie sorgfältig die GDI versuchen muss, die Attribute der logischen Schriftart mit denen einer tatsächlichen physischen Schriftart abzugleichen. Eine `lfQuality` Liste von `LOGFONT` Werten finden Sie unter dem Member in der Struktur im Windows SDK.

*nPitchAndFamilie*<br/>
Gibt Dichte und Familie der Schriftart an. Eine `lfPitchAndFamily` Liste mit `LOGFONT` Werten und weiteren Informationen finden Sie unter dem Member in der Struktur im Windows SDK.

*lpszFacename*<br/>
A `CString` oder Zeiger auf eine null-terminierte Zeichenfolge, die den Schriftnamen der Schriftart angibt. Die Länge dieser Zeichenfolge darf 30 Zeichen nicht überschreiten. Die Windows [EnumFontFamilies-Funktion](/windows/win32/api/wingdi/nf-wingdi-enumfontfamiliesw) kann verwendet werden, um alle derzeit verfügbaren Schriftarten aufzuzählen. Wenn *lpszFacename* NULL ist, verwendet die GDI eine geräteunabhängige Schrift.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Die Schriftart kann anschließend als Schriftart für jeden Gerätekontext ausgewählt werden.

Die `CreateFont` Funktion erstellt keine neue Windows GDI-Schriftart. Es wählt lediglich die nächste Übereinstimmung aus den physischen Schriftarten aus, die dem GDI zur Verfügung stehen.

Anwendungen können die Standardeinstellungen für die meisten Parameter verwenden, wenn sie eine logische Schriftart erstellen. Die Parameter, die immer bestimmte Werte angegeben werden sollten, sind *nHeight* und *lpszFacename*. Wenn *nHeight* und *lpszFacename* nicht von der Anwendung festgelegt werden, ist die erstellte logische Schriftart geräteabhängig.

Wenn Sie mit `CFont` dem von `CreateFont` der `CDC::SelectObject` Funktion erstellten Objekt fertig sind, wählen `CFont` Sie eine andere Schriftart im Gerätekontext aus, und löschen Sie dann das nicht mehr benötigte Objekt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#71](../../mfc/codesnippet/cpp/cfont-class_2.cpp)]

## <a name="cfontcreatefontindirect"></a><a name="createfontindirect"></a>CFont::CreateFontIndirect

Initialisiert ein `CFont` Objekt mit den in einer [LOGFONT-Struktur](/windows/win32/api/wingdi/ns-wingdi-logfontw)angegebenen Eigenschaften.

```
BOOL CreateFontIndirect(const LOGFONT* lpLogFont);
```

### <a name="parameters"></a>Parameter

*lpLogFont*<br/>
Zeigt auf `LOGFONT` eine Struktur, die die Eigenschaften der logischen Schriftart definiert.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Die Schriftart kann anschließend als aktuelle Schriftart für jedes Gerät ausgewählt werden.

Diese Schriftart weist die in der [LOGFONT-Struktur](/windows/win32/api/wingdi/ns-wingdi-logfontw) angegebenen Merkmale auf. Wenn die Schriftart mithilfe der [Cdc::SelectObject-Memberfunktion](../../mfc/reference/cdc-class.md#selectobject) ausgewählt wird, versucht der GDI-Schriftartmapper, die logische Schriftart mit einer vorhandenen physischen Schriftart abzugleichen. Wenn der Schriftart-Mapper keine genaue Übereinstimmung für die logische Schriftart findet, stellt er eine alternative Schriftart bereit, deren Eigenschaften so viele der angeforderten Merkmale wie möglich entsprechen.

Wenn Sie das `CFont` von der `CreateFontIndirect` Funktion erstellte Objekt nicht mehr benötigen, wählen `CDC::SelectObject` `CFont` Sie eine andere Schriftart im Gerätekontext aus, und löschen Sie dann das nicht mehr benötigte Objekt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#72](../../mfc/codesnippet/cpp/cfont-class_3.cpp)]

## <a name="cfontcreatepointfont"></a><a name="createpointfont"></a>CFont::CreatePointFont

Diese Funktion bietet eine einfache Möglichkeit, eine Schriftart mit einer angegebenen Schriftart und Punktgröße zu erstellen.

```
BOOL CreatePointFont(
    int nPointSize,
    LPCTSTR lpszFaceName,
    CDC* pDC = NULL);
```

### <a name="parameters"></a>Parameter

*nPointSize*<br/>
Angeforderte Schrifthöhe in Zehntel eines Punktes. (Übergeben Sie z. B. 120, um eine 12-Punkte-Schriftart anzufordern.)

*lpszFaceName*<br/>
A `CString` oder Zeiger auf eine null-terminierte Zeichenfolge, die den Schriftnamen der Schriftart angibt. Die Länge dieser Zeichenfolge darf 30 Zeichen nicht überschreiten. Die Funktion Windows 'EnumFontFamilies kann verwendet werden, um alle derzeit verfügbaren Schriftarten aufzuzählen. Wenn *lpszFaceName* NULL ist, verwendet die GDI eine geräteunabhängige Schrift.

*pDC*<br/>
Zeiger auf [CDC](../../mfc/reference/cdc-class.md) das CDC-Objekt, das zum Konvertieren der Höhe in *nPointSize* in logische Einheiten verwendet werden soll. Wenn NULL, wird ein Bildschirmgerätekontext für die Konvertierung verwendet.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Es konvertiert automatisch die Höhe in *nPointSize* in logische Einheiten mit dem CDC-Objekt, auf das *pDC*zeigt.

Wenn Sie mit `CFont` dem von `CreatePointFont` der Funktion erstellten Objekt fertig sind, `CFont` wählen Sie zuerst die Schriftart aus dem Gerätekontext aus, und löschen Sie dann das Objekt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#73](../../mfc/codesnippet/cpp/cfont-class_4.cpp)]

## <a name="cfontcreatepointfontindirect"></a><a name="createpointfontindirect"></a>CFont::CreatePointFontIndirect

Diese Funktion ist die gleiche wie [CreateFontIndirect,](#createfontindirect) mit der Ausnahme, dass das `lfHeight` Element des in Zehnteln eines Punktes und nicht in Geräteeinheiten interpretiert `LOGFONT` wird.

```
BOOL CreatePointFontIndirect(
    const LOGFONT* lpLogFont,
    CDC* pDC = NULL);
```

### <a name="parameters"></a>Parameter

*lpLogFont*<br/>
Zeigt auf eine [LOGFONT-Struktur,](/windows/win32/api/wingdi/ns-wingdi-logfontw) die die Eigenschaften der logischen Schriftart definiert. Das `lfHeight` Element `LOGFONT` der Struktur wird in Zehnteln eines Punktes und nicht in logischen Einheiten gemessen. (Wenn Sie `lfHeight` z. B. auf 120 setzen, um eine 12-Punkte-Schriftart anzufordern.)

*pDC*<br/>
Zeiger auf das [CDC-Objekt,](../../mfc/reference/cdc-class.md) das zum `lfHeight` Konvertieren der Höhe in logische Einheiten verwendet werden soll. Wenn NULL, wird ein Bildschirmgerätekontext für die Konvertierung verwendet.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Funktion konvertiert automatisch `lfHeight` die Höhe in logische Einheiten mithilfe des CDC-Objekts, auf das *pDC* zeigt, bevor die `LOGFONT` Struktur an Windows übergeben wird.

Wenn Sie mit `CFont` dem von `CreatePointFontIndirect` der Funktion erstellten Objekt fertig sind, `CFont` wählen Sie zuerst die Schriftart aus dem Gerätekontext aus, und löschen Sie dann das Objekt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#74](../../mfc/codesnippet/cpp/cfont-class_5.cpp)]

## <a name="cfontfromhandle"></a><a name="fromhandle"></a>Cfont::FromHandle

Gibt einen Zeiger `CFont` auf ein Objekt zurück, wenn einem Windows GDI-Schriftartobjekt ein HFONT-Handle übergeben wird.

```
static CFont* PASCAL FromHandle(HFONT hFont);
```

### <a name="parameters"></a>Parameter

*hFont*<br/>
Ein HFONT-Handle für eine Windows-Schriftart.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `CFont` ein Objekt, wenn erfolgreich; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Wenn `CFont` ein Objekt noch nicht an das `CFont` Handle angefügt ist, wird ein temporäres Objekt erstellt und angefügt. Dieses `CFont` temporäre Objekt ist nur gültig, bis die Anwendung das nächste Mal Leerlaufzeit in ihrer Ereignisschleife hat, zu diesem Zeitpunkt alle temporären Grafikobjekte gelöscht werden. Eine andere Möglichkeit, dies zu sagen, ist, dass das temporäre Objekt nur während der Verarbeitung einer Fensternachricht gültig ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#75](../../mfc/codesnippet/cpp/cfont-class_6.cpp)]

## <a name="cfontgetlogfont"></a><a name="getlogfont"></a>CFont::GetLogFont

Rufen Sie diese Funktion auf, um eine Kopie der `LOGFONT` Struktur für `CFont`abzurufen.

```
int GetLogFont(LOGFONT* pLogFont);
```

### <a name="parameters"></a>Parameter

*pLogFont*<br/>
Zeigen Sie auf die [LOGFONT-Struktur,](/windows/win32/api/wingdi/ns-wingdi-logfontw) um die Schriftartinformationen zu erhalten.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Funktion erfolgreich ist, andernfalls 0.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#76](../../mfc/codesnippet/cpp/cfont-class_7.cpp)]

## <a name="cfontoperator-hfont"></a><a name="operator_hfont"></a>CFont::operator HFONT

Verwenden Sie diesen Operator, um das Windows GDI-Handle der Schriftart abzubekommen, die dem `CFont` Objekt zugeordnet ist.

```
operator HFONT() const;
```

### <a name="return-value"></a>Rückgabewert

Das Handle des Windows GDI-Schriftartobjekts, das `CFont` bei Erfolg angefügt ist. andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Da dieser Operator automatisch für `CFont` Konvertierungen von [Fonts](/windows/win32/gdi/fonts-and-text)und `CFont` Text verwendet wird, können Sie Objekte an Funktionen übergeben, die HFONTs erwarten.

Weitere Informationen zur Verwendung von Grafikobjekten finden Sie unter [Grafikobjekte](/windows/win32/gdi/graphic-objects) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#77](../../mfc/codesnippet/cpp/cfont-class_8.cpp)]

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject-Klasse](../../mfc/reference/cgdiobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
