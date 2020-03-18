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
ms.openlocfilehash: 27f4f14c9e93091728e256c890dcffee26a43de4
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426972"
---
# <a name="cpalette-class"></a>CPalette-Klasse

Kapselt eine Windows-Farbpalette.

## <a name="syntax"></a>Syntax

```
class CPalette : public CGdiObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[CPalette:: CPalette](#cpalette)|Erstellt ein `CPalette` Objekt ohne angehängte Windows-Palette. Sie müssen das `CPalette`-Objekt mit einer der initialisierungsmember-Funktionen initialisieren, bevor es verwendet werden kann.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[CPalette:: AnimatePalette](#animatepalette)|Ersetzt Einträge in der logischen Palette, die durch das `CPalette` Objekt identifiziert wird. Die Anwendung muss ihren Client Bereich nicht aktualisieren, da die neuen Einträge von Windows sofort der Systempalette zugeordnet werden.|
|[CPalette:: CreateHalftonePalette](#createhalftonepalette)|Erstellt eine halbftone-Palette für den Gerätekontext und fügt Sie an das `CPalette`-Objekt an.|
|[CPalette:: CreatePalette](#createpalette)|Erstellt eine Windows-Farbpalette und fügt Sie an das `CPalette`-Objekt an.|
|[CPalette:: FromHandle](#fromhandle)|Gibt einen Zeiger auf ein `CPalette` Objekt zurück, wenn ein Handle für ein Windows-Palettenobjekt angegeben wird.|
|[CPalette:: getentrycount](#getentrycount)|Ruft die Anzahl der Paletteneinträge in einer logischen Palette ab.|
|[CPalette:: getnearestpaletteingedex](#getnearestpaletteindex)|Gibt den Index des Eintrags in der logischen Palette zurück, der mit einem Farbwert am ehesten übereinstimmt.|
|[CPalette:: GetPaletteEntries](#getpaletteentries)|Ruft einen Bereich von paletteneinträgen in einer logischen Palette ab.|
|[CPalette:: ResizePalette](#resizepalette)|Ändert die Größe der logischen Palette, die vom `CPalette`-Objekt angegeben wird, in die angegebene Anzahl von Einträgen.|
|[CPalette:: setpaletteentries](#setpaletteentries)|Legt RGB-Farbwerte und-Flags in einem Bereich von Einträgen in einer logischen Palette fest.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|Beschreibung|
|----------|-----------------|
|[CPalette:: Operator hpalette](#operator_hpalette)|Gibt die an den `CPalette`angefügte hpalette zurück.|

## <a name="remarks"></a>Hinweise

Eine Palette bietet eine Schnittstelle zwischen einer Anwendung und einem Farbausgabe Gerät (z. b. einem Anzeigegerät). Die-Schnittstelle ermöglicht es der Anwendung, die Farbfunktionen des Ausgabegeräts in vollem Umfang zu nutzen, ohne die von anderen Anwendungen angezeigten Farben schwer zu beeinträchtigen. Windows verwendet die logische Palette der Anwendung (eine Liste der erforderlichen Farben) und die Systempalette (die verfügbare Farben definiert), um die verwendeten Farben zu bestimmen.

Ein `CPalette`-Objekt stellt Element Funktionen zum Bearbeiten der Palette bereit, auf die vom-Objekt verwiesen wird. Erstellen Sie ein `CPalette` Objekt, und verwenden Sie seine Member-Funktionen, um die tatsächliche Palette, ein GDI-Objekt (Graphics Device Interface) zu erstellen und die zugehörigen Einträge und anderen Eigenschaften zu bearbeiten.

Weitere Informationen zur Verwendung von `CPalette`finden Sie unter [Graphic Objects](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CPalette`

## <a name="requirements"></a>Voraussetzungen

**Header:** afxwin.h

##  <a name="animatepalette"></a>CPalette:: AnimatePalette

Ersetzt Einträge in der logischen Palette, die an das `CPalette` Objekt angefügt ist.

```
void AnimatePalette(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors);
```

### <a name="parameters"></a>Parameter

*nstartindex*<br/>
Gibt den ersten Eintrag in der Palette an, der animiert werden soll.

*nnumentries*<br/>
Gibt die Anzahl der zu animierenden Einträge in der Palette an.

*lppalettecolors*<br/>
Verweist auf das erste Element eines Arrays von [PaletteEntry](/previous-versions/dd162769\(v=vs.85\)) -Strukturen, um die durch *nstartindex* und *nnumentries*identifizierten Paletteneinträge zu ersetzen.

### <a name="remarks"></a>Hinweise

Wenn eine Anwendung `AnimatePalette`aufruft, muss Sie Ihren Client Bereich nicht aktualisieren, da die neuen Einträge von Windows sofort der Systempalette zugeordnet werden.

Die `AnimatePalette`-Funktion ändert nur Einträge mit dem PC_RESERVED-Flag, das im entsprechenden `palPaletteEntry` Member der [LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette) -Struktur festgelegt ist, die an das `CPalette` Objekt angefügt ist. Weitere Informationen zu dieser Struktur finden Sie unter LOGPALETTE in der Windows SDK.

##  <a name="cpalette"></a>CPalette:: CPalette

Erstellt ein `CPalette`-Objekt.

```
CPalette();
```

### <a name="remarks"></a>Hinweise

Das-Objekt hat keine angefügte Palette, bis Sie `CreatePalette` zum Anfügen eines anfügen.

##  <a name="createhalftonepalette"></a>CPalette:: CreateHalftonePalette

Erstellt eine halbftone-Palette für den Gerätekontext.

```
BOOL CreateHalftonePalette(CDC* pDC);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Identifiziert den Gerätekontext.

### <a name="return-value"></a>Rückgabewert

Ist ungleich null (0), wenn die Funktion erfolgreich ausgeführt wird, andernfalls null (0).

### <a name="remarks"></a>Hinweise

Eine Anwendung sollte eine halbftone-Palette erstellen, wenn der streckungs Modus eines Geräte Kontexts auf "Halbton" festgelegt ist. Die von der [CreateHalftonePalette](/windows/win32/api/wingdi/nf-wingdi-createhalftonepalette) -Member-Funktion zurückgegebene logische Halbton-Palette sollte dann ausgewählt und in den Gerätekontext umgesetzt werden, bevor die [CDC:: StretchBlt](../../mfc/reference/cdc-class.md#stretchblt) -Funktion oder die [StretchDIBits](/windows/win32/api/wingdi/nf-wingdi-stretchdibits) -Funktion aufgerufen wird.

Weitere Informationen zu `CreateHalftonePalette` und `StretchDIBits`finden Sie in der Windows SDK.

##  <a name="createpalette"></a>CPalette:: CreatePalette

Initialisiert eine `CPalette`-Objekt, indem eine logische Windows-Farbpalette erstellt und an das `CPalette` Objekt angefügt wird.

```
BOOL CreatePalette(LPLOGPALETTE lpLogPalette);
```

### <a name="parameters"></a>Parameter

*lplogpalette*<br/>
Verweist auf eine [LOGPALETTE](/windows/win32/api/wingdi/ns-wingdi-logpalette) -Struktur, die Informationen zu den Farben in der logischen Palette enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Weitere Informationen zur `LOGPALETTE` Struktur finden Sie in der Windows SDK.

##  <a name="fromhandle"></a>CPalette:: FromHandle

Gibt einen Zeiger auf ein `CPalette` Objekt zurück, wenn ein Handle für ein Windows-Palettenobjekt angegeben wird.

```
static CPalette* PASCAL FromHandle(HPALETTE hPalette);
```

### <a name="parameters"></a>Parameter

*hPalette*<br/>
Ein Handle für eine Windows-GDI-Farbpalette.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein `CPalette` Objekt, wenn erfolgreich. andernfalls NULL.

### <a name="remarks"></a>Hinweise

Wenn ein `CPalette` Objekt nicht bereits an die Windows-Palette angefügt ist, wird ein temporäres `CPalette` Objekt erstellt und angefügt. Dieses temporäre `CPalette` Objekt ist nur gültig, bis das nächste Mal die Leerlaufzeit der Anwendung in der Ereignisschleife liegt. zu diesem Zeitpunkt werden alle temporären Grafik Objekte gelöscht. Das heißt, dass das temporäre Objekt nur während der Verarbeitung einer Fenster Nachricht gültig ist.

##  <a name="getentrycount"></a>CPalette:: getentrycount

Rufen Sie diese Member-Funktion auf, um die Anzahl von Einträgen in einer gegebenen logischen Palette abzurufen.

```
int GetEntryCount();
```

### <a name="return-value"></a>Rückgabewert

Anzahl von Einträgen in einer logischen Palette.

##  <a name="getnearestpaletteindex"></a>CPalette:: getnearestpaletteingedex

Gibt den Index des Eintrags in der logischen Palette zurück, der am ehesten mit dem angegebenen Farbwert übereinstimmt.

```
UINT GetNearestPaletteIndex(COLORREF crColor) const;
```

### <a name="parameters"></a>Parameter

*crcolor*<br/>
Gibt die Farbe an, die abgeglichen werden soll.

### <a name="return-value"></a>Rückgabewert

Der Index eines Eintrags in einer logischen Palette. Der Eintrag enthält die Farbe, die fast mit der angegebenen Farbe übereinstimmt.

##  <a name="getpaletteentries"></a>CPalette:: GetPaletteEntries

Ruft einen Bereich von paletteneinträgen in einer logischen Palette ab.

```
UINT GetPaletteEntries(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors) const;
```

### <a name="parameters"></a>Parameter

*nstartindex*<br/>
Gibt den ersten Eintrag in der logischen Palette an, der abgerufen werden soll.

*nnumentries*<br/>
Gibt die Anzahl der Einträge in der logischen Palette an, die abgerufen werden soll.

*lppalettecolors*<br/>
Verweist auf ein Array von [PaletteEntry](/previous-versions/dd162769\(v=vs.85\)) -Datenstrukturen, um die Paletteneinträge zu empfangen. Das Array muss mindestens so viele Datenstrukturen enthalten, wie von *nnumentries*angegeben.

### <a name="return-value"></a>Rückgabewert

Die Anzahl von Einträgen, die aus der logischen Palette abgerufen wurden. 0, wenn die Funktion nicht ausgeführt werden konnte.

##  <a name="operator_hpalette"></a>CPalette:: Operator hpalette

Verwenden Sie diesen Operator, um das angefügte Windows-GDI-Handle des `CPalette` Objekts zu erhalten.

```
operator HPALETTE() const;
```

### <a name="return-value"></a>Rückgabewert

Bei Erfolg ein Handle für das Windows-GDI-Objekt, das durch das `CPalette`-Objekt dargestellt wird. andernfalls NULL.

### <a name="remarks"></a>Hinweise

Dieser Operator ist ein Typumwandlungs Operator, der die direkte Verwendung eines hpalette-Objekts unterstützt.

Weitere Informationen zum Verwenden von Grafikobjekten finden Sie im Artikel [Graphic Objects](/windows/win32/gdi/graphic-objects) in the Windows SDK.

##  <a name="resizepalette"></a>CPalette:: ResizePalette

Ändert die Größe der logischen Palette, die an das `CPalette`-Objekt angefügt ist, an die Anzahl der durch *nnumentries*angegebenen Einträge.

```
BOOL ResizePalette(UINT nNumEntries);
```

### <a name="parameters"></a>Parameter

*nnumentries*<br/>
Gibt die Anzahl der Einträge in der Palette an, nachdem die Größe geändert wurde.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Größe der Palette erfolgreich geändert wurde. andernfalls 0.

### <a name="remarks"></a>Hinweise

Wenn eine Anwendung `ResizePalette` aufruft, um die Größe der Palette zu verringern, sind die in der Palette der Größe verbleibenden Einträge unverändert. Wenn die Anwendung `ResizePalette` aufruft, um die Palette zu vergrößern, werden die zusätzlichen Paletteneinträge auf schwarz festgelegt (die roten, grünen und blauen Werte sind alle 0), und die Flags für alle zusätzlichen Einträge werden auf 0 festgelegt.

Weitere Informationen zur Windows-API `ResizePalette`finden Sie unter [ResizePalette](/windows/win32/api/wingdi/nf-wingdi-resizepalette) im Windows SDK.

##  <a name="setpaletteentries"></a>CPalette:: setpaletteentries

Legt RGB-Farbwerte und-Flags in einem Bereich von Einträgen in einer logischen Palette fest.

```
UINT SetPaletteEntries(
    UINT nStartIndex,
    UINT nNumEntries,
    LPPALETTEENTRY lpPaletteColors);
```

### <a name="parameters"></a>Parameter

*nstartindex*<br/>
Gibt den ersten Eintrag in der logischen Palette an, der festgelegt werden soll.

*nnumentries*<br/>
Gibt die Anzahl der Einträge in der logischen Palette an, die festgelegt werden soll.

*lppalettecolors*<br/>
Verweist auf ein Array von [PaletteEntry](/previous-versions/dd162769\(v=vs.85\)) -Datenstrukturen, um die Paletteneinträge zu empfangen. Das Array muss mindestens so viele Datenstrukturen enthalten, wie von *nnumentries*angegeben.

### <a name="return-value"></a>Rückgabewert

Die Anzahl von Einträgen, die in der logischen Palette festgelegt sind. 0, wenn die Funktion nicht ausgeführt werden konnte.

### <a name="remarks"></a>Hinweise

Wenn die logische Palette in einen Gerätekontext ausgewählt wird, wenn die Anwendung `SetPaletteEntries`aufruft, werden die Änderungen erst wirksam, wenn die Anwendung [CDC:: RealizePalette](../../mfc/reference/cdc-class.md#realizepalette)aufruft.

Weitere Informationen finden Sie unter [PaletteEntry](/previous-versions/dd162769\(v=vs.85\)) in der Windows SDK.

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject-Klasse](../../mfc/reference/cgdiobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CPalette:: GetPaletteEntries](#getpaletteentries)<br/>
[CPalette:: setpaletteentries](#setpaletteentries)
