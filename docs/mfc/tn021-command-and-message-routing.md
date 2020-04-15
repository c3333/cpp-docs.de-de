---
title: 'TN021: Befehls- und Meldungsrouting'
ms.date: 06/28/2018
f1_keywords:
- vc.routing
helpviewer_keywords:
- TN021
- command routing [MFC], technical note TN021
- Windows messages [MFC], routing
ms.assetid: b5952c8b-123e-406c-a36d-a6ac7c6df307
ms.openlocfilehash: bdd405bda5c0af9e04a50eee4ef5738f3a53259e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370409"
---
# <a name="tn021-command-and-message-routing"></a>TN021: Befehls- und Meldungsrouting

> [!NOTE]
> Der folgende technische Hinweis wurde seit dem ersten Erscheinen in der Onlinedokumentation nicht aktualisiert. Daher können einige Verfahren und Themen veraltet oder falsch sein. Um aktuelle Informationen zu erhalten, wird empfohlen, das gewünschte Thema im Index der Onlinedokumentation zu suchen.

Dieser Hinweis beschreibt die Befehlsrouting- und Dispatcharchitektur sowie erweiterte Themen im allgemeinen Fensternachrichtenrouting.

Allgemeine Informationen zu den hier beschriebenen Architekturen, insbesondere die Unterscheidung zwischen Windows-Meldungen, Steuerbenachrichtigungen und Befehlen, finden Sie unter Visual C++. In diesem Hinweis wird davon ausgegangen, dass Sie mit den in der gedruckten Dokumentation beschriebenen Problemen sehr vertraut sind und nur sehr fortgeschrittene Themen behandeln.

## <a name="command-routing-and-dispatch-mfc-10-functionality-evolves-to-mfc-20-architecture"></a>Befehlsrouting und Dispatch MFC 1.0-Funktionalität wird zur MFC 2.0-Architektur weiterentwickelt

Windows verfügt über die WM_COMMAND Nachricht, die überladen ist, um Benachrichtigungen über Menübefehle, Beschleunigerschlüssel und Dialogsteuerungsbenachrichtigungen bereitzustellen.

MFC 1.0 baute darauf ein wenig auf, indem einem Befehlshandler (z. B. "OnFileNew") in einer `CWnd` abgeleiteten Klasse erlaubt wurde, als Reaktion auf eine bestimmte WM_COMMAND aufgerufen zu werden. Dies wird mit einer Datenstruktur, der Meldungszuordnung, zusammengeklebt und führt zu einem sehr platzsparenden Befehlsmechanismus.

MFC 1.0 bot auch zusätzliche Funktionen zum Trennen von Steuerbenachrichtigungen von Befehlsmeldungen. Befehle werden durch eine 16-Bit-ID dargestellt, die manchmal als Befehls-ID bezeichnet wird. Befehle beginnen normalerweise `CFrameWnd` von einem (d. h. einer Menüauswahl oder einem übersetzten Beschleuniger) und werden an eine Vielzahl anderer Fenster weitergeleitet.

MFC 1.0 verwendete Befehlsrouting in begrenztem Sinne für die Implementierung von Multiple Document Interface (MDI). (Ein MDI-Rahmenfenster delegiert Befehle an das aktive MDI-Untergeordnete Fenster.)

Diese Funktionalität wurde in MFC 2.0 verallgemeinert und erweitert, damit Befehle von einer größeren Anzahl von Objekten (nicht nur Fensterobjekten) verarbeitet werden können. Es bietet eine formellere und erweiterbare Architektur für das Routing von Nachrichten und verwendet das Befehlszielrouting nicht nur für die Behandlung von Befehlen, sondern auch für die Aktualisierung von UI-Objekten (wie Menüelemente und Symbolleistenschaltflächen), um die aktuelle Verfügbarkeit eines Befehls widerzuspiegeln.

## <a name="command-ids"></a>Befehls-IDs

Eine Erläuterung des Befehlsroutings und des Bindungsprozesses finden Sie unter Visual C++. [Technische Anmerkung 20](../mfc/tn020-id-naming-and-numbering-conventions.md) enthält Informationen zur ID-Benennung.

Wir verwenden das generische Präfix "ID_" für Befehls-IDs. Befehls-IDs sind >= 0x8000. In der Nachrichtenzeile oder Statusleiste wird die Befehlsbeschreibungszeichenfolge angezeigt, wenn eine STRINGTABLE-Ressource mit denselben IDs wie die Befehls-ID vorhanden ist.

In den Ressourcen Ihrer Anwendung kann an mehreren Stellen eine Befehls-ID angezeigt werden:

- In einer STRINGTABLE-Ressource, die dieselbe ID wie die Meldungszeilenaufforderung hat.

- In möglicherweise vielen MENU-Ressourcen, die an Menüelemente angefügt sind, die denselben Befehl aufrufen.

- (ADVANCED) in einer Dialogtaste für einen GOSUB-Befehl.

Im Quellcode Ihrer Anwendung kann an mehreren Stellen eine Befehls-ID angezeigt werden:

- In Ihrer RESOURCE. H (oder eine andere Hauptsymbolheaderdatei), um anwendungsspezifische Befehls-IDs zu definieren.

- PERHAPS In einem ID-Array, das zum Erstellen einer Symbolleiste verwendet wird.

- In einem ON_COMMAND Makro.

- PERHAPS In einem ON_UPDATE_COMMAND_UI Makro.

Derzeit ist die einzige Implementierung in MFC, die Befehls-IDs erfordert, >= 0x8000 ist die Implementierung von GOSUB-Dialogen/Befehlen.

## <a name="gosub-commands-using-command-architecture-in-dialogs"></a>GOSUB-Befehle, Verwenden der Befehlsarchitektur in Dialogen

Die Befehlsarchitektur des Routings und Aktivierens von Befehlen eignet sich gut für Framefenster, Menüelemente, Symbolleistenschaltflächen, Dialogleistenschaltflächen, andere Steuerleisten und andere Benutzeroberflächenelemente, die entwickelt wurden, um Befehle bedarfsgerecht zu aktualisieren und Befehle weiterzuleiten oder IDs an ein Hauptbefehlsziel (in der Regel das Hauptrahmenfenster) zu steuern. Dieses Hauptbefehlsziel kann den Befehl oder die Steuerbenachrichtigungen gegebenenfalls an andere Befehlszielobjekte weiterleiten.

Ein Dialogfeld (modal oder moduslos) kann von einigen Funktionen der Befehlsarchitektur profitieren, wenn Sie der entsprechenden Befehls-ID die Steuerungs-ID des Dialogsteuerelements zuweisen. Die Unterstützung von Dialogfeldern erfolgt nicht automatisch, daher müssen Sie möglicherweise zusätzlichen Code schreiben.

Beachten Sie, dass Ihre Befehls-IDs >= 0x8000 sein sollten, damit alle diese Funktionen ordnungsgemäß funktionieren. Da viele Dialoge an denselben Frame weitergeleitet werden können, sollten freigegebene Befehle >= 0x8000 sein, während die nicht freigegebenen IDCs in einem bestimmten Dialogfeld <= 0x7FFF sein sollten.

Sie können eine normale Schaltfläche in einem normalen modalen Dialog mit dem IDC der Schaltfläche auf die entsprechende Befehls-ID setzen. Wenn der Benutzer die Schaltfläche auswählt, erhält der Besitzer des Dialogfelds (in der Regel das Hauptrahmenfenster) den Befehl wie jeder andere Befehl. Dies wird als GOSUB-Befehl bezeichnet, da er normalerweise verwendet wird, um ein anderes Dialogfeld (ein GOSUB des ersten Dialogs) aufzurufen.

Sie können die `CWnd::UpdateDialogControls` Funktion auch in Ihrem Dialog aufrufen und ihr die Adresse Ihres Hauptrahmenfensters übergeben. Diese Funktion aktiviert oder deaktiviert die Dialogsteuerelemente, je nach, ob sie Befehlshandler im Frame haben. Diese Funktion wird automatisch für Sie für Steuerleisten in der Leerlaufschleife Ihrer Anwendung aufgerufen, aber Sie müssen sie direkt für normale Dialoge aufrufen, die Sie mit dieser Funktion verwenden möchten.

## <a name="when-on_update_command_ui-is-called"></a>Wenn ON_UPDATE_COMMAND_UI aufgerufen wird

Die Beibehaltung des aktivierten/geprüften Zustands aller Menüelemente eines Programms kann ein rechenaufwendiges Problem sein. Eine gängige Technik besteht darin, Menüelemente nur dann zu aktivieren/zu überprüfen, wenn der Benutzer den POPUP auswählt. Die MFC 2.0-Implementierung von `CFrameWnd` behandelt die WM_INITMENUPOPUP-Nachricht und verwendet die Befehlsroutingarchitektur, um die Zustände von Menüs über ON_UPDATE_COMMAND_UI-Handler zu bestimmen.

`CFrameWnd`behandelt auch die WM_ENTERIDLE Nachricht, um das aktuelle Menüelement zu beschreiben, das in der Statusleiste ausgewählt ist (auch als Meldungszeile bezeichnet).

Die Menüstruktur einer Anwendung, die von Visual C++ bearbeitet wird, wird verwendet, um die potenziellen Befehle darzustellen, die zu WM_INITMENUPOPUP Zeitpunkt verfügbar sind. ON_UPDATE_COMMAND_UI Handler den Status oder Text eines Menüs ändern können, oder für erweiterte Anwendungen (z. B. die Datei-MRU-Liste oder das POPupmenü OLE-Verben), die Menüstruktur tatsächlich ändern, bevor das Menü gezeichnet wird.

Die gleiche Art von ON_UPDATE_COMMAND_UI Verarbeitung wird für Symbolleisten (und andere Steuerleisten) durchgeführt, wenn die Anwendung in ihre Leerlaufschleife eintritt. Weitere Informationen zu Steuerleisten finden Sie in der *Klassenbibliotheksreferenz* und [im Technischen Hinweis 31.](../mfc/tn031-control-bars.md)

## <a name="nested-pop-up-menus"></a>Verschachtelte Popupmenüs

Wenn Sie eine verschachtelte Menüstruktur verwenden, werden Sie feststellen, dass der ON_UPDATE_COMMAND_UI Handler für das erste Menüelement im Popupmenü in zwei verschiedenen Fällen aufgerufen wird.

Zuerst wird es für das Pop-up-Menü selbst aufgerufen. Dies ist notwendig, da Popupmenüs keine IDs haben und wir die ID des ersten Menüelements des Popupmenüs verwenden, um auf das gesamte Popupmenü zu verweisen. In diesem Fall *m_pSubMenu* ist die `CCmdUI` m_pSubMenu Membervariable des Objekts nicht NULL und weist auf das Popupmenü hin.

Zweitens wird es kurz vor dem Zeichnen der Menüpunkte im Popup-Menü aufgerufen. In diesem Fall bezieht sich die ID nur *m_pSubMenu* auf das `CCmdUI` erste Menüelement, und die m_pSubMenu Membervariable des Objekts null ist.

Auf diese Weise können Sie das Popupmenü aktivieren, das sich von seinen Menüelementen unterscheidet, erfordert jedoch, dass Sie einen menübewussten Code schreiben. Zum Beispiel in einem verschachtelten Menü mit der folgenden Struktur:

```Output
File>
    New>
    Sheet (ID_NEW_SHEET)
    Chart (ID_NEW_CHART)
```

Die Befehle ID_NEW_SHEET und ID_NEW_CHART können unabhängig aktiviert oder deaktiviert werden. Das Popupmenü **"Neu"** sollte aktiviert sein, wenn eine der beiden aktiviert ist.

Der Befehlshandler für ID_NEW_SHEET (der erste Befehl im Pop-up) würde etwa wie folgt aussehen:

```cpp
void CMyApp::OnUpdateNewSheet(CCmdUI* pCmdUI)
{
    if (pCmdUI->m_pSubMenu != NULL)
    {
        // enable entire pop-up for "New" sheet and chart
        BOOL bEnable = m_bCanCreateSheet || m_bCanCreateChart;
        // CCmdUI::Enable is a no-op for this case, so we
        // must do what it would have done.
        pCmdUI->m_pMenu->EnableMenuItem(pCmdUI->m_nIndex,
            MF_BYPOSITION |
            (bEnable  MF_ENABLED : (MF_DISABLED | MF_GRAYED)));

        return;
    }
    // otherwise just the New Sheet command
    pCmdUI->Enable(m_bCanCreateSheet);
}
```

Der Befehlshandler für ID_NEW_CHART wäre ein normaler Updatebefehlshandler und sieht etwa wie folgt aus:

```cpp
void CMyApp::OnUpdateNewChart(CCmdUI* pCmdUI)
{
    pCmdUI->Enable(m_bCanCreateChart);
}
```

## <a name="on_command-and-on_bn_clicked"></a>ON_COMMAND und ON_BN_CLICKED

Die Nachrichtenzuordnungsmakros für **ON_COMMAND** und **ON_BN_CLICKED** sind identisch. Der MFC-Befehls- und Steuerungsbenachrichtigungsroutingmechanismus verwendet nur die Befehls-ID, um zu entscheiden, wohin die Weiterleitung geplant werden soll. Steuerbenachrichtigungen mit Steuerbenachrichtigungscode von Null (**BN_CLICKED**) werden als Befehle interpretiert.

> [!NOTE]
> Tatsächlich durchlaufen alle Steuerbenachrichtigungen die Befehlshandlerkette. Beispielsweise ist es technisch möglich, einen Steuerbenachrichtigungshandler für **EN_CHANGE** in Ihrer Dokumentklasse zu schreiben. Dies ist im Allgemeinen nicht ratsam, da die praktischen Anwendungen dieser Funktion nur wenige sind, die Funktion von ClassWizard nicht unterstützt wird und die Verwendung der Funktion zu fragilem Code führen kann.

## <a name="disabling-the-automatic-disabling-of-button-controls"></a>Deaktivieren der automatischen Deaktivierung von Button-Steuerelementen

Wenn Sie ein Schaltflächensteuerelement in einer Dialogleiste oder in einem Dialogfeld platzieren, in dem Sie **CWnd::UpdateDialogControls** eigennwilligen Aufrufen verwenden, werden Sie feststellen, dass Schaltflächen, die nicht **über ON_COMMAND** oder **ON_UPDATE_COMMAND_UI** Handler verfügen, vom Framework automatisch für Sie deaktiviert werden. In einigen Fällen benötigen Sie keinen Handler, aber Sie möchten, dass die Schaltfläche aktiviert bleibt. Der einfachste Weg, dies zu erreichen, besteht darin, einen Dummy-Befehlshandler hinzuzufügen (einfach mit ClassWizard zu tun) und nichts darin zu tun.

## <a name="window-message-routing"></a>Fenster-Nachrichten-Routing

Im Folgenden werden einige weiter fortgeschrittene Themen zu den MFC-Klassen beschrieben und erläutert, wie sich das Routing von Windows-Nachrichten und andere Themen auf sie auswirken. Die Informationen hier werden nur kurz beschrieben. Weitere Informationen zu öffentlichen APIs finden Sie in der *Klassenbibliotheksreferenz.* Weitere Informationen zu Implementierungsdetails finden Sie im Quellcode der MFC-Bibliothek.

Weitere Informationen zur Fensterbereinigung, einem sehr wichtigen Thema für alle **CWnd-abgeleiteten**Klassen, finden Sie in [Technical Note 17.](../mfc/tn017-destroying-window-objects.md)

## <a name="cwnd-issues"></a>CWnd-Probleme

Die Implementierungsmemberfunktion **CWnd::OnChildNotify** bietet eine leistungsstarke und erweiterbare Architektur für untergeordnete Fenster (auch als Steuerelemente bezeichnet), um Nachrichten, Befehle und Steuerbenachrichtigungen, die an ihren übergeordneten (oder "Besitzer" ) gesendet werden, zu hooken oder anderweitig zu informieren. Wenn das untergeordnete Fenster (/Steuerelement) selbst ein **C++CWnd-Objekt** ist, wird die virtuelle Funktion **OnChildNotify** zuerst mit den Parametern aus der ursprünglichen Nachricht (d. h. einer **MSG-Struktur)** aufgerufen. Das untergeordnete Fenster kann die Nachricht in Ruhe lassen, sie essen oder die Nachricht für das übergeordnete Element (selten) ändern.

Die standardmäßige **CWnd-Implementierung** verarbeitet die folgenden Meldungen und verwendet den **OnChildNotify-Hook,** damit untergeordnete Fenster (Steuerelemente) zuerst auf die Nachricht zugreifen können:

- **WM_MEASUREITEM** und **WM_DRAWITEM** (zur Selbstauslosung)

- **WM_COMPAREITEM** und **WM_DELETEITEM** (zur Selbstauslosung)

- **WM_HSCROLL** und **WM_VSCROLL**

- **WM_CTLCOLOR**

- **WM_PARENTNOTIFY**

Sie werden feststellen, dass der **OnChildNotify-Hook** zum Ändern von Besitzer-Zeichnungsnachrichten in selbstzeichnende Nachrichten verwendet wird.

Zusätzlich zum **OnChildNotify-Hook** weisen Bildlaufnachrichten ein weiteres Routingverhalten auf. Weitere Informationen zu Bildlaufleisten und Quellen **WM_HSCROLL** und **WM_VSCROLL** Nachrichten finden Sie weiter unten.

## <a name="cframewnd-issues"></a>CFrameWnd-Probleme

Die **CFrameWnd-Klasse** stellt den größten Teil der Befehlsrouting- und Benutzeroberflächenaktualisierungsimplementierung bereit. Dies wird hauptsächlich für das Hauptrahmenfenster der Anwendung verwendet (**CWinApp::m_pMainWnd**), gilt jedoch für alle Rahmenfenster.

Das Hauptrahmenfenster ist das Fenster mit der Menüleiste und ist das übergeordnete Element der Statusleiste oder Meldungszeile. Weitere Informationen zum Befehlsrouting und WM_INITMENUPOPUP finden Sie in der obigen **Diskussion.**

Die **CFrameWnd-Klasse** bietet die Verwaltung der aktiven Ansicht. Die folgenden Meldungen werden durch die aktive Ansicht weitergeleitet:

- Alle Befehlsmeldungen (die aktive Ansicht erhält zuerst Zugriff darauf).

- **WM_HSCROLL** und **WM_VSCROLL** Nachrichten von gleichgeordneten Bildlaufleisten (siehe unten).

- **WM_ACTIVATE** (und **WM_MDIACTIVATE** für MDI) werden in Aufrufe der virtuellen Funktion **CView::OnActivateView**umgewandelt.

## <a name="cmdiframewndcmdichildwnd-issues"></a>CMDIFrameWnd/CMDIChildWnd-Probleme

Beide MDI-Rahmenfensterklassen leiten sich von **CFrameWnd** ab und sind daher beide für die gleiche Art von Befehlsrouting und Benutzeroberflächenaktualisierung aktiviert, die in **CFrameWnd**bereitgestellt wird. In einer typischen MDI-Anwendung enthält nur das Hauptframefenster (d. h. das **CMDIFrameWnd-Objekt)** die Menüleiste und die Statusleiste und ist daher die Hauptquelle der Befehlsroutingimplementierung.

Das allgemeine Routingschema besteht darin, dass das aktive untergeordnete MDI-Fenster ersten Zugriff auf Befehle erhält. Die **standardmäßigen PreTranslateMessage-Funktionen** verarbeiten Beschleunigertabellen sowohl für mDI-untergeordnete Fenster (erste) als auch für den MDI-Frame (zweiter) sowie für die standardmäßigen MDI-Systembefehlsbeschleuniger, die normalerweise von **TranslateMDISysAccel (zuletzt)** verarbeitet werden.

## <a name="scroll-bar-issues"></a>Scroll-Leiste-Probleme

Bei der Verarbeitung von scroll-message (**WM_HSCROLL**/**OnHScroll** und/oder **WM_VSCROLL**/**OnVScroll**) sollten Sie versuchen, den Handlercode zu schreiben, damit er sich nicht darauf verlässt, woher die Bildlaufleistennachricht stammt. Dies ist nicht nur ein allgemeines Windows-Problem, da Bildlaufnachrichten von echten Bildlaufleistensteuerelementen oder von **WS_HSCROLL**/**WS_VSCROLL** Bildlaufleisten stammen können, die keine Bildlaufleistensteuerelemente sind.

MFC erweitert dies, damit Bildlaufleistensteuerelemente entweder untergeordnete oder gleichgeordnete Fenster gescrollt werden können (tatsächlich kann die übergeordnete/kind-Beziehung zwischen der Bildlaufleiste und dem Fenster, das gescrollt wird, alles sein). Dies ist besonders wichtig für gemeinsame Bildlaufleisten mit Splitterfenstern. Weitere Informationen zur Implementierung von **CSplitterWnd** finden Sie im [Technischen Hinweis 29,](../mfc/tn029-splitter-windows.md) einschließlich weiterer Informationen zu Problemen mit der geteilten Bildlaufleiste.

Nebenbei ist zu beachten, dass es zwei von **CWnd** abgeleitete Klassen gibt, bei denen die zum Erstellungszeitpunkt angegebenen Bildlaufleistenstile gefangen und nicht an Windows übergeben werden. Wenn sie an eine Erstellungsroutine übergeben werden, können **WS_HSCROLL** und **WS_VSCROLL** unabhängig festgelegt werden, aber nach der Erstellung kann nicht mehr geändert werden. Natürlich sollten Sie die WS_SCROLL Stilbits des fensters, das sie erstellt haben, nicht direkt testen oder festlegen.

Für **CMDIFrameWnd** werden die Scrollleistenstile, die Sie an **Erstellen** oder **LoadFrame** übergeben, zum Erstellen des MDICLIENT verwendet. Wenn Sie einen scrollbaren MDICLIENT-Bereich (wie den Windows-Programm-Manager) wünschen, legen Sie beide Bildlaufleistenstile **(WS_HSCROLL** &#124; **WS_VSCROLL**) für den Stil fest, der zum Erstellen des **CMDIFrameWnd**verwendet wird.

Für **CSplitterWnd** gelten die Bildlaufleistenstile für die speziellen freigegebenen Bildlaufleisten für die Splitterbereiche. Bei statischen Splitterfenstern legen Sie normalerweise keinen Bildlaufleistenstil fest. Bei dynamischen Splitterfenstern haben Sie in der Regel den Stil der Bildlaufleiste für die Richtung festgelegt, die Sie teilen möchten, **d. h. WS_HSCROLL,** wenn Sie Zeilen aufteilen können, **WS_VSCROLL,** wenn Sie Spalten aufteilen können.

## <a name="see-also"></a>Siehe auch

[Technische Hinweise – nach Nummern geordnet](../mfc/technical-notes-by-number.md)<br/>
[Technische Hinweise – nach Kategorien geordnet](../mfc/technical-notes-by-category.md)
