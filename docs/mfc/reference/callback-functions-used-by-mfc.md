---
title: Von MFC verwendete Rückruffunktionen
ms.date: 11/04/2016
helpviewer_keywords:
- callback functions [MFC], MFC
- MFC, callback functions
- functions [MFC], callback
- callback functions [MFC]
ms.assetid: b2a6857c-fdd3-45ec-8fd8-2e71fac77582
ms.openlocfilehash: 8d84f939795e768c6b1356dcd8dc291421aedfdc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371141"
---
# <a name="callback-functions-used-by-mfc"></a>Von MFC verwendete Rückruffunktionen

Drei Rückruffunktionen werden in der Microsoft Foundation-Klassenbibliothek angezeigt. Diese Rückruffunktionen werden an [CDC::EnumObjects](../../mfc/reference/cdc-class.md#enumobjects), [CDC::GrayString](../../mfc/reference/cdc-class.md#graystring)und [CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc)übergeben. Beachten Sie, dass alle Rückruffunktionen MFC-Ausnahmen abfangen müssen, bevor sie zu Windows zurückkehren, da Ausnahmen nicht über Rückrufgrenzen hinweg ausgelöst werden können. Weitere Informationen zu Ausnahmen finden Sie im Artikel [Ausnahmen](../../mfc/exception-handling-in-mfc.md).

|Name||
|----------|-----------------|
|[Rückruffunktion für CDC::EnumObjects](#enum_objects)||
|[Rückruffunktion für CDC::GrayString](#graystring)||
|[Rückruffunktion für CDC::SetAbortProc](#setabortproc)||

## <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="callback-function-for-cdcenumobjects"></a><a name="enum_objects"></a>Rückruffunktion für CDC::EnumObjects

Der *ObjectFunc-Name* ist ein Platzhalter für den von der Anwendung bereitgestellten Funktionsnamen.

### <a name="syntax"></a>Syntax

```
int CALLBACK EXPORT ObjectFunc(
    LPSTR lpszLogObject,
    LPSTR* lpData);
```

### <a name="parameters"></a>Parameter

*lpszLogObject*<br/>
Verweist auf eine [LOGPEN-](/windows/win32/api/Wingdi/ns-wingdi-logpen) oder [LOGBRUSH-Datenstruktur,](/windows/win32/api/wingdi/ns-wingdi-logbrush) die Informationen zu den logischen Attributen des Objekts enthält.

*lpData*<br/>
Verweist auf die von der `EnumObjects` Anwendung bereitgestellten Daten, die an die Funktion übergeben werden.

### <a name="return-value"></a>Rückgabewert

Die Rückruffunktion gibt eine **int**zurück. Der Wert dieser Rückgabe ist benutzerdefiniert. Wenn die Rückruffunktion 0 `EnumObjects` zurückgibt, wird die Enumeration vorzeitig beendet.

### <a name="remarks"></a>Bemerkungen

Der tatsächliche Name muss exportiert werden.

## <a name="callback-function-for-cdcgraystring"></a><a name="graystring"></a>Rückruffunktion für CDC::GrayString

*OutputFunc* ist ein Platzhalter für den von der Anwendung bereitgestellten Rückruffunktionsnamen.

### <a name="syntax"></a>Syntax

```
BOOL CALLBACK EXPORT OutputFunc(
    HDC hDC,
    LPARAM lpData,
    int nCount);
```

### <a name="parameters"></a>Parameter

*Hdc*<br/>
Identifiziert einen Speichergerätekontext mit einer Bitmap, die `nWidth` mindestens `nHeight` `GrayString`die von und an angegebene Breite und Höhe aufweist.

*lpData*<br/>
Zeigt auf die zu zeichnende Zeichenfolge.

*nCount*<br/>
Gibt die Anzahl der ausauszugebenden Zeichen an.

### <a name="return-value"></a>Rückgabewert

Der Rückgabewert der Rückruffunktion muss TRUE sein, um den Erfolg anzuzeigen. andernfalls ist es FALSE.

### <a name="remarks"></a>Bemerkungen

Die Rückruffunktion (*OutputFunc*) muss ein Bild relativ zu den Koordinaten (0,0) und nicht (*x*, *y*) zeichnen.

## <a name="callback-function-for-cdcsetabortproc"></a><a name="setabortproc"></a>Rückruffunktion für CDC::SetAbortProc

Der Name *AbortFunc* ist ein Platzhalter für den von der Anwendung bereitgestellten Funktionsnamen.

### <a name="syntax"></a>Syntax

```
BOOL CALLBACK EXPORT AbortFunc(
    HDC hPr,
    int code);
```

### <a name="parameters"></a>Parameter

*Hpr*<br/>
Identifiziert den Gerätekontext.

*Code*<br/>
Gibt an, ob ein Fehler aufgetreten ist. Es ist 0, wenn kein Fehler aufgetreten ist. Es ist SP_OUTOFDISK, ob der Druck-Manager derzeit nicht mehr Speicherplatz hat und mehr Speicherplatz verfügbar ist, wenn die Anwendung wartet. Wenn *Code* SP_OUTOFDISK ist, muss die Anwendung den Druckauftrag nicht abbrechen. Ist dies nicht der Fall, muss er `PeekMessage` `GetMessage` dem Druck-Manager nachgeben, indem er die oder Windows-Funktion aufruft.

### <a name="return-value"></a>Rückgabewert

Der Rückgabewert der Abbruchhandlerfunktion ist ungleich Null, wenn der Druckauftrag fortgesetzt werden soll, und 0, wenn er abgebrochen wird.

### <a name="remarks"></a>Bemerkungen

Der tatsächliche Name muss exportiert werden, wie im Abschnitt "Hinweise" von [CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc)beschrieben.

## <a name="see-also"></a>Siehe auch

[Strukturen, Stile, Rückrufe und Meldungszuordnungen](structures-styles-callbacks-and-message-maps.md)<br/>
[CDC::EnumObjects](../../mfc/reference/cdc-class.md#enumobjects)<br/>
[CDC::SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc)<br/>
[CDC::GrayString](../../mfc/reference/cdc-class.md#graystring)
