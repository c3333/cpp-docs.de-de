---
title: 'TN024: MFC-definierte Meldungen und Ressourcen'
ms.date: 11/04/2016
helpviewer_keywords:
- resources [MFC]
- Windows messages [MFC], MFC-defined
- messages [MFC], MFC
- TN024
ms.assetid: c65353ce-8096-454b-ad22-1a7a1dd9a788
ms.openlocfilehash: 24bcacd46b839babe9c9c89facb1cc56d18c0ee5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370354"
---
# <a name="tn024-mfc-defined-messages-and-resources"></a>TN024: MFC-definierte Meldungen und Ressourcen

> [!NOTE]
> Der folgende technische Hinweis wurde seit dem ersten Erscheinen in der Onlinedokumentation nicht aktualisiert. Daher können einige Verfahren und Themen veraltet oder falsch sein. Um aktuelle Informationen zu erhalten, wird empfohlen, das gewünschte Thema im Index der Onlinedokumentation zu suchen.

Dieser Hinweis beschreibt die internen Windows-Nachrichten und Ressourcenformate, die von MFC verwendet werden. Diese Informationen erklären die Implementierung des Frameworks und unterstützen Sie beim Debuggen Ihrer Anwendung. Für Abenteuerlustige, auch wenn alle diese Informationen offiziell nicht unterstützt werden, können Sie einige dieser Informationen für erweiterte Implementierungen verwenden.

Dieser Hinweis enthält Details zur privaten MFC-Implementierung. alle Inhalte können sich in Zukunft ändern. Private Windows-Nachrichten mit MFC haben nur im Bereich einer Anwendung Bedeutung, ändern sich jedoch in Zukunft, um systemweite Nachrichten zu enthalten.

Der Bereich der privaten MFC-Nachrichten und Ressourcentypen befindet sich im reservierten "System"-Bereich, der von Microsoft Windows reserviert wird. Derzeit werden nicht alle Zahlen in den Bereichen verwendet und in Zukunft können neue Zahlen im Bereich verwendet werden. Die aktuell verwendeten Nummern können geändert werden.

MFC private Windows-Nachrichten sind im Bereich 0x360->0x37F.

MFC private Ressourcentypen liegen im Bereich 0xF0->0xFF.

**MFC Private Windows-Nachrichten**

Diese Windows-Meldungen werden anstelle virtueller C++-Funktionen verwendet, bei denen eine relativ lose Kopplung zwischen Fensterobjekten erforderlich ist und eine virtuelle C++-Funktion nicht geeignet wäre.

Diese privaten Windows-Nachrichten und zugehörigen Parameterstrukturen werden im privaten MFC-Header 'AFXPRIV deklariert. H'. Seien Sie gewarnt, dass jeder Code, der diesen Header enthält, möglicherweise auf nicht dokumentiertem Verhalten angewiesen ist und wahrscheinlich in zukünftigen Versionen von MFC unterbricht.

Im seltenen Fall, dass sie eine dieser Nachrichten verarbeiten müssen, sollten Sie das ON_MESSAGE Message Map-Makro verwenden und die Nachricht im generischen LRESULT/WPARAM/LPARAM-Format behandeln.

**WM_QUERYAFXWNDPROC**

Diese Nachricht wird an ein Fenster gesendet, das erstellt wird. Dies wird sehr früh im Erstellungsprozess gesendet, um zu bestimmen, ob die WndProc **AfxWndProc ist. AfxWndProc** gibt 1 zurück.

|||
|-|-|
|wParam|Nicht verwendet|
|lParam|Nicht verwendet|
|gibt Folgendes zurück:|1, wenn von **AfxWndProc** verarbeitet|

**WM_SIZEPARENT**

Diese Nachricht wird von einem Framefenster an die`CFrameWnd::OnSize` unmittelbaren `CFrameWnd::RecalcLayout` untergeordneten Elemente gesendet, während die Größe (Anrufe, die aufrufen `CWnd::RepositionBars`) wird, um die Steuerleisten an der Seite des Frames neu zu positionieren. Die AFX_SIZEPARENTPARAMS-Struktur enthält das aktuelle verfügbare Clientrechteck des übergeordneten Elements und `DeferWindowPos` eine HDWP (die möglicherweise NULL ist), mit der sie aufrufen können, um die Neulackierung zu minimieren.

|||
|-|-|
|wParam|Nicht verwendet|
|lParam|Anschrift einer AFX_SIZEPARENTPARAMS Struktur|
|gibt Folgendes zurück:|Nicht verwendet (0)|

Das Ignorieren der Meldung zeigt an, dass das Fenster nicht am Layout teilnimmt.

**WM_SETMESSAGESTRING**

Diese Nachricht wird an ein Rahmenfenster gesendet, um sie aufzufordern, die Meldungszeile in der Statusleiste zu aktualisieren. Es können entweder eine Zeichenfolgen-ID oder ein LPCSTR angegeben werden (aber nicht beides).

|||
|-|-|
|wParam|String-ID (oder Null)|
|lParam|LPCSTR für die Zeichenfolge (oder NULL)|
|gibt Folgendes zurück:|Nicht verwendet (0)|

**WM_IDLEUPDATECMDUI**

Diese Nachricht wird im Leerlauf gesendet, um die Aktualisierung der Update-Befehls-UI-Handler im Leerlauf zu implementieren. Wenn das Fenster (in der Regel eine Kontrollleiste) die Nachricht verarbeitet, erstellt es ein `CCmdUI` Objekt (oder ein Objekt einer abgeleiteten Klasse) und ruft jedes der "Elemente" im Fenster auf. `CCmdUI::DoUpdate` Dadurch wird wiederum nach einem ON_UPDATE_COMMAND_UI Handler für die Objekte in der Befehlshandlerkette gesucht.

|||
|-|-|
|wParam|BOOL bDisableIfNoHandler|
|lParam|Nicht verwendet (0)|
|gibt Folgendes zurück:|Nicht verwendet (0)|

*bDisableIfNoHandler* ist ungleich Null, um das UI-Objekt zu deaktivieren, wenn weder ein ON_UPDATE_COMMAND_UI noch ein ON_COMMAND-Handler vorhanden ist.

**WM_EXITHELPMODE**

Diese Nachricht wird `CFrameWnd` in einen zum Beenden des kontextsensitiven Hilfemodus gesendet. Der Empfang dieser Nachricht beendet die `CFrameWnd::OnContextHelp`modale Schleife, die von gestartet wurde.

|||
|-|-|
|wParam|Nicht verwendet (0)|
|lParam|Nicht verwendet (0)|
|gibt Folgendes zurück:|Nicht verwendet|

**WM_INITIALUPDATE**

Diese Nachricht wird von der Dokumentvorlage an alle abhängigen Elemente eines Rahmenfensters gesendet, wenn sie ihre erste Aktualisierung sicher durchführen können. Es wird einem `CView::OnInitialUpdate` Aufruf zugeordnet, kann `CWnd`aber in anderen -abgeleiteten Klassen für andere One-Shot-Aktualisierungen verwendet werden.

|||
|-|-|
|wParam|Nicht verwendet (0)|
|lParam|Nicht verwendet (0)|
|gibt Folgendes zurück:|Nicht verwendet (0)|

**WM_RECALCPARENT**

Diese Nachricht wird von einer Ansicht an `GetParent`das übergeordnete Fenster gesendet (über erhalten), `RecalcLayout`um eine Layoutneuberechnung zu erzwingen (normalerweise ruft das übergeordnete Element auf). Dies wird in OLE-Serveranwendungen verwendet, bei denen der Frame mit zunehmender Gesamtgröße der Ansicht vergrößert werden muss.

Wenn das übergeordnete Fenster diese Meldung verarbeitet, sollte es TRUE zurückgeben und den in lParam übergebenen RECT mit der neuen Größe des Clientbereichs ausfüllen. Dies wird `CScrollView` verwendet, um Bildlaufleisten richtig zu handhaben (platzieren Sie dann auf der Außenseite des Fensters, wenn sie hinzugefügt werden), wenn ein Serverobjekt an Ort und Stelle aktiviert ist.

|||
|-|-|
|wParam|Nicht verwendet (0)|
|lParam|LPRECT rectClient, kann NULL sein|
|gibt Folgendes zurück:|TRUE, wenn ein neues Clientrechteck zurückgegeben wird, FALSE andernfalls|

**WM_SIZECHILD**

Diese Nachricht wird `COleResizeBar` von an das `GetOwner`Besitzerfenster (über ) gesendet, wenn der Benutzer die Größe der Größe mit den Ziehpunkts für die Größenänderung ändert. `COleIPFrameWnd`reagiert auf diese Meldung, indem versucht wird, das Rahmenfenster neu zu positionieren, wie es der Benutzer angefordert hat.

Das neue Rechteck, das in Clientkoordinaten relativ zum Rahmenfenster angegeben ist, das die Größenleiste enthält, wird von lParam angezeigt.

|||
|-|-|
|wParam|Nicht verwendet (0)|
|lParam|LPRECT rectNeu|
|gibt Folgendes zurück:|Nicht verwendet (0)|

**WM_DISABLEMODAL**

Diese Nachricht wird an alle Popupfenster gesendet, die einem Framefenster gehören, das deaktiviert wird. Das Rahmenfenster verwendet das Ergebnis, um zu bestimmen, ob das Popupfenster deaktiviert werden soll.

Sie können dies verwenden, um eine spezielle Verarbeitung in Ihrem Popupfenster durchzuführen, wenn der Frame in einen modalen Zustand wechselt, oder um zu verhindern, dass bestimmte Popupfenster deaktiviert werden. Tooltips verwenden diese Meldung, um sich selbst zu zerstören, wenn das Rahmenfenster z. B. in einen modalen Zustand wechselt.

|||
|-|-|
|wParam|Nicht verwendet (0)|
|lParam|Nicht verwendet (0)|
|gibt Folgendes zurück:|Ungleich Null, um das Fenster **NICHT** zu deaktivieren, 0 gibt an, dass das Fenster deaktiviert wird|

**WM_FLOATSTATUS**

Diese Meldung wird an alle Popupfenster gesendet, die einem Rahmenfenster gehören, wenn der Rahmen entweder durch ein anderes Rahmenfenster der obersten Ebene aktiviert oder deaktiviert wird. Dies wird von der `CMiniFrameWnd`Implementierung von MFS_SYNCACTIVE in verwendet, um die Aktivierung dieser Popupfenster mit der Aktivierung des Rahmenfensters der obersten Ebene synchron zu halten.

|||
|-|-|
|wParam|Weist einen der folgenden Werte auf:<br /><br /> FS_SHOW<br /><br /> FS_HIDE<br /><br /> FS_ACTIVATE<br /><br /> FS_DEACTIVATE<br /><br /> FS_ENABLEFS_DISABLE<br /><br /> FS_SYNCACTIVE|
|lParam|Nicht verwendet (0)|

Der Rückgabewert sollte ungleich Null sein, wenn FS_SYNCACTIVE festgelegt ist und das Fenster seine Aktivierung mit dem übergeordneten Frame synchronisiert. `CMiniFrameWnd`gibt einen Wert ungleich Null zurück, wenn der Stil auf MFS_SYNCACTIVE festgelegt ist.

Weitere Informationen finden Sie `CMiniFrameWnd`in der Implementierung von .

## <a name="wm_activatetoplevel"></a>WM_ACTIVATETOPLEVEL

Diese Nachricht wird an ein Fenster der obersten Ebene gesendet, wenn ein Fenster in der Gruppe der obersten Ebene entweder aktiviert oder deaktiviert wird. Ein Fenster ist Teil einer Gruppe der obersten Ebene, wenn es sich um ein Fenster der obersten Ebene handelt (kein übergeordnetes fenster oder Besitzer), oder es ist im Besitz eines solchen Fensters. Diese Meldung ähnelt in der Verwendung WM_ACTIVATEAPP, funktioniert jedoch in Situationen, in denen Fenster, die zu verschiedenen Prozessen gehören, in einer einzelnen Fensterhierarchie gemischt werden (häufig in OLE-Anwendungen).

## <a name="wm_commandhelp-wm_helphittest-wm_exithelpmode"></a>WM_COMMANDHELP, WM_HELPHITTEST WM_EXITHELPMODE

Diese Meldungen werden bei der Implementierung der kontextsensitiven Hilfe verwendet. Weitere Informationen finden Sie im [Technischen Hinweis 28.](../mfc/tn028-context-sensitive-help-support.md)

## <a name="mfc-private-resource-formats"></a>MFC Private Ressourcenformate

Derzeit definiert MFC zwei private Ressourcenformate: RT_TOOLBAR und RT_DLGINIT.

## <a name="rt_toolbar-resource-format"></a>RT_TOOLBAR-Ressourcenformat

Die von AppWizard bereitgestellte Standardsymbolleiste basiert auf einer RT_TOOLBAR benutzerdefinierte Ressource, die in MFC 4.0 eingeführt wurde. Sie können diese Ressource mit dem Toolbar-Editor bearbeiten.

## <a name="rt_dlginit-resource-format"></a>RT_DLGINIT-Ressourcenformat

Ein privates MFC-Ressourcenformat wird verwendet, um zusätzliche Dialoginitialisierungsinformationen zu speichern. Dazu gehören die anfänglichen Zeichenfolgen, die in einem Kombinationsfeld gespeichert sind. Das Format dieser Ressource ist nicht für die manuelle Bearbeitung ausgelegt, sondern wird von Visual C++ verarbeitet.

Visual C++ und diese RT_DLGINIT Ressource sind nicht erforderlich, um die zugehörigen Features von MFC zu verwenden, da es eine API-Alternative zur Verwendung der Informationen in der Ressource gibt. Die Verwendung von Visual C++ erleichtert das Schreiben, Verwalten und Übersetzen Ihrer Anwendung auf lange Sicht erheblich.

Die Grundstruktur einer RT_DLGINIT Ressource ist wie folgt:

```
+---------------+    \
| Control ID    |   UINT             |
+---------------+    |
| Message #     |   UINT             |
+---------------+    |
|length of data |   DWORD            |
+---------------+    |   Repeated
|   Data        |   Variable Length  |   for each control
|   ...         |   and Format       |   and message
+---------------+    /
|     0         |   BYTE
+---------------+
```

Ein wiederholter Abschnitt enthält die Steuerelement-ID zum Senden der Nachricht, die zu sendende Nachricht (eine normale Windows-Nachricht) und eine variable Datenlänge. Die Windows-Nachricht wird in einem Formular gesendet:

```
SendDlgItemMessage(<Control ID>, <Message #>, 0, &<Data>);
```

Dies ist ein sehr allgemeines Format, das alle Windows-Nachrichten und Dateninhalte zulässt. Der Visual C++-Ressourceneditor und MFC unterstützen nur eine begrenzte Teilmenge von Windows-Nachrichten: CB_ADDSTRING für die anfänglichen Listenauswahlen für Kombinationsfelder (die Daten sind eine Textzeichenfolge).

## <a name="see-also"></a>Siehe auch

[Technische Hinweise – nach Nummern geordnet](../mfc/technical-notes-by-number.md)<br/>
[Technische Hinweise – nach Kategorien geordnet](../mfc/technical-notes-by-category.md)
