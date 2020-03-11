---
title: CString-Formatierung und Meldungsfeldanzeige
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects [MFC], formatting and message boxes
ms.assetid: d1068cf4-9cc5-4952-b9e7-d612c53cbc28
ms.openlocfilehash: ad880c5302fd2274c5d46719e912461fd7497f10
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78854060"
---
# <a name="cstring-formatting-and-message-box-display"></a>CString-Formatierung und Meldungsfeldanzeige

Zum Formatieren und Analysieren von `CString` Objekten stehen eine Reihe von Funktionen zur Verfügung. Sie können diese Funktionen immer dann verwenden, wenn Sie `CString` Objekte bearbeiten müssen, Sie sind jedoch besonders nützlich für das Formatieren von Zeichen folgen, die im Meldungs Feld Text angezeigt werden.

Diese Gruppe von Funktionen umfasst auch eine globale Routine zum Anzeigen eines Meldungs Felds.

### <a name="cstring-functions"></a>CString-Funktionen

|||
|-|-|
|[Afxextractsubstring](#afxextractsubstring)|Extrahiert Teil Zeichenfolgen, die durch ein einzelnes Zeichen einer angegebenen Quell Zeichenfolge getrennt sind.|
|[AfxFormatString1](#afxformatstring1)|Ersetzt eine angegebene Zeichenfolge für die Formatzeichen "%1" in einer Zeichenfolge, die in der Zeichen folgen Tabelle enthalten ist.|
|[AfxFormatString2](#afxformatstring2)|Ersetzt zwei Zeichen folgen für die Formatzeichen "%1" und "%2" in einer Zeichenfolge, die in der Zeichen folgen Tabelle enthalten ist.|
|[AfxMessageBox](#afxmessagebox)|Zeigt ein Meldungsfeld an.|

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** AFXWIN. h

##  <a name="afxextractsubstring"></a>Afxextractsubstring

Diese globale Funktion kann verwendet werden, um eine Teil Zeichenfolge aus einer angegebenen Quell Zeichenfolge zu extrahieren.

```
BOOL AFXAPI AfxExtractSubString (
    CString& rString,
    LPCTSTR lpszFullString,
    int iSubString,
    TCHAR chSep  = '\n');
```

### <a name="parameters"></a>Parameter

*RString*<br/>
Verweis auf ein [CString](../../atl-mfc-shared/using-cstring.md) -Objekt, das eine einzelne Teil Zeichenfolge empfängt.

*lpszfullstring*<br/>
Eine Zeichenfolge mit dem vollständigen Text der Zeichenfolge, aus der extrahiert werden soll.

*isubstring*<br/>
NULL basierter Index der Teil Zeichenfolge, die aus *lpszfullstring*extrahiert werden soll.

*chsep*<br/>
Trennzeichen, das zum Begrenzen von Teil Zeichenfolgen verwendet wird.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Funktion erfolgreich die Teil Zeichenfolge am bereitgestellten Index extrahiert hat. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Diese Funktion eignet sich zum Extrahieren mehrerer Teil Zeichenfolgen aus einer Quell Zeichenfolge, wenn ein bekanntes einzelnes Zeichen jede Teil Zeichenfolge trennt. Diese Funktion sucht nach dem Anfang des *lpszfullstring* -Parameters jedes Mal, wenn er aufgerufen wird.

Diese Funktion gibt false zurück, wenn entweder " *lpszfullstring* " auf NULL festgelegt ist oder die Funktion das Ende von " *lpszfullstring* " erreicht, ohne dass " *isubstring*+ 1"-Vorkommen des angegebenen Trenn Zeichens gefunden werden. Der Parameter " *RString* " wird nicht von seinem ursprünglichen Wert geändert, wenn " *lpszfullstring* " auf NULL festgelegt wurde. Andernfalls wird der *RString* -Parameter auf die leere Zeichenfolge festgelegt, wenn die Teil Zeichenfolge für den angegebenen Index nicht extrahiert werden konnte.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_Utilities#48](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_1.cpp)]

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** AFXWIN. h

##  <a name="afxformatstring1"></a>AfxFormatString1

Ersetzt die Zeichenfolge, auf die durch *lpsz1* auf alle Instanzen der Zeichen "%1" in der von *NIDS*identifizierten Vorlagen Zeichenfolgen-Ressource verwiesen wird.

```
void  AfxFormatString1(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1);
```

### <a name="parameters"></a>Parameter

*RString*<br/>
Ein Verweis auf ein `CString` Objekt, das die resultierende Zeichenfolge enthält, nachdem die Ersetzung durchgeführt wurde.

*NIDS*<br/>
Die Ressourcen-ID der Vorlagen Zeichenfolge, für die die Ersetzung durchgeführt wird.

*lpsz1*<br/>
Eine Zeichenfolge, die die Formatzeichen "%1" in der Vorlagen Zeichenfolge ersetzt.

### <a name="remarks"></a>Bemerkungen

Die neu formatierte Zeichenfolge wird in *RString*gespeichert. Wenn die Zeichenfolge in der Zeichen folgen Tabelle z. b. "Datei %1 nicht gefunden" lautet und *lpsz1* gleich "c:\MyFile. TXT ", dann enthält *RString* die Zeichenfolge" file c:\MyFile. TXT nicht gefunden ". Diese Funktion eignet sich zum Formatieren von Zeichen folgen, die an Meldungs Felder und andere Fenster gesendet werden.

Wenn die Formatzeichen "%1" mehrmals in der Zeichenfolge vorkommen, werden mehrere Ersetzungen vorgenommen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_Utilities#25](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_2.cpp)]

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** AFXWIN. h

##  <a name="afxformatstring2"></a>AfxFormatString2

Ersetzt die Zeichenfolge, auf die durch *lpsz1* auf alle Instanzen der Zeichen "%1" gezeigt wird, und die Zeichenfolge, auf die *lpsz2* für alle Instanzen der Zeichen "%2" verweist, in der von *NIDS*identifizierten Vorlagen Zeichenfolgen-Ressource.

```
void AfxFormatString2(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1,
    LPCTSTR lpsz2);
```

### <a name="parameters"></a>Parameter

*RString*<br/>
Ein Verweis auf die `CString`, die die resultierende Zeichenfolge nach der Ersetzung enthalten wird.

*NIDS*<br/>
Die Zeichen folgen-Tabellen-ID der Vorlagen Zeichenfolge, für die die Ersetzung durchgeführt wird.

*lpsz1*<br/>
Eine Zeichenfolge, die die Formatzeichen "%1" in der Vorlagen Zeichenfolge ersetzt.

*lpsz2*<br/>
Eine Zeichenfolge, die die Formatzeichen "%2" in der Vorlagen Zeichenfolge ersetzt.

### <a name="remarks"></a>Bemerkungen

Die neu formatierte Zeichenfolge wird in *RString*gespeichert. Wenn die Zeichenfolge in der Zeichen folgen Tabelle z. b. "Datei %1 wurde nicht im Verzeichnis %2 gefunden" angezeigt wird, verweist *lpsz1* auf "MyFile. TXT ", und *lpsz2* verweist auf" c:\meinedir ", dann enthält *RString* die Zeichenfolge" File MyFile. TXT wurde nicht im Verzeichnis "c:\meineidir" gefunden. "

Wenn die Formatzeichen "%1" oder "%2" mehrmals in der Zeichenfolge vorkommen, werden mehrere Ersetzungen vorgenommen. Sie müssen nicht in numerischer Reihenfolge sein.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_Utilities#26](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_3.cpp)]

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** AFXWIN. h

##  <a name="afxmessagebox"></a>AfxMessageBox

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
Der Stil des Meldungsfelds. Wenden Sie alle Meldungs [Feld Stile](../../mfc/reference/styles-used-by-mfc.md#message-box-styles) auf das Feld an.

*nidhelp*<br/>
Die Hilfekontext-ID für die Meldung; 0 gibt an, dass der Standardhilfekontext der Anwendung verwendet wird.

*nidprompt*<br/>
Eine eindeutige ID, die verwendet wird, um auf eine Zeichenfolge in der Zeichenfolgentabelle zu verweisen.

### <a name="return-value"></a>Rückgabewert

Null (0), wenn nicht genügend Arbeitsspeicher vorhanden ist, um des Meldungsfelds anzuzeigen; andernfalls wird einer der folgenden Werte zurückgegeben:

- Idabort: die Schaltfläche "Abbrechen" wurde ausgewählt.

- IDCANCEL die Schaltfläche Abbrechen wurde ausgewählt.

- IDIGNORE die Schaltfläche "ignorieren" wurde ausgewählt.

- IDNO die Schaltfläche "Nein" wurde ausgewählt.

- IDOK die Schaltfläche OK wurde ausgewählt.

- Idretry die Schaltfläche "Wiederholen" wurde ausgewählt.

- Wird die Schaltfläche Ja ausgewählt.

Sofern ein Meldungsfeld über die Schaltfläche "Abbrechen" verfügt, wird der IDCANCEL-Wert zurückgegeben, wenn entweder die ESC-TASTE gedrückt oder die Schaltfläche "Abbrechen" gewählt wird. Enthält das Meldungsfeld keine Schaltfläche "Abbrechen", hat das Drücken der ESC-TASTE keine Auswirkung.

Die Funktionen [AfxFormatString1](#afxformatstring1) und [AfxFormatString2](#afxformatstring2) können nützlich sein, um Text zu formatieren, der in einem Meldungs Feld angezeigt wird.

### <a name="remarks"></a>Bemerkungen

Die erste Form dieser überladenen Funktion zeigt eine Text Zeichenfolge an, auf die *lpszText* im Meldungs Feld verweist, und verwendet *nidhelp* , um einen Hilfe Kontext zu beschreiben. Der Hilfekontext wird verwendet, um zu einem zugeordneten Hilfethema zu wechseln, wenn der Benutzer die Hilfetaste drückt (in der Regel F1).

Die zweite Form der Funktion verwendet die Zeichen folgen Ressource mit der ID *nidprompt* , um eine Meldung im Meldungs Feld anzuzeigen. Die zugehörige Hilfeseite wird über den Wert von *nidhelp*gefunden. Wenn der Standardwert von " *nidhelp* " (-1) verwendet wird, wird die Zeichen folgen Ressourcen-ID " *nidprompt*" für den Hilfe Kontext verwendet. Weitere Informationen zum Definieren von Hilfe Kontexten finden Sie in der [technischen Notiz 28](../../mfc/tn028-context-sensitive-help-support.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCWindowing#133](../../mfc/reference/codesnippet/cpp/cstring-formatting-and-message-box-display_4.cpp)]

## <a name="see-also"></a>Weitere Informationen

[Makros und Globals](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CStringT-Klasse](../../atl-mfc-shared/reference/cstringt-class.md)
