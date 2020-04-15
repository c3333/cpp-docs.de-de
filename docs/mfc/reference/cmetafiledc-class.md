---
title: CMetaFileDC-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMetaFileDC
- AFXEXT/CMetaFileDC
- AFXEXT/CMetaFileDC::CMetaFileDC
- AFXEXT/CMetaFileDC::Close
- AFXEXT/CMetaFileDC::CloseEnhanced
- AFXEXT/CMetaFileDC::Create
- AFXEXT/CMetaFileDC::CreateEnhanced
helpviewer_keywords:
- CMetaFileDC [MFC], CMetaFileDC
- CMetaFileDC [MFC], Close
- CMetaFileDC [MFC], CloseEnhanced
- CMetaFileDC [MFC], Create
- CMetaFileDC [MFC], CreateEnhanced
ms.assetid: ffce60fa-4181-4d46-9832-25e46fad4db4
ms.openlocfilehash: 0919dacfd758df39064c5381690e9e23a029fcd1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369949"
---
# <a name="cmetafiledc-class"></a>CMetaFileDC-Klasse

Implementiert eine Windows-Metadatei, die eine Sequenz von Graphics Device Interface (GDI)-Befehlen enthält, dass Sie wiedergeben können, um ein gewünschtes Bild oder einen Text zu erstellen.

## <a name="syntax"></a>Syntax

```
class CMetaFileDC : public CDC
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMetaFileDC::CMetaFileDC](#cmetafiledc)|Erstellt ein `CMetaFileDC`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMetaFileDC::Schließen](#close)|Schließt den Gerätekontext und erstellt ein Metadateihandle.|
|[CMetaFileDC::CloseEnhanced](#closeenhanced)|Schließt einen erweiterten Metadatei-Gerätekontext und erstellt einen erweiterten Metafile-Handle.|
|[CMetaFileDC::Erstellen](#create)|Erstellt den Windows-Metadateigerätekontext und `CMetaFileDC` fügt ihn an das Objekt an.|
|[CMetaFileDC::CreateEnhanced](#createenhanced)|Erstellt einen Metadateigerätekontext für eine Metadatei im erweiterten Format.|

## <a name="remarks"></a>Bemerkungen

Um eine Windows-Metadatei zu `CMetaFileDC` implementieren, erstellen Sie zunächst ein Objekt. Rufen `CMetaFileDC` Sie den Konstruktor auf, und rufen Sie dann die [Memberfunktion](#create) Erstellen `CMetaFileDC` auf, die einen Windows-Metadateigerätekontext erstellt und an das Objekt anfügt.

Senden Sie `CMetaFileDC` dem Objekt anschließend die Reihenfolge der CDC-GDI-Befehle, die sie wiedergeben möchten. Es können nur die GDI-Befehle verwendet werden, die Ausgabe erstellen, z. `MoveTo` B. und `LineTo`.

Nachdem Sie die gewünschten Befehle an die `Close` Metadatei gesendet haben, rufen Sie die Memberfunktion auf, die die Metadateigerätekontexte schließt und ein Metadateihandle zurückgibt. Entsorgen Sie `CMetaFileDC` dann das Objekt.

[CDC::PlayMetaFile](../../mfc/reference/cdc-class.md#playmetafile) kann dann das Metadateihandle verwenden, um die Metadatei wiederholt wiederzugeben. Die Metadatei kann auch von Windows-Funktionen wie [CopyMetaFile](/windows/win32/api/wingdi/nf-wingdi-copymetafilew)bearbeitet werden, die eine Metadatei auf den Datenträger kopiert.

Wenn die Metadatei nicht mehr benötigt wird, löschen Sie sie mit der [DeleteMetaFile](/windows/win32/api/wingdi/nf-wingdi-deletemetafile) Windows-Funktion aus dem Speicher.

Sie können das `CMetaFileDC` Objekt auch so implementieren, dass es sowohl `GetTextExtent`Ausgabeaufrufe als auch Attribut-GDI-Aufrufe wie verarbeiten kann. Eine solche Metadatei ist flexibler und kann allgemeiner GDI-Code, der häufig aus einer Mischung aus Ausgabe- und Attributaufrufen besteht, leichter wiederverwenden. Die `CMetaFileDC` Klasse erbt zwei Gerätekontexte `m_hDC` und `m_hAttribDC`von CDC. Der `m_hDC` Gerätekontext verarbeitet alle CDC-GDI-Ausgabeaufrufe, und der [CDC](../../mfc/reference/cdc-class.md) `m_hAttribDC` Gerätekontext verarbeitet alle CDC GDI-Attributaufrufe. Normalerweise beziehen sich diese beiden Gerätekontexte auf dasselbe Gerät. Im Fall `CMetaFileDC`von ist das Attribut DC standardmäßig auf NULL festgelegt.

Erstellen Sie einen zweiten Gerätekontext, der auf den Bildschirm, einen Drucker `SetAttribDC` oder ein anderes Gerät als `m_hAttribDC`eine Metadatei verweist, und rufen Sie dann die Memberfunktion auf, um den neuen Gerätekontext mit zu verknüpfen. GDI-Informationsaufrufe werden nun an `m_hAttribDC`die neue gerichtet. Ausgabe-GDI-Aufrufe `m_hDC`gehen an , die die Metadatei darstellt.

Weitere Informationen `CMetaFileDC`zu finden Sie unter [Gerätekontexte](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CMetaFileDC`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxext.h

## <a name="cmetafiledcclose"></a><a name="close"></a>CMetaFileDC::Schließen

Schließt den Metadateigerätekontext und erstellt ein Windows-Metadateihandle, das mithilfe der [CDC::PlayMetaFile-Memberfunktion](../../mfc/reference/cdc-class.md#playmetafile) zum Abspielen der Metadatei verwendet werden kann.

```
HMETAFILE Close();
```

### <a name="return-value"></a>Rückgabewert

Eine gültige HMETAFILE, wenn die Funktion erfolgreich ist; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Das Windows-Metadateihandle kann auch verwendet werden, um die Metadatei mit Windows-Funktionen wie [CopyMetaFile](/windows/win32/api/wingdi/nf-wingdi-copymetafilew)zu bearbeiten.

Löschen Sie die Metadatei nach der Verwendung, indem Sie die Windows [DeleteMetaFile-Funktion](/windows/win32/api/wingdi/nf-wingdi-deletemetafile) aufrufen.

## <a name="cmetafiledccloseenhanced"></a><a name="closeenhanced"></a>CMetaFileDC::CloseEnhanced

Schließt einen erweiterten Metadatei-Gerätekontext und gibt ein Handle zurück, das eine Metadatei im erweiterten Format identifiziert.

```
HENHMETAFILE CloseEnhanced();
```

### <a name="return-value"></a>Rückgabewert

Ein Handle einer erweiterten Metadatei, falls erfolgreich; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Eine Anwendung kann das von dieser Funktion zurückgegebene Enhanced-Metafile-Handle verwenden, um die folgenden Aufgaben auszuführen:

- Anzeigen eines In einer erweiterten Metadatei gespeicherten Bildes

- Erstellen von Kopien der erweiterten Metadatei

- Aufzählen, Bearbeiten oder Kopieren einzelner Datensätze in der erweiterten Metadatei

- Abrufen einer optionalen Beschreibung des Metadateiinhalts aus dem erweiterten Metafile-Header

- Abrufen einer Kopie des erweiterten Metadateiheaders

- Abrufen einer binären Kopie der erweiterten Metadatei

- Aufzählen der Farben in der optionalen Palette

- Konvertieren einer Metadatei im erweiterten Format in eine Metadatei im Windows-Format

Wenn die Anwendung das erweiterte Metadateihandle nicht mehr benötigt, sollte sie `DeleteEnhMetaFile` das Handle durch Aufrufen der Win32-Funktion freigeben.

## <a name="cmetafiledccmetafiledc"></a><a name="cmetafiledc"></a>CMetaFileDC::CMetaFileDC

Erstellen `CMetaFileDC` Sie ein Objekt in zwei Schritten.

```
CMetaFileDC();
```

### <a name="remarks"></a>Bemerkungen

Rufen Sie `CMetaFileDC`zuerst `Create`auf , dann aufrufen Sie , wodurch `CMetaFileDC` der Windows-Metadateigerätekontext erstellt und an das Objekt angefügt wird.

## <a name="cmetafiledccreate"></a><a name="create"></a>CMetaFileDC::Erstellen

Erstellen `CMetaFileDC` Sie ein Objekt in zwei Schritten.

```
BOOL Create(LPCTSTR lpszFilename = NULL);
```

### <a name="parameters"></a>Parameter

*lpszDateiname*<br/>
Zeigt auf eine null-beendete Zeichenfolge. Gibt den Dateinamen der zu erstellenden Metadatei an. Wenn *lpszFilename* NULL ist, wird eine neue In-Memory-Metadatei erstellt.

### <a name="return-value"></a>Rückgabewert

Ist ungleich null (0), wenn die Funktion erfolgreich ausgeführt wird, andernfalls null (0).

### <a name="remarks"></a>Bemerkungen

Rufen Sie zunächst `CMetaFileDC`den Konstruktor auf, dann rufen Sie auf, `Create`der `CMetaFileDC` den Windows-Metadateigerätekontext erstellt und an das Objekt anfügt.

## <a name="cmetafiledccreateenhanced"></a><a name="createenhanced"></a>CMetaFileDC::CreateEnhanced

Erstellt einen Gerätekontext für eine Metadatei im erweiterten Format.

```
BOOL CreateEnhanced(
    CDC* pDCRef,
    LPCTSTR lpszFileName,
    LPCRECT lpBounds,
    LPCTSTR lpszDescription);
```

### <a name="parameters"></a>Parameter

*pDCRef*<br/>
Identifiziert ein Referenzgerät für die erweiterte Metadatei.

*lpszFileName*<br/>
Zeigt auf eine null-beendete Zeichenfolge. Gibt den Dateinamen für die erweiterte Metadatei an, die erstellt werden soll. Wenn dieser Parameter NULL ist, ist die erweiterte Metadatei speicherbasiert und ihr Inhalt `DeleteEnhMetaFile` geht verloren, wenn das Objekt zerstört wird oder wenn die Win32-Funktion aufgerufen wird.

*lpBounds*<br/>
Zeigt auf eine [RECT-Datenstruktur](/windows/win32/api/windef/ns-windef-rect) oder ein [CRect-Objekt,](../../atl-mfc-shared/reference/crect-class.md) das die Dimensionen in HIMETRIC-Einheiten (in 0,01-Millimeter-Schritten) des Bildes angibt, das in der erweiterten Metadatei gespeichert werden soll.

*lpszBeschreibung*<br/>
Zeigt auf eine Null-Termin-Zeichenfolge, die den Namen der Anwendung angibt, die das Bild erstellt hat, sowie den Titel des Bildes.

### <a name="return-value"></a>Rückgabewert

Ein Handle des Gerätekontexts für die erweiterte Metadatei, falls erfolgreich; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Dieser DC kann verwendet werden, um ein geräteunabhängiges Bild zu speichern.

Windows verwendet das Referenzgerät, das durch den *Parameter pDCRef* identifiziert wird, um die Auflösung und Die Einheiten des Geräts aufzuzeichnen, auf dem ursprünglich ein Bild angezeigt wurde. Wenn der *pDCRef-Parameter* NULL ist, verwendet er das aktuelle Anzeigegerät als Referenz.

Die linken und oberen `RECT` Elemente der Datenstruktur, auf die der *Parameter lpBounds* zeigt, müssen kleiner als die rechten bzw. unteren Elemente sein. Punkte entlang der Ränder des Rechtecks sind im Bild enthalten. Wenn *lpBounds* NULL ist, berechnet die Grafikgeräteschnittstelle (GDI) die Abmessungen des kleinsten Rechtecks, das das von der Anwendung gezeichnete Bild umschließen kann. Der *Parameter lpBounds* sollte nach Möglichkeit angegeben werden.

Die Zeichenfolge, auf die der Parameter *lpszDescription* zeigt, muss ein Nullzeichen zwischen dem Anwendungsnamen und dem Bildnamen enthalten und mit zwei Nullzeichen enden, z. B. "XYZ Graphics Editor, "0Bald Eagle, 0, "0", wobei die Zeichenmarke "0" das Nullzeichen darstellt. Wenn *lpszDescription* NULL ist, gibt es keinen entsprechenden Eintrag im enhanced-metafile-Header.

Anwendungen verwenden den von dieser Funktion erstellten Domänencontroller, um ein Grafikbild in einer erweiterten Metadatei zu speichern. Das Handle, das diesen DC identifiziert, kann an jede GDI-Funktion übergeben werden.

Nachdem eine Anwendung ein Bild in einer erweiterten Metadatei gespeichert hat, kann `CDC::PlayMetaFile` das Bild auf jedem Ausgabegerät angezeigt werden, indem die Funktion aufgerufen wird. Bei der Anzeige des Bildes verwendet Windows das Rechteck, auf das der Parameter lpBounds zeigt, und die *Auflösungsdaten* des Referenzgeräts, um das Bild zu positionieren und zu skalieren. Der von dieser Funktion zurückgegebene Gerätekontext enthält dieselben Standardattribute, die jedem neuen Domänencontroller zugeordnet sind.

Anwendungen müssen die Win32-Funktion `GetWinMetaFileBits` verwenden, um eine erweiterte Metadatei in das ältere Windows-Metadateiformat zu konvertieren.

Der Dateiname für die erweiterte Metadatei sollte die verwenden. EMF-Erweiterung.

## <a name="see-also"></a>Siehe auch

[CDC-Klasse](../../mfc/reference/cdc-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
