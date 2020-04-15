---
title: 'TN028: Bereitstellen kontextbezogener Hilfe'
ms.date: 11/04/2016
f1_keywords:
- vc.help
helpviewer_keywords:
- context-sensitive Help [MFC], MFC applications
- TN028
- resource identifiers, context-sensitive Help
ms.assetid: 884f1c55-fa27-4d4c-984f-30907d477484
ms.openlocfilehash: 502edc837d7886dd60ab5107fb194c1490a76928
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370327"
---
# <a name="tn028-context-sensitive-help-support"></a>TN028: Bereitstellen kontextbezogener Hilfe

In diesem Hinweis werden die Regeln zum Zuweisen von Hilfekontext-IDs und anderen Hilfeproblemen in MFC beschrieben. Für die kontextsensitive Hilfeunterstützung ist der Hilfecompiler erforderlich, der in Visual C++ verfügbar ist.

> [!NOTE]
> Neben der Implementierung kontextsensitiver Hilfe mithilfe von WinHelp unterstützt MFC auch die Verwendung der HTML-Hilfe. Weitere Informationen zu dieser Unterstützung und Programmierung mit HTML-Hilfe finden Sie in der [HTML-Hilfe: Kontextsensitive Hilfe für Ihre Programme](../mfc/html-help-context-sensitive-help-for-your-programs.md).

## <a name="types-of-help-supported"></a>Unterstützte Arten der Hilfe

Es gibt zwei Arten von kontextsensitiven Hilfe, die in Windows-Anwendungen implementiert ist. Die erste, die als "F1-Hilfe" bezeichnet wird, beinhaltet das Starten von WinHelp mit dem entsprechenden Kontext basierend auf dem aktuell aktiven Objekt. Der zweite ist der Modus "Shift+ F1". In diesem Modus ändert sich der Mauszeiger zum Hilfecursor, und der Benutzer klickt weiter auf ein Objekt. An diesem Punkt wird WinHelp gestartet, um Hilfe für das Objekt zu geben, auf das der Benutzer geklickt hat.

Die Microsoft Foundation-Klassen implementieren beide Formen der Hilfe. Darüber hinaus unterstützt das Framework zwei einfache Hilfebefehle, Hilfeindex und Verwenden der Hilfe.

## <a name="help-files"></a>Hilfedateien

Die Microsoft Foundation-Klassen verwenden eine einzelne Hilfedatei. Diese Hilfedatei muss denselben Namen und Pfad wie die Anwendung haben. Wenn die ausführbare Datei z. B. C:'MyApplication'MyHelp.exe' lautet, muss die Hilfedatei C:'MyApplication'MyHelp.hlp' sein. Sie legen den Pfad über die *m_pszHelpFilePath* Membervariable der [CWinApp-Klasse](../mfc/reference/cwinapp-class.md)fest.

## <a name="help-context-ranges"></a>Hilfe Kontextbereiche

Die Standardimplementierung von MFC erfordert, dass ein Programm einige Regeln für die Zuweisung von Hilfekontext-IDs befolgt. Bei diesen Regeln handelt es sich um eine Reihe von IDs, die bestimmten Steuerelementen zugeordnet sind. Sie können diese Regeln überschreiben, indem Sie verschiedene Implementierungen der verschiedenen Hilfe-bezogenen Memberfunktionen bereitstellen.

```
0x00000000 - 0x0000FFFF : user defined
0x00010000 - 0x0001FFFF : commands (menus/command buttons)
0x00010000 + ID_
(note: 0x18000-> 0x1FFFF is the practical range since command IDs are>=0x8000)
0x00020000 - 0x0002FFFF : windows and dialogs
0x00020000 + IDR_
(note: 0x20000-> 0x27FFF is the practical range since IDRs are <= 0x7FFF)
0x00030000 - 0x0003FFFF : error messages (based on error string ID)
0x00030000 + IDP_
0x00040000 - 0x0004FFFF : special purpose (non-client areas)
0x00040000 + HitTest area
0x00050000 - 0x0005FFFF : controls (those that are not commands)
0x00040000 + IDW_
```

## <a name="simple-help-commands"></a>Einfache "Hilfe"-Befehle

Es gibt zwei einfache Hilfebefehle, die von den Microsoft Foundation-Klassen implementiert werden:

- ID_HELP_INDEX, die von [CWinApp implementiert wird::OnHelpIndex](../mfc/reference/cwinapp-class.md#onhelpindex)

- ID_HELP_USING, die von [CWinApp implementiert wird::OnHelpUsing](../mfc/reference/cwinapp-class.md#onhelpusing)

Der erste Befehl zeigt den Hilfeindex für die Anwendung an. Die zweite zeigt die Benutzerhilfe zur Verwendung des WinHelp-Programms.

## <a name="context-sensitive-help-f1-help"></a>Kontextsensitive Hilfe (F1-Hilfe)

Die Taste F1 wird in der Regel in einen Befehl mit der ID ID_HELP von einem Beschleuniger übersetzt, der in die Beschleunigertabelle des Hauptfensters eingefügt wird. Der Befehl ID_HELP kann auch durch eine Schaltfläche mit der ID ID_HELP im Hauptfenster oder Dialogfeld generiert werden.

Unabhängig davon, wie der Befehl ID_HELP generiert wird, wird er als normaler Befehl weitergeleitet, bis er einen Befehlshandler erreicht. Weitere Informationen zur MFC-Befehlsroutingarchitektur finden Sie unter [Technical Note 21](../mfc/tn021-command-and-message-routing.md). Wenn die Anwendung die Hilfe aktiviert hat, wird der Befehl ID_HELP von [CWinApp::OnHelp](../mfc/reference/cwinapp-class.md#onhelp)verarbeitet. Das Anwendungsobjekt empfängt die Hilfenachricht und leitet den Befehl dann entsprechend weiter. Dies ist erforderlich, da das Standardbefehlsrouting nicht ausreicht, um den spezifischsten Kontext zu bestimmen.

`CWinApp::OnHelp`versucht, WinHelp in der folgenden Reihenfolge zu starten:

1. Sucht nach `AfxMessageBox` einem aktiven Anruf mit einer Hilfe-ID. Wenn derzeit ein Meldungsfeld aktiv ist, wird WinHelp mit dem kontextabhängigen Kontext gestartet, der für dieses Meldungsfeld geeignet ist.

1. Sendet eine WM_COMMANDHELP Nachricht an das aktive Fenster. Wenn dieses Fenster nicht durch Starten von WinHelp antwortet, wird dieselbe Nachricht an die Vorfahren dieses Fensters gesendet, bis die Nachricht verarbeitet wird oder das aktuelle Fenster ein Fenster der obersten Ebene ist.

1. Sendet einen ID_DEFAULT_HELP Befehl an das Hauptfenster. Dadurch wird die Standardhilfe aufgerufen. Dieser Befehl wird im `CWinApp::OnHelpIndex`Allgemeinen zugeordnet.

Um die Standard-ID-Basiswerte global zu überschreiben (z. B. 0x10000 für Befehle und 0x20000 für Ressourcen wie Dialogfelder), sollte die Anwendung [CWinApp::WinHelp](../mfc/reference/cwinapp-class.md#winhelp)überschreiben.

Um diese Funktionalität und die Art und Weise, wie ein Hilfekontext bestimmt wird, zu überschreiben, sollten Sie die WM_COMMANDHELP-Nachricht behandeln. Möglicherweise möchten Sie spezifischeres Hilferouting bereitstellen, als das Framework bereitstellt, da es nur so tief geht wie das aktuelle untergeordnete MDI-Fenster. Möglicherweise möchten Sie auch spezifischere Hilfe für ein bestimmtes Fenster oder Dialogfeld bereitstellen, möglicherweise basierend auf dem aktuellen internen Status dieses Objekts oder dem aktiven Steuerelement im Dialogfeld.

## <a name="wm_commandhelp"></a>WM_COMMANDHELP

```

afx_msg LRESULT CWnd::OnCommandHelp(WPARAM wParam, LPARAM lParam)
```

WM_COMMANDHELP ist eine private Windows MFC-Nachricht, die vom aktiven Fenster empfangen wird, wenn Hilfe angefordert wird. Wenn das Fenster diese Nachricht `CWinApp::WinHelp` empfängt, kann es mit einem Kontext aufrufen, der dem internen Status des Fensters entspricht.

*lParam*<br/>
Enthält den aktuell verfügbaren Hilfekontext. *lParam* ist Null, wenn kein Hilfekontext bestimmt wurde. Eine Implementierung `OnCommandHelp` von kann die Kontext-ID in *lParam* verwenden, `CWinApp::WinHelp`um einen anderen Kontext zu bestimmen, oder sie einfach an übergeben.

*wParam*<br/>
Wird nicht verwendet und ist Null.

Wenn `OnCommandHelp` die `CWinApp::WinHelp`Funktion aufruft, sollte sie **TRUE**zurückgeben. Durch das Zurücksenden von **TRUE** wird das Routing dieses Befehls an andere Klassen und andere Fenster angehalten.

## <a name="help-mode-shiftf1-help"></a>Hilfemodus (Shift+F1-Hilfe)

Dies ist die zweite Form der kontextsensitiven Hilfe. Im Allgemeinen wird dieser Modus durch Drücken von SHIFT+F1 oder über das Menü/die Symbolleiste eingegeben. Es wird als Befehl (ID_CONTEXT_HELP) implementiert. Der Nachrichtenfilter-Hook wird nicht verwendet, um diesen Befehl zu übersetzen, während ein modales Dialogfeld oder Menü aktiv`CWinApp::Run`ist, daher steht dieser Befehl dem Benutzer nur zur Verfügung, wenn die Anwendung die Hauptnachrichtenpumpe ( ausführt).

Nach dem Betreten dieses Modus wird der Mauszeiger der Hilfe über alle Bereiche der Anwendung angezeigt, auch wenn die Anwendung normalerweise einen eigenen Cursor für diesen Bereich anzeigen würde (z. B. den Größenrahmen um das Fenster). Der Benutzer kann mit der Maus oder der Tastatur einen Befehl auswählen. Anstatt den Befehl auszuführen, wird Hilfe für diesen Befehl angezeigt. Außerdem kann der Benutzer auf ein sichtbares Objekt auf dem Bildschirm klicken, z. B. auf eine Schaltfläche auf der Symbolleiste, und die Hilfe wird für dieses Objekt angezeigt. Diese Hilfewirdwird von `CWinApp::OnContextHelp`wird bereitgestellt.

Während der Ausführung dieser Schleife sind alle Tastatureingaben inaktiv, mit Ausnahme von Tasten, die auf das Menü zugreifen. Außerdem wird die Befehlsübersetzung weiterhin durchgeführt, `PreTranslateMessage` damit der Benutzer eine Beschleunigertaste drücken und Hilfe zu diesem Befehl erhalten kann.

Wenn bestimmte Übersetzungen oder Aktionen in `PreTranslateMessage` der Funktion stattfinden, die während des SHIFT+F1-Hilfemodus nicht `CWinApp` stattfinden sollten, sollten Sie den *m_bHelpMode* Mitglied überprüfen, bevor Sie diese Vorgänge ausführen. Die `CDialog` Implementierung `PreTranslateMessage` von überprüft `IsDialogMessage`dies vor dem Aufruf, zum Beispiel. Dadurch werden die "Dialognavigationstasten" in moduslosen Dialogen während des SHIFT+F1-Modus deaktiviert. Darüber hinaus `CWinApp::OnIdle` wird während dieser Schleife immer noch aufgerufen.

Wenn der Benutzer einen Befehl aus dem Menü auswählt, wird er als Hilfe zu diesem Befehl behandelt (durch WM_COMMANDHELP, siehe unten). Wenn der Benutzer auf einen sichtbaren Bereich des Anwendungsfensters klickt, wird bestimmt, ob es sich um einen Nicht-Client-Klick oder einen Clientklick handelt. `OnContextHelp`behandelt die Zuordnung von Nicht-Client-Klicks zu Clientklicks automatisch. Wenn es sich um einen Clientklick handelt, sendet er eine WM_HELPHITTEST an das Fenster, auf das geklickt wurde. Wenn dieses Fenster einen Wert ungleich Null zurückgibt, wird dieser Wert als Kontext für die Hilfe verwendet. Wenn das übergeordnete `OnContextHelp` Fenster Null zurückgegeben wird (und wenn dies nicht der Ort ist, wird das übergeordnete Fenster usw. nicht angezeigt). Wenn ein Hilfekontext nicht bestimmt werden kann, wird standardmäßig ein ID_DEFAULT_HELP Befehl an das `CWinApp::OnHelpIndex`Hauptfenster gesendet, der dann (normalerweise) zugeordnet wird.

## <a name="wm_helphittest"></a>WM_HELPHITTEST

```

afx_msg LRESULT CWnd::OnHelpHitTest(
WPARAM, LPARAM lParam)
```

WM_HELPHITTEST ist eine private MFC-Fensternachricht, die vom aktiven Fenster empfangen wird, auf das im UMSCHALT+F1-Hilfemodus geklickt wurde. Wenn das Fenster diese Nachricht **DWORD** empfängt, gibt es eine DWORD-Hilfe-ID zur Verwendung durch WinHelp zurück.

LOWORD(lParam) enthält die X-Achsen-Gerätekoordinate, auf die relativ zum Clientbereich des Fensters mit der Maus geklickt wurde.

HIWORD(lParam) enthält die Y-Achsen-Koordinate.

*wParam*<br/>
wird nicht verwendet und ist Null. Wenn der Rückgabewert ungleich Null ist, wird WinHelp mit diesem Kontext aufgerufen. Wenn der Rückgabewert Null ist, wird das übergeordnete Fenster um Hilfe abgefragt.

In vielen Fällen können Sie Hit-Testing-Code nutzen, den Sie möglicherweise bereits haben. Sehen Sie `CToolBar::OnHelpHitTest` sich die Implementierung von für ein Beispiel für die Behandlung der WM_HELPHITTEST Nachricht `CControlBar`(der Code nutzt den Treffertestcode auf Schaltflächen und QuickInfos in verwendet ).

## <a name="mfc-application-wizard-support-and-makehm"></a>MFC Application Wizard Support und MAKEHM

Der MFC-Anwendungs-Assistent erstellt die erforderlichen Dateien zum Erstellen einer Hilfedatei (.cnt- und .hpj-Dateien). Es enthält auch eine Reihe von vorgefertigten .rtf-Dateien, die vom Microsoft-Hilfe-Compiler akzeptiert werden. Viele der Themen sind vollständig, aber einige müssen möglicherweise für Ihre spezifische Anwendung geändert werden.

Die automatische Erstellung einer "Help Mapping"-Datei wird von einem Dienstprogramm namens MAKEHM unterstützt. Das MAKEHM-Dienstprogramm kann die RESOURCE einer Anwendung übersetzen. H-Datei in eine Hilfezuordnungsdatei. Beispiel:

```
#define IDD_MY_DIALOG   2000
#define ID_MY_COMMAND   150
```

wird übersetzt in:

```
HIDD_MY_DIALOG    0x207d0
HID_MY_COMMAND    0x10096
```

Dieses Format ist mit der Funktion des Hilfe-Compilers kompatibel, die Kontext-IDs (die Zahlen auf der rechten Seite) mit Themennamen (den Symbolen auf der linken Seite) zuordnet.

Der Quellcode für MAKEHM ist im MFC Programming Utilities-Beispiel [MAKEHM](../overview/visual-cpp-samples.md)verfügbar.

## <a name="adding-help-support-after-running-the-mfc-application-wizard"></a>Hinzufügen von Hilfeunterstützung nach dem Ausführen des MFC-Anwendungs-Assistenten

Die beste Möglichkeit, Ihrer Anwendung Hilfe hinzuzufügen, besteht darin, die Option "Kontextsensitive Hilfe" auf der Seite Erweiterte Funktionen des MFC-Anwendungs-Assistenten zu aktivieren, bevor Sie Ihre Anwendung erstellen. Auf diese Weise fügt der MFC-Anwendungs-Assistent `CWinApp`automatisch die erforderlichen Nachrichtenzuordnungseinträge zu Ihrer -abgeleiteten Klasse hinzu, um die Hilfe zu unterstützen.

## <a name="help-on-message-boxes"></a>Hilfe zu Nachrichtenfeldern

Hilfe zu Message Boxes (manchmal auch `AfxMessageBox` als Warnungen bezeichnet) `MessageBox` wird durch die Funktion, einen Wrapper für die Windows-API, unterstützt.

Es gibt zwei `AfxMessageBox`Versionen von , eine für die Verwendung mit einer`LPCSTR`Zeichenfolgen-ID und eine andere für die Verwendung mit einem Zeiger auf String ( ):

```
int AFXAPI AfxMessageBox(LPCSTR lpszText,
    UINT nType,
    UINT nIDHelp);

int AFXAPI AfxMessageBox(UINT nIDPrompt,
    UINT nType,
    UINT nIDHelp);
```

In beiden Fällen gibt es eine optionale Hilfe-ID.

Im ersten Fall ist die Standardeinstellung für nIDHelp 0, was keine Hilfe für dieses Meldungsfeld angibt. Wenn der Benutzer F1 drückt, während ein Meldungsfeld aktiv ist, erhält der Benutzer keine Hilfe (auch wenn die Anwendung die Hilfe unterstützt). Wenn dies nicht wünschenswert ist, sollte eine Hilfe-ID für nIDHelp bereitgestellt werden.

Im zweiten Fall ist der Standardwert für nIDHelp -1, was darauf hinweist, dass die Hilfe-ID mit nIDPrompt identisch ist. Die Hilfe funktioniert nur, wenn die Anwendung hilfeaktiviert ist. Sie sollten 0 für nIDHelp angeben, wenn Sie möchten, dass das Meldungsfeld keine Hilfeunterstützung bietet. Wenn Sie möchten, dass die Nachricht Hilfe aktiviert wird, aber eine andere Hilfe-ID als nIDPrompt wünschen, geben Sie einfach einen positiven Wert für nIDHelp an, der sich von dem von nIDPrompt unterscheidet.

## <a name="see-also"></a>Siehe auch

[Technische Hinweise – nach Nummern geordnet](../mfc/technical-notes-by-number.md)<br/>
[Technische Hinweise – nach Kategorien geordnet](../mfc/technical-notes-by-category.md)
