---
title: 'TN024: MFC-definierte Meldungen und Ressourcen'
ms.date: 11/04/2016
helpviewer_keywords:
- resources [MFC]
- Windows messages [MFC], MFC-defined
- messages [MFC], MFC
- TN024
ms.assetid: c65353ce-8096-454b-ad22-1a7a1dd9a788
ms.openlocfilehash: 9ad6827e4a46bb9f2ff3b02986a01737772e0858
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88839217"
---
# <a name="tn024-mfc-defined-messages-and-resources"></a>TN024: MFC-definierte Meldungen und Ressourcen

> [!NOTE]
> Der folgende technische Hinweis wurde seit dem ersten Erscheinen in der Onlinedokumentation nicht aktualisiert. Daher können einige Verfahren und Themen veraltet oder falsch sein. Um aktuelle Informationen zu erhalten, wird empfohlen, das gewünschte Thema im Index der Onlinedokumentation zu suchen.

In diesem Hinweis werden die internen Windows-Meldungen und Ressourcen Formate beschrieben, die von MFC verwendet werden. Diese Informationen erläutern die Implementierung des Frameworks und unterstützen Sie beim Debuggen Ihrer Anwendung. Für den abenteuerlichen, auch wenn alle diese Informationen offiziell nicht unterstützt werden, können Sie einige dieser Informationen für erweiterte Implementierungen verwenden.

Dieser Hinweis enthält Details zur privaten MFC-Implementierung. Alle Inhalte können in Zukunft geändert werden. Private MFC-Windows-Meldungen haben nur im Bereich einer Anwendung Bedeutung, werden jedoch in Zukunft geändert, sodass Sie systemweite Nachrichten enthalten.

Der Bereich der privaten MFC-Windows-Meldungen und-Ressourcentypen befindet sich im reservierten "System"-Bereich, der von Microsoft Windows reserviert wird. Derzeit werden nicht alle Zahlen in den Bereichen verwendet, und in der Zukunft können neue Zahlen im Bereich verwendet werden. Die aktuell verwendeten Zahlen können geändert werden.

Private MFC-Windows-Meldungen liegen im Bereich 0x360->0x37f.

Private MFC-Ressourcentypen liegen im Bereich 0xF0->0xFF.

**Private MFC-Windows-Meldungen**

Diese Windows-Meldungen werden anstelle von virtuellen C++-Funktionen verwendet, bei denen eine relativ lose Kopplung zwischen Fenster Objekten erforderlich ist und die virtuelle C++-Funktion nicht geeignet wäre.

Diese privaten Windows-Meldungen und zugeordneten Parameter Strukturen werden im privaten MFC-Header ' afxpriv ' deklariert. H '. Beachten Sie, dass jeder Code, der diesen Header enthält, sich auf nicht dokumentiertes Verhalten verlassen kann und wahrscheinlich in zukünftigen Versionen von MFC unterbrechen wird.

In dem seltenen Fall, dass eine dieser Nachrichten verarbeiten muss, sollten Sie das ON_MESSAGE Message Map-Makro verwenden und die Nachricht im generischen LRESULT/wParam/lParam-Format verarbeiten.

**WM_QUERYAFXWNDPROC**

Diese Meldung wird an ein Fenster gesendet, das erstellt wird. Dies wird sehr früh im Erstellungs Prozess als Methode zum ermitteln, ob der WndProc **afxwndproc ist, gesendet. Afxwndproc** gibt 1 zurück.

| Parameter und Rückgabewert | Beschreibung |
|-|-|
|wParam|Nicht verwendet|
|lParam|Nicht verwendet|
|gibt Folgendes zurück:|1, wenn von **afxwndproc** verarbeitet|

**WM_SIZEPARENT**

Diese Meldung wird von einem Rahmen Fenster an die unmittelbar untergeordneten Elemente gesendet, während die Größe geändert wird ( `CFrameWnd::OnSize` Aufrufe `CFrameWnd::RecalcLayout` , die aufruft `CWnd::RepositionBars` ), um die Steuer leisten auf der Seite des Frames neu zu positionieren. Die AFX_SIZEPARENTPARAMS-Struktur enthält das aktuelle verfügbare Client Rechteck des übergeordneten Elements und eine hdwp (die möglicherweise NULL ist), mit der aufgerufen wird, `DeferWindowPos` um das Neuzeichnen zu minimieren.

| Parameter und Rückgabewert | Beschreibung |
|-|-|
|wParam|Nicht verwendet|
|lParam|Adresse einer AFX_SIZEPARENTPARAMS Struktur|
|gibt Folgendes zurück:|Nicht verwendet (0)|

Das Ignorieren der Meldung weist darauf hin, dass das Fenster nicht an dem Layout teilnimmt.

**WM_SETMESSAGESTRING**

Diese Meldung wird an ein Rahmen Fenster gesendet, um Sie aufzufordern, die Meldungs Zeile in der Statusleiste zu aktualisieren. Es kann entweder eine Zeichen folgen-ID oder eine LPCSTR-Angabe angegeben werden (aber nicht beides).

| Parameter und Rückgabewert | Beschreibung |
|-|-|
|wParam|Zeichen folgen-ID (oder NULL)|
|lParam|LPCSTR für die Zeichenfolge (oder NULL)|
|gibt Folgendes zurück:|Nicht verwendet (0)|

**WM_IDLEUPDATECMDUI**

Diese Meldung wird im Leerlauf gesendet, um die Leerlaufzeit Aktualisierung von Benutzeroberflächen Handlern für den Update-Befehl zu implementieren. Wenn das Fenster (in der Regel eine Steuerleiste) die Nachricht verarbeitet, erstellt es ein `CCmdUI` -Objekt (oder ein Objekt einer abgeleiteten Klasse) und ruft `CCmdUI::DoUpdate` für jedes der Elemente im-Fenster auf. Dadurch wird die Überprüfung auf einen ON_UPDATE_COMMAND_UI Handler für die Objekte in der Befehls Handler-Kette durchsucht.

| Parameter und Rückgabewert | Beschreibung |
|-|-|
|wParam|Bool bdisableifnohandler|
|lParam|Nicht verwendet (0)|
|gibt Folgendes zurück:|Nicht verwendet (0)|

*bdisableifnohandler* ist nicht NULL, um das UI-Objekt zu deaktivieren, wenn weder eine ON_UPDATE_COMMAND_UI noch ein ON_COMMAND Handler vorhanden ist.

**WM_EXITHELPMODE**

Diese Meldung wird an einen gesendet `CFrameWnd` , um den kontextbezogenen Hilfe Modus zu beenden. Der Empfang dieser Nachricht beendet die von gestartete modale Schleife `CFrameWnd::OnContextHelp` .

| Parameter und Rückgabewert | Beschreibung |
|-|-|
|wParam|Nicht verwendet (0)|
|lParam|Nicht verwendet (0)|
|gibt Folgendes zurück:|Nicht verwendet|

**WM_INITIALUPDATE**

Diese Meldung wird von der Dokument Vorlage an alle untergeordneten Elemente eines Rahmen Fensters gesendet, wenn Sie sicher sind, dass Sie das erste Update durchführen können. Sie wird einem-Rückruf zugeordnet, `CView::OnInitialUpdate` kann aber in anderen `CWnd` von abgeleiteten Klassen für andere One-Shot-Aktualisierungen verwendet werden.

| Parameter und Rückgabewert | Beschreibung |
|-|-|
|wParam|Nicht verwendet (0)|
|lParam|Nicht verwendet (0)|
|gibt Folgendes zurück:|Nicht verwendet (0)|

**WM_RECALCPARENT**

Diese Meldung wird von einer Ansicht an das übergeordnete Fenster gesendet (über abgerufen `GetParent` ), um die Neuberechnung eines Layouts zu erzwingen (in der Regel wird das übergeordnete Element aufruft `RecalcLayout` ). Dies wird in OLE-Server Anwendungen verwendet, bei denen es erforderlich ist, dass sich der Frame vergrößert, wenn die Gesamtgröße der Ansicht zunimmt.

Wenn das übergeordnete Fenster diese Nachricht verarbeitet, sollte Sie "true" zurückgeben und das in lParam übergebenen Rect mit der neuen Größe des Client Bereichs ausfüllen. Diese wird in verwendet `CScrollView` , um Scrollleisten ordnungsgemäß zu verarbeiten (platzieren Sie Sie dann beim Hinzufügen an der Außenseite des Fensters), wenn ein Server Objekt direkt aktiviert ist.

| Parameter und Rückgabewert | Beschreibung |
|-|-|
|wParam|Nicht verwendet (0)|
|lParam|Lprect rectclient, kann NULL sein.|
|gibt Folgendes zurück:|TRUE, wenn ein neues Client Rechteck zurückgegeben wurde, andernfalls false.|

**WM_SIZECHILD**

Diese Meldung wird von `COleResizeBar` an das Besitzer Fenster (via) gesendet, `GetOwner` Wenn der Benutzer die Größe der Leiste der Größenänderung mit den Handles zur Größenänderung ändert. `COleIPFrameWnd` reagiert auf diese Meldung, indem versucht wird, das Rahmen Fenster neu zu positionieren, wenn der Benutzer angefordert hat.

Das neue Rechteck, das in Client Koordinaten relativ zum Rahmen Fenster, das die Größenänderung enthält, angegeben wird, wird von lParam gezeigt.

| Parameter und Rückgabewert | Beschreibung |
|-|-|
|wParam|Nicht verwendet (0)|
|lParam|Lprect rectnew|
|gibt Folgendes zurück:|Nicht verwendet (0)|

**WM_DISABLEMODAL**

Diese Nachricht wird an alle Popup Fenster gesendet, die sich im Besitz eines Rahmen Fensters befinden, das deaktiviert wird. Das Rahmen Fenster verwendet das Ergebnis, um zu bestimmen, ob das Popup Fenster deaktiviert werden soll.

Mit dieser Option können Sie im Popup Fenster eine besondere Verarbeitung durchführen, wenn der Frame in einen modalen Zustand versetzt wird oder wenn bestimmte Popup Fenster deaktiviert werden. Quick Infos verwenden diese Meldung, um sich selbst zu zerstören, wenn das Rahmen Fenster z. b. in einen modalen Zustand übergeht.

| Parameter und Rückgabewert | Beschreibung |
|-|-|
|wParam|Nicht verwendet (0)|
|lParam|Nicht verwendet (0)|
|gibt Folgendes zurück:|Ungleich 0 (null), um das Fenster **nicht** zu deaktivieren, 0 gibt an, dass das Fenster deaktiviert wird.|

**WM_FLOATSTATUS**

Diese Nachricht wird an alle Popup Fenster gesendet, die sich im Besitz eines Rahmen Fensters befinden, wenn der Rahmen entweder durch ein anderes Rahmen Fenster der obersten Ebene aktiviert oder deaktiviert wird. Dies wird von der Implementierung von MFS_SYNCACTIVE in verwendet `CMiniFrameWnd` , um die Aktivierung dieser Popup Fenster mit der Aktivierung des Frame Fensters der obersten Ebene synchron zu halten.

| Parameter | Beschreibung |
|-|-|
|wParam|Weist einen der folgenden Werte auf:<br /><br /> FS_SHOW<br /><br /> FS_HIDE<br /><br /> FS_ACTIVATE<br /><br /> FS_DEACTIVATE<br /><br /> FS_ENABLEFS_DISABLE<br /><br /> FS_SYNCACTIVE|
|lParam|Nicht verwendet (0)|

Der Rückgabewert darf nicht NULL sein, wenn FS_SYNCACTIVE festgelegt ist und das Fenster seine Aktivierung mit dem übergeordneten Frame synchronisiert. `CMiniFrameWnd` Gibt einen Wert ungleich 0 (null) zurück, wenn der Stil auf MFS_SYNCACTIVE festgelegt ist

Weitere Informationen finden Sie in der Implementierung von `CMiniFrameWnd` .

## <a name="wm_activatetoplevel"></a>WM_ACTIVATETOPLEVEL

Diese Meldung wird an ein Fenster der obersten Ebene gesendet, wenn ein Fenster in der Gruppe "Gruppe der obersten Ebene" aktiviert oder deaktiviert ist. Ein Fenster ist Teil einer Gruppe der obersten Ebene, wenn es sich um ein Fenster der obersten Ebene (kein übergeordnetes Element oder Besitzer) handelt, oder das Fenster im Besitz eines solchen Fensters ist. Diese Meldung ähnelt der Verwendung von WM_ACTIVATEAPP, funktioniert jedoch in Situationen, in denen Windows, die zu verschiedenen Prozessen gehören, in einer einzigen Fenster Hierarchie gemischt werden (häufig in OLE-Anwendungen).

## <a name="wm_commandhelp-wm_helphittest-wm_exithelpmode"></a>WM_COMMANDHELP, WM_HELPHITTEST WM_EXITHELPMODE

Diese Nachrichten werden in der Implementierung der kontextbezogenen Hilfe verwendet. Weitere Informationen finden Sie in der [technischen Notiz 28](../mfc/tn028-context-sensitive-help-support.md) .

## <a name="mfc-private-resource-formats"></a>Private MFC-Ressourcen Formate

Derzeit definiert MFC zwei private Ressourcen Formate: RT_TOOLBAR und RT_DLGINIT.

## <a name="rt_toolbar-resource-format"></a>RT_TOOLBAR-Ressourcen Format

Die von AppWizard angegebene Standard Symbolleiste basiert auf einer RT_TOOLBAR benutzerdefinierten Ressource, die in MFC 4,0 eingeführt wurde. Sie können diese Ressource mit dem Symbolleisten-Editor bearbeiten.

## <a name="rt_dlginit-resource-format"></a>RT_DLGINIT-Ressourcen Format

Ein privates MFC-Ressourcen Format wird verwendet, um zusätzliche Dialogfeld Initialisierungs Informationen zu speichern. Dies schließt die anfänglichen Zeichen folgen ein, die in einem Kombinations Feld gespeichert sind. Das Format dieser Ressource ist nicht so konzipiert, dass Sie manuell bearbeitet wird, sondern von Visual C++ verarbeitet wird.

Visual C++ und diese RT_DLGINIT Ressource sind nicht erforderlich, um die zugehörigen Features von MFC zu verwenden, da es eine API-Alternative zur Verwendung der Informationen in der Ressource gibt. Wenn Sie Visual C++ verwenden, ist es viel einfacher, Ihre Anwendung langfristig zu schreiben, zu warten und zu übersetzen.

Die grundlegende Struktur einer RT_DLGINIT Ressource lautet wie folgt:

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

Ein wiederholter Abschnitt enthält die Steuerelement-ID zum Senden der Nachricht, die zu sendende Meldung (eine normale Windows-Meldung) und eine Variable Länge von Daten. Die Windows-Meldung wird in einem Formular gesendet:

```
SendDlgItemMessage(<Control ID>, <Message #>, 0, &<Data>);
```

Dies ist ein allgemeines Format, das alle Windows-Meldungen und Dateninhalte zulässt. Der Ressourcen-Editor für Visual C++ und MFC unterstützen nur eine begrenzte Teilmenge von Windows-Meldungen: CB_ADDSTRING für die ersten Listen Optionen für Kombinations Felder (die Daten sind eine Text Zeichenfolge).

## <a name="see-also"></a>Weitere Informationen

[Technische Hinweise nach Zahl](../mfc/technical-notes-by-number.md)<br/>
[Technische Hinweise nach Kategorie](../mfc/technical-notes-by-category.md)
