---
title: CPalette-Klasse
ms.date: 11/04/2016
f1_keywords:
- CPalette
- AFXWIN/CPalette
- AFXWIN/CPalette::CPalette
- AFXWIN/CPalette::AnimatePalette
- AFXWIN/CPalette::CreateHalftonePalette
- AFXWIN/CPalette::CreatePalette
- AFXWIN/CPalette::FromHandle
- AFXWIN/CPalette::GetEntryCount
- AFXWIN/CPalette::GetNearestPaletteIndex
- AFXWIN/CPalette::GetPaletteEntries
- AFXWIN/CPalette::ResizePalette
- AFXWIN/CPalette::SetPaletteEntries
helpviewer_keywords:
- CPalette [MFC], CPalette
- CPalette [MFC], AnimatePalette
- CPalette [MFC], CreateHalftonePalette
- CPalette [MFC], CreatePalette
- CPalette [MFC], FromHandle
- CPalette [MFC], GetEntryCount
- CPalette [MFC], GetNearestPaletteIndex
- CPalette [MFC], GetPaletteEntries
- CPalette [MFC], ResizePalette
- CPalette [MFC], SetPaletteEntries
ms.assetid: 8cd95498-53ed-4852-85e1-70e522541114
ms.openlocfilehash: 83cd125fa7ab64aa39c606bc048022400d158e72
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374765"
---
# <a name="cpalette-class"></a>CPalette-Klasse

Kapselt eine Windows-Farbpalette.

## <a name="syntax"></a>Syntax

```
class CPalette : public CGdiObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPalette::CPalette](#cpalette)|Erstellt ein `CPalette` Objekt ohne angefügte Windows-Palette. Sie müssen das `CPalette` Objekt mit einer der Initialisierungsmemberfunktionen initialisieren, bevor es verwendet werden kann.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPalette::AnimatePalette](#animatepalette)|Ersetzt Einträge in der logischen `CPalette` Palette, die vom Objekt identifiziert werden. Die Anwendung muss ihren Clientbereich nicht aktualisieren, da Windows die neuen Einträge sofort der Systempalette zuordnet.|
|[CPalette::ErstellenHalftonePalette](#createhalftonepalette)|Erstellt eine Halbtonpalette für den Gerätekontext `CPalette` und fügt sie an das Objekt an.|
|[CPalette::CreatePalette](#createpalette)|Erstellt eine Windows-Farbpalette und `CPalette` fügt sie an das Objekt an.|
|[Cpalette::FromHandle](#fromhandle)|Gibt einen Zeiger `CPalette` auf ein Objekt zurück, wenn einem Windows-Palettenobjekt ein Handle übergeben wird.|
|[CPalette::GetEntryCount](#getentrycount)|Ruft die Anzahl der Paletteneinträge in einer logischen Palette ab.|
|[CPalette::GetNearestPaletteIndex](#getnearestpaletteindex)|Gibt den Index des Eintrags in der logischen Palette zurück, der am ehesten mit einem Farbwert übereinstimmt.|
|[CPalette::GetPaletteEntries](#getpaletteentries)|Ruft eine Reihe von Paletteneinträgen in einer logischen Palette ab.|
|[CPalette::Größenpalette ändern](#resizepalette)|Ändert die Größe der vom `CPalette` Objekt angegebenen logischen Palette in die angegebene Anzahl von Einträgen.|
|[CPalette::SetPaletteEntries](#setpaletteentries)|Legt RGB-Farbwerte und -Flags in einem Bereich von Einträgen in einer logischen Palette fest.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPalette::operator HPALETTE](#operator_hpalette)|Gibt die HPALETTE `CPalette`zurück, die an die angehängt ist.|

## <a name="remarks"></a>Bemerkungen

Eine Palette stellt eine Schnittstelle zwischen einer Anwendung und einem Farbausgabegerät (z. B. einem Anzeigegerät) bereit. Die Schnittstelle ermöglicht es der Anwendung, die Farbfunktionen des Ausgabegeräts voll auszuschöpfen, ohne die von anderen Anwendungen angezeigten Farben stark zu beeinträchtigen. Windows verwendet die logische Palette der Anwendung (eine Liste der benötigten Farben) und die Systempalette (die verfügbare Farben definiert), um die verwendeten Farben zu bestimmen.

Ein `CPalette` Objekt stellt Memberfunktionen zum Bearbeiten der Palette bereit, auf die das Objekt verweist. Erstellen `CPalette` Sie ein Objekt, und verwenden Sie seine Memberfunktionen, um die eigentliche Palette, ein GDI-Objekt (Graphics Device Interface) zu erstellen und seine Einträge und andere Eigenschaften zu bearbeiten.

Weitere Informationen zur `CPalette`Verwendung finden Sie unter [Grafikobjekte](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CPalette`

## <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="cpaletteanimatepalette"></a><a name="animatepalette"></a>CPalette::AnimatePalette

Ersetzt Einträge in der logischen `CPalette` Palette, die dem Objekt zugeordnet sind.

```
void AnimatePalette(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors);
```

### <a name="parameters"></a>Parameter

*nStartIndex*<br/>
Gibt den ersten Eintrag in der Palette an, der animiert werden soll.

*nNumEntries*<br/>
Gibt die Anzahl der Einträge in der Palette an, die animiert werden soll.

*lpPaletteFarben*<br/>
Zeigt auf das erste Element eines Arrays von [PALETTEENTRY-Strukturen,](/previous-versions/dd162769\(v=vs.85\)) um die Paletteneinträge zu ersetzen, die durch *nStartIndex* und *nNumEntries*identifiziert wurden.

### <a name="remarks"></a>Bemerkungen

Wenn eine `AnimatePalette`Anwendung aufruft, muss sie ihren Clientbereich nicht aktualisieren, da Windows die neuen Einträge sofort der Systempalette zuordnet.

Die `AnimatePalette` Funktion ändert nur Einträge, wobei das `palPaletteEntry` PC_RESERVED Flag im entsprechenden Member `CPalette` der [LOGPALETTE-Struktur](/windows/win32/api/wingdi/ns-wingdi-logpalette) festgelegt ist, die dem Objekt zugeordnet ist. Weitere Informationen zu dieser Struktur finden Sie unter LOGPALETTE im Windows SDK.

## <a name="cpalettecpalette"></a><a name="cpalette"></a>CPalette::CPalette

Erstellt ein `CPalette`-Objekt.

```
CPalette();
```

### <a name="remarks"></a>Bemerkungen

Das Objekt verfügt über keine `CreatePalette` angefügte Palette, bis Sie eine anfügen.

## <a name="cpalettecreatehalftonepalette"></a><a name="createhalftonepalette"></a>CPalette::ErstellenHalftonePalette

Erstellt eine Halbtonpalette für den Gerätekontext.

```
BOOL CreateHalftonePalette(CDC* pDC);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Identifiziert den Gerätekontext.

### <a name="return-value"></a>Rückgabewert

Ist ungleich null (0), wenn die Funktion erfolgreich ausgeführt wird, andernfalls null (0).

### <a name="remarks"></a>Bemerkungen

Eine Anwendung sollte eine Halbtonpalette erstellen, wenn der Dehnmodus eines Gerätekontexts auf HALFTONE festgelegt ist. Die logische Halbtonpalette, die von der [Memberfunktion CreateHalftonePalette](/windows/win32/api/wingdi/nf-wingdi-createhalftonepalette) zurückgegeben wird, sollte dann ausgewählt und in den Gerätekontext umgesetzt werden, bevor die [CDC::StretchBlt-](../../mfc/reference/cdc-class.md#stretchblt) oder [StretchDIBits-Funktion](/windows/win32/api/wingdi/nf-wingdi-stretchdibits) aufgerufen wird.

Weitere Informationen zu `CreateHalftonePalette` und `StretchDIBits`.

## <a name="cpalettecreatepalette"></a><a name="createpalette"></a>CPalette::CreatePalette

Initialisiert ein `CPalette` Objekt, indem eine logische Windows-Farbpalette `CPalette` erstellt und an das Objekt angefügt wird.

```
BOOL CreatePalette(LPLOGPALETTE lpLogPalette);
```

### <a name="parameters"></a>Parameter

*lpLogPalette*<br/>
Zeigt auf eine [LOGPALETTE-Struktur,](/windows/win32/api/wingdi/ns-wingdi-logpalette) die Informationen zu den Farben in der logischen Palette enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zur `LOGPALETTE` Struktur finden Sie im Windows SDK.

## <a name="cpalettefromhandle"></a><a name="fromhandle"></a>Cpalette::FromHandle

Gibt einen Zeiger `CPalette` auf ein Objekt zurück, wenn einem Windows-Palettenobjekt ein Handle übergeben wird.

```
static CPalette* PASCAL FromHandle(HPALETTE hPalette);
```

### <a name="parameters"></a>Parameter

*hPalette*<br/>
Ein Handle für eine Windows GDI-Farbpalette.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `CPalette` ein Objekt, wenn erfolgreich; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Wenn `CPalette` ein Objekt noch nicht an die `CPalette` Windows-Palette angefügt ist, wird ein temporäres Objekt erstellt und angefügt. Dieses `CPalette` temporäre Objekt ist nur gültig, bis die Anwendung das nächste Mal Leerlaufzeit in ihrer Ereignisschleife hat, zu diesem Zeitpunkt alle temporären Grafikobjekte gelöscht werden. Mit anderen Worten, das temporäre Objekt ist nur während der Verarbeitung einer Fensternachricht gültig.

## <a name="cpalettegetentrycount"></a><a name="getentrycount"></a>CPalette::GetEntryCount

Rufen Sie diese Memberfunktion auf, um die Anzahl der Einträge in einer bestimmten logischen Palette abzurufen.

```
int GetEntryCount();
```

### <a name="return-value"></a>Rückgabewert

Anzahl der Einträge in einer logischen Palette.

## <a name="cpalettegetnearestpaletteindex"></a><a name="getnearestpaletteindex"></a>CPalette::GetNearestPaletteIndex

Gibt den Index des Eintrags in der logischen Palette zurück, der dem angegebenen Farbwert am ehesten entspricht.

```
UINT GetNearestPaletteIndex(COLORREF crColor) const;
```

### <a name="parameters"></a>Parameter

*crColor*<br/>
Gibt die Farbe an, die abgeglichen werden soll.

### <a name="return-value"></a>Rückgabewert

Der Index eines Eintrags in einer logischen Palette. Der Eintrag enthält die Farbe, die fast mit der angegebenen Farbe übereinstimmt.

## <a name="cpalettegetpaletteentries"></a><a name="getpaletteentries"></a>CPalette::GetPaletteEntries

Ruft eine Reihe von Paletteneinträgen in einer logischen Palette ab.

```
UINT GetPaletteEntries(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors) const;
```

### <a name="parameters"></a>Parameter

*nStartIndex*<br/>
Gibt den ersten Eintrag in der logischen Palette an, der abgerufen werden soll.

*nNumEntries*<br/>
Gibt die Anzahl der Einträge in der logischen Palette an, die abgerufen werden soll.

*lpPaletteFarben*<br/>
Zeigt auf ein [PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\)) Array von PALETTEENTRY-Datenstrukturen, um die Paletteneinträge zu empfangen. Das Array muss mindestens so viele Datenstrukturen enthalten, wie von *nNumEntries*angegeben.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Einträge, die aus der logischen Palette abgerufen wurden; 0, wenn die Funktion fehlgeschlagen ist.

## <a name="cpaletteoperator-hpalette"></a><a name="operator_hpalette"></a>CPalette::operator HPALETTE

Verwenden Sie diesen Operator, um das `CPalette` angefügte Windows GDI-Handle des Objekts abzubekommen.

```
operator HPALETTE() const;
```

### <a name="return-value"></a>Rückgabewert

Wenn erfolgreich, ein Handle für das Windows `CPalette` GDI-Objekt, das durch das Objekt dargestellt wird; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Dieser Operator ist ein Gießoperator, der die direkte Verwendung eines HPALETTE-Objekts unterstützt.

Weitere Informationen zur Verwendung von Grafikobjekten finden Sie im Artikel [Grafikobjekte](/windows/win32/gdi/graphic-objects) im Windows SDK.

## <a name="cpaletteresizepalette"></a><a name="resizepalette"></a>CPalette::Größenpalette ändern

Ändert die Größe der dem `CPalette` Objekt zugeordneten logischen Palette in die Anzahl der Einträge, die von *nNumEntries*angegeben werden.

```
BOOL ResizePalette(UINT nNumEntries);
```

### <a name="parameters"></a>Parameter

*nNumEntries*<br/>
Gibt die Anzahl der Einträge in der Palette an, nachdem die Größe geändert wurde.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Größe der Palette erfolgreich geändert wurde. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Wenn eine `ResizePalette` Anwendung aufruft, um die Größe der Palette zu reduzieren, bleiben die Einträge in der geänderten Palette unverändert. Wenn die `ResizePalette` Anwendung aufruft, um die Palette zu vergrößern, werden die zusätzlichen Paletteneinträge auf Schwarz (die roten, grünen und blauen Werte sind alle 0) und die Flags für alle zusätzlichen Einträge auf 0 gesetzt.

Weitere Informationen zur Windows-API `ResizePalette`finden Sie unter [ResizePalette](/windows/win32/api/wingdi/nf-wingdi-resizepalette) im Windows SDK.

## <a name="cpalettesetpaletteentries"></a><a name="setpaletteentries"></a>CPalette::SetPaletteEntries

Legt RGB-Farbwerte und -Flags in einem Bereich von Einträgen in einer logischen Palette fest.

```
UINT SetPaletteEntries(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors);
```

### <a name="parameters"></a>Parameter

*nStartIndex*<br/>
Gibt den ersten Eintrag in der festzulegenden logischen Palette an.

*nNumEntries*<br/>
Gibt die Anzahl der Einträge in der festzulegenden logischen Palette an.

*lpPaletteFarben*<br/>
Zeigt auf ein [PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\)) Array von PALETTEENTRY-Datenstrukturen, um die Paletteneinträge zu empfangen. Das Array muss mindestens so viele Datenstrukturen enthalten, wie von *nNumEntries*angegeben.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Einträge, die in der logischen Palette festgelegt wurden; 0, wenn die Funktion fehlgeschlagen ist.

### <a name="remarks"></a>Bemerkungen

Wenn die logische Palette beim Aufrufen `SetPaletteEntries`der Anwendung in einem Gerätekontext ausgewählt ist, werden die Änderungen erst wirksam, wenn die Anwendung [CDC::RealizePalette](../../mfc/reference/cdc-class.md#realizepalette)aufruft.

Weitere Informationen finden Sie unter [PALETTEENTRY](/previous-versions/dd162769\(v=vs.85\)) im Windows SDK.

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject-Klasse](../../mfc/reference/cgdiobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CPalette::GetPaletteEntries](#getpaletteentries)<br/>
[CPalette::SetPaletteEntries](#setpaletteentries)
