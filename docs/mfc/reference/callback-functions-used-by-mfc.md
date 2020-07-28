---
title: Von MFC verwendete Rückruffunktionen
ms.date: 11/04/2016
helpviewer_keywords:
- callback functions [MFC], MFC
- MFC, callback functions
- functions [MFC], callback
- callback functions [MFC]
ms.assetid: b2a6857c-fdd3-45ec-8fd8-2e71fac77582
ms.openlocfilehash: 19c0bd3a0685abe36c020a5dda930f5683a4baa9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87183434"
---
# <a name="callback-functions-used-by-mfc"></a>Von MFC verwendete Rückruffunktionen

Drei Rückruf Funktionen werden in der Microsoft Foundation Class-Bibliothek angezeigt. Diese Rückruf Funktionen werden an [CDC:: enujubjects](../../mfc/reference/cdc-class.md#enumobjects), [CDC:: graystring](../../mfc/reference/cdc-class.md#graystring)und [CDC:: abtabortproc](../../mfc/reference/cdc-class.md#setabortproc)übermittelt. Beachten Sie, dass alle Rückruf Funktionen vor der Rückgabe an Windows MFC-Ausnahmen abfangen müssen, da Ausnahmen nicht über Rückruf Grenzen hinweg ausgelöst werden können. Weitere Informationen zu Ausnahmen finden Sie im Artikel [Ausnahmen](../../mfc/exception-handling-in-mfc.md).

|Name||
|----------|-----------------|
|[Rückruffunktion für CDC::EnumObjects](#enum_objects)||
|[Rückruffunktion für CDC::GrayString](#graystring)||
|[Rückruffunktion für CDC::SetAbortProc](#setabortproc)||

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxwin.h

## <a name="callback-function-for-cdcenumobjects"></a><a name="enum_objects"></a>Rückruffunktion für CDC:: enumujects

Der *objectfunc* -Name ist ein Platzhalter für den von der Anwendung bereitgestellten Funktionsnamen.

### <a name="syntax"></a>Syntax

```
int CALLBACK EXPORT ObjectFunc(
    LPSTR lpszLogObject,
    LPSTR* lpData);
```

### <a name="parameters"></a>Parameter

*lpszlogobject*<br/>
Verweist auf eine [logpen](/windows/win32/api/Wingdi/ns-wingdi-logpen) -oder [logbrush](/windows/win32/api/wingdi/ns-wingdi-logbrush) -Datenstruktur, die Informationen zu den logischen Attributen des-Objekts enthält.

*lpdata*<br/>
Verweist auf die von der Anwendung bereitgestellten Daten, die an die Funktion übergeben werden `EnumObjects` .

### <a name="return-value"></a>Rückgabewert

Die Rückruffunktion gibt zurück **`int`** . Der Wert dieser Rückgabe ist Benutzer definiert. Wenn die Rückruffunktion 0 zurückgibt, `EnumObjects` hält die Enumeration frühzeitig an.

### <a name="remarks"></a>Bemerkungen

Der tatsächliche Name muss exportiert werden.

## <a name="callback-function-for-cdcgraystring"></a><a name="graystring"></a>Rückruffunktion für CDC:: graystring

*OutputFunc* ist ein Platzhalter für den von der Anwendung bereitgestellten Rückruf Funktionsnamen.

### <a name="syntax"></a>Syntax

```
BOOL CALLBACK EXPORT OutputFunc(
    HDC hDC,
    LPARAM lpData,
    int nCount);
```

### <a name="parameters"></a>Parameter

*HDC*<br/>
Identifiziert einen Speichergeräte Kontext mit einer Bitmap von mindestens der von und angegebenen Breite und Höhe `nWidth` `nHeight` `GrayString` .

*lpdata*<br/>
Zeigt auf die zu zeichnende Zeichenfolge.

*nCount*<br/>
Gibt die Anzahl von Zeichen an, die ausgegeben werden sollen.

### <a name="return-value"></a>Rückgabewert

Der Rückgabewert der Rückruffunktion muss "true" sein, um den Erfolg anzugeben. Andernfalls ist Sie false.

### <a name="remarks"></a>Bemerkungen

Die Rückruffunktion (*OutputFunc*) muss ein Bild relativ zu den Koordinaten (0, 0) anstelle von (*x*, *y*) zeichnen.

## <a name="callback-function-for-cdcsetabortproc"></a><a name="setabortproc"></a>Rückruffunktion für CDC:: abtabortproc

Der Name *abortfunc* ist ein Platzhalter für den von der Anwendung bereitgestellten Funktionsnamen.

### <a name="syntax"></a>Syntax

```
BOOL CALLBACK EXPORT AbortFunc(
    HDC hPr,
    int code);
```

### <a name="parameters"></a>Parameter

*HPR*<br/>
Identifiziert den Gerätekontext.

*code*<br/>
Gibt an, ob ein Fehler aufgetreten ist. Der Wert ist 0, wenn kein Fehler aufgetreten ist. Es ist SP_OUTOFDISK, wenn der Druck-Manager zurzeit nicht über genügend Speicherplatz verfügt und bei der Wartezeit der Anwendung mehr Speicherplatz verfügbar wird. Wenn *Code* SP_OUTOFDISK ist, muss die Anwendung den Druckauftrag nicht abbrechen. Wenn dies nicht der Fall ist, muss Sie dem Druck-Manager durch Aufrufen der-oder der Windows-Funktion zurückzugeben `PeekMessage` `GetMessage` .

### <a name="return-value"></a>Rückgabewert

Der Rückgabewert der Abort-Handler-Funktion ist ungleich 0 (null), wenn der Druckauftrag fortgesetzt werden soll, und 0, wenn er abgebrochen wird.

### <a name="remarks"></a>Bemerkungen

Der tatsächliche Name muss exportiert werden, wie im Abschnitt "Hinweise" von [CDC:: abtabortproc](../../mfc/reference/cdc-class.md#setabortproc)beschrieben.

## <a name="see-also"></a>Weitere Informationen

[Strukturen, Stile, Rückrufe und Meldungs Zuordnungen](structures-styles-callbacks-and-message-maps.md)<br/>
[CDC:: umumujects](../../mfc/reference/cdc-class.md#enumobjects)<br/>
[CDC:: abtabortproc](../../mfc/reference/cdc-class.md#setabortproc)<br/>
[CDC:: graystring](../../mfc/reference/cdc-class.md#graystring)
