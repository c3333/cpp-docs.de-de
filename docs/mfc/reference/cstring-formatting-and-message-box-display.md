---
title: CString-Formatierung und Meldungsfeldanzeige
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects [MFC], formatting and message boxes
ms.assetid: d1068cf4-9cc5-4952-b9e7-d612c53cbc28
ms.openlocfilehash: d30d26ecf0e72ee33affe3df5b88c438ff83bb6b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365994"
---
# <a name="cstring-formatting-and-message-box-display"></a>CString-Formatierung und Meldungsfeldanzeige

Zum Formatieren und Analysieren von `CString` Objekten werden eine Reihe von Funktionen bereitgestellt. Sie können diese Funktionen immer `CString` dann verwenden, wenn Sie Objekte bearbeiten müssen, aber sie sind besonders nützlich für das Formatieren von Zeichenfolgen, die im Text in den Meldungsfeldtexten angezeigt werden.

Diese Gruppe von Funktionen enthält auch eine globale Routine zum Anzeigen eines Meldungsfelds.

### <a name="cstring-functions"></a>CString-Funktionen

|||
|-|-|
|[AfxExtractSubString](#afxextractsubstring)|Extrahiert Unterzeichenfolgen, die durch ein einzelnes Zeichen getrennt sind, aus einer bestimmten Quellzeichenfolge.|
|[AfxFormatString1](#afxformatstring1)|Ersetzt eine bestimmte Zeichenfolge durch die Formatzeichen "%1" in einer Zeichenfolge, die in der Zeichenfolgentabelle enthalten ist.|
|[AfxFormatString2](#afxformatstring2)|Ersetzt zwei Zeichenfolgen für die Formatzeichen "%1" und "%2" in einer Zeichenfolge, die in der Zeichenfolgentabelle enthalten ist.|
|[AfxMessageBox](#afxmessagebox)|Zeigt ein Meldungsfeld an.|

### <a name="requirements"></a>Anforderungen

  **Header** afxwin.h

## <a name="afxextractsubstring"></a><a name="afxextractsubstring"></a>AfxExtractSubString

Diese globale Funktion kann verwendet werden, um eine Teilzeichenfolge aus einer bestimmten Quellzeichenfolge zu extrahieren.

```
BOOL AFXAPI AfxExtractSubString (
    CString& rString,
    LPCTSTR lpszFullString,
    int iSubString,
    TCHAR chSep  = '\n');
```

### <a name="parameters"></a>Parameter

*rString*<br/>
Verweis auf ein [CString-Objekt,](../../atl-mfc-shared/using-cstring.md) das eine einzelne Teilzeichenfolge empfängt.

*lpszFullString*<br/>
Zeichenfolge, die den vollständigen Text der Zeichenfolge enthält, aus der extrahiert werden soll.

*iSubString*<br/>
Nullbasierter Index der Teilzeichenfolge, die aus *lpszFullString*extrahiert werden soll.

*chSep*<br/>
Trennzeichen, das zum Trennen von Teilzeichenfolgen verwendet wird.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Funktion die Teilzeichenfolge am bereitgestellten Index erfolgreich extrahiert hat; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Funktion ist nützlich, um mehrere Teilzeichenfolgen aus einer Quellzeichenfolge zu extrahieren, wenn ein bekanntes einzelnes Zeichen jede Teilzeichenfolge trennt. Diese Funktion sucht jedes Mal, wenn sie aufgerufen wird, vom Anfang des *parameters lpszFullString.*

Diese Funktion gibt FALSE zurück, wenn entweder *lpszFullString* auf NULL gesetzt ist oder die Funktion das Ende von *lpszFullString* erreicht, ohne *iSubString*+1-Vorkommen des angegebenen Trennzeichens zu finden. Der *parameter rString* wird nicht von seinem ursprünglichen Wert geändert, wenn *lpszFullString* auf NULL gesetzt wurde. Andernfalls wird der *Parameter rString* auf die leere Zeichenfolge gesetzt, wenn die Teilzeichenfolge für den angegebenen Index nicht extrahiert werden konnte.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_Utilities#48](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_1.cpp)]

### <a name="requirements"></a>Anforderungen

  **Header** afxwin.h

## <a name="afxformatstring1"></a><a name="afxformatstring1"></a>AfxFormatString1

Ersetzt die Zeichenfolge, auf die *lpsz1* zeigt, für alle Instanzen der Zeichen "%1" in der Vorlagenzeichenfolgenressource, die von *nIDS*identifiziert wird.

```
void  AfxFormatString1(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1);
```

### <a name="parameters"></a>Parameter

*rString*<br/>
Ein Verweis `CString` auf ein Objekt, das die resultierende Zeichenfolge enthält, nachdem die Ersetzung ausgeführt wurde.

*Nids*<br/>
Die Ressourcen-ID der Vorlagenzeichenfolge, für die die Ersetzung ausgeführt wird.

*lpsz1*<br/>
Eine Zeichenfolge, die die Formatzeichen "%1" in der Vorlagenzeichenfolge ersetzt.

### <a name="remarks"></a>Bemerkungen

Die neu gebildete Zeichenfolge wird in *rString*gespeichert. Wenn die Zeichenfolge in der Zeichenfolgentabelle z. B. "Datei %1 nicht gefunden" ist und *lpsz1* gleich "C:'MYFILE' ist. TXT", dann *rString* enthält die Zeichenfolge "Datei C:'MYFILE. TXT nicht gefunden". Diese Funktion ist nützlich zum Formatieren von Zeichenfolgen, die an Meldungsfelder und andere Fenster gesendet werden.

Wenn die Formatzeichen "%1" mehr als einmal in der Zeichenfolge angezeigt werden, werden mehrere Ersetzungen vorgenommen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_Utilities#25](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_2.cpp)]

### <a name="requirements"></a>Anforderungen

  **Header** afxwin.h

## <a name="afxformatstring2"></a><a name="afxformatstring2"></a>AfxFormatString2

Ersetzt die Zeichenfolge, auf die *lpsz1* zeigt, für alle Instanzen der Zeichen "%1" und die Zeichenfolge, auf die von *lpsz2* verwiesen wird, für alle Instanzen der Zeichen "%2" in der Vorlagenzeichenfolgenressource, die von *nIDS*identifiziert wird.

```
void AfxFormatString2(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1,
    LPCTSTR lpsz2);
```

### <a name="parameters"></a>Parameter

*rString*<br/>
Ein Verweis `CString` auf die, die die resultierende Zeichenfolge enthält, nachdem die Ersetzung ausgeführt wurde.

*Nids*<br/>
Die Zeichenfolgentabellen-ID der Vorlagenzeichenfolge, für die die Ersetzung ausgeführt wird.

*lpsz1*<br/>
Eine Zeichenfolge, die die Formatzeichen "%1" in der Vorlagenzeichenfolge ersetzt.

*lpsz2*<br/>
Eine Zeichenfolge, die die Formatzeichen "%2" in der Vorlagenzeichenfolge ersetzt.

### <a name="remarks"></a>Bemerkungen

Die neu gebildete Zeichenfolge wird in *rString*gespeichert. Wenn die Zeichenfolge in der Zeichenfolgentabelle beispielsweise "Datei %1 ist, die im Verzeichnis %2 nicht gefunden wurde", zeigt *lpsz1* auf "MYFILE" ab. TXT" und *lpsz2* zeigt auf "C:-MYDIR", dann enthält *rString* die Zeichenfolge "File MYFILE. TXT wurde nicht im Verzeichnis C:'MYDIR' gefunden.

Wenn die Formatzeichen "%1" oder "%2" mehr als einmal in der Zeichenfolge angezeigt werden, werden mehrere Ersetzungen vorgenommen. Sie müssen nicht in numerischer Reihenfolge sein.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_Utilities#26](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_3.cpp)]

### <a name="requirements"></a>Anforderungen

  **Header** afxwin.h

## <a name="afxmessagebox"></a><a name="afxmessagebox"></a>AfxMessageBox

Zeigt ein Meldungsfeld auf dem Bildschirm an.

```
int AfxMessageBox(
    LPCTSTR lpszText,
    UINT nType = MB_OK,
    UINT nIDHelp = 0);

int AFXAPI AfxMessageBox(
    UINT nIDPrompt,
    UINT nType = MB_OK,
    UINT nIDHelp = (UINT) -1);
```

### <a name="parameters"></a>Parameter

*lpszText*<br/>
Zeigt auf ein `CString`-Objekt oder auf eine auf NULL endende Zeichenfolge, worin die im Meldungsfeld anzuzeigende Meldung enthalten ist.

*nType*<br/>
Der Stil des Meldungsfelds. Wenden Sie einen der [Meldungsfeldstile](../../mfc/reference/styles-used-by-mfc.md#message-box-styles) auf das Feld an.

*nIDHelp*<br/>
Die Hilfekontext-ID für die Meldung; 0 gibt an, dass der Standardhilfekontext der Anwendung verwendet wird.

*nIDPrompt*<br/>
Eine eindeutige ID, die verwendet wird, um auf eine Zeichenfolge in der Zeichenfolgentabelle zu verweisen.

### <a name="return-value"></a>Rückgabewert

Null (0), wenn nicht genügend Arbeitsspeicher vorhanden ist, um des Meldungsfelds anzuzeigen; andernfalls wird einer der folgenden Werte zurückgegeben:

- IDABORT Die Schaltfläche Abbrechen wurde ausgewählt.

- IDCANCEL Die Schaltfläche Abbrechen wurde ausgewählt.

- IDIGNORE Die Schaltfläche Ignorieren wurde ausgewählt.

- IDNO Die Schaltfläche Nein wurde ausgewählt.

- IDOK Die Schaltfläche OK wurde ausgewählt.

- IDRETRY Die Schaltfläche "Wiederholen" wurde ausgewählt.

- IDYES Die Schaltfläche Ja wurde ausgewählt.

Sofern ein Meldungsfeld über die Schaltfläche "Abbrechen" verfügt, wird der IDCANCEL-Wert zurückgegeben, wenn entweder die ESC-TASTE gedrückt oder die Schaltfläche "Abbrechen" gewählt wird. Enthält das Meldungsfeld keine Schaltfläche "Abbrechen", hat das Drücken der ESC-TASTE keine Auswirkung.

Die Funktionen [AfxFormatString1](#afxformatstring1) und [AfxFormatString2](#afxformatstring2) können beim Formatieren von Text nützlich sein, der in einem Meldungsfeld angezeigt wird.

### <a name="remarks"></a>Bemerkungen

Die erste Form dieser überladenen Funktion zeigt eine Textzeichenfolge an, auf die *lpszText* im Meldungsfeld zeigt, und verwendet *nIDHelp,* um einen Hilfekontext zu beschreiben. Der Hilfekontext wird verwendet, um zu einem zugeordneten Hilfethema zu wechseln, wenn der Benutzer die Hilfetaste drückt (in der Regel F1).

Die zweite Form der Funktion verwendet die Zeichenfolgenressource mit der ID *nIDPrompt,* um eine Meldung im Meldungsfeld anzuzeigen. Die zugehörige Hilfeseite wird über den Wert von *nIDHelp*gefunden. Wenn der Standardwert von *nIDHelp* (-1) verwendet wird, wird die Zeichenfolgenressourcen-ID *nIDPrompt*für den Hilfekontext verwendet. Weitere Informationen zum Definieren von Hilfekontexten finden Sie unter [Technischer Hinweis 28](../../mfc/tn028-context-sensitive-help-support.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#133](../../mfc/reference/codesnippet/cpp/cstring-formatting-and-message-box-display_4.cpp)]

## <a name="see-also"></a>Siehe auch

[MFC-Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CStringT-Klasse](../../atl-mfc-shared/reference/cstringt-class.md)
