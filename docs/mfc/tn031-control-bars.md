---
title: 'TN031: Schiebeleisten-Steuerelemente'
ms.date: 11/04/2016
f1_keywords:
- vc.controls.bars
helpviewer_keywords:
- control bars [MFC], styles
- CStatusBar class [MFC], Tech Note 31 usage
- CControlBar class [MFC], Tech Note 31 usage
- CControlBar class [MFC], deriving from
- control bars [MFC], classes [MFC]
- CDialogBar class [MFC], Tech Note 31 usage
- CToolBar class [MFC], Tech Note 31 usage
- TN031
- styles [MFC], control bars
ms.assetid: 8cb895c0-40ea-40ef-90ee-1dd29f34cfd1
ms.openlocfilehash: 37c3a15c281018260e65508dee3799ab0011dbfe
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370303"
---
# <a name="tn031-control-bars"></a>TN031: Schiebeleisten-Steuerelemente

> [!NOTE]
> Der folgende technische Hinweis wurde seit dem ersten Erscheinen in der Onlinedokumentation nicht aktualisiert. Daher können einige Verfahren und Themen veraltet oder falsch sein. Um aktuelle Informationen zu erhalten, wird empfohlen, das gewünschte Thema im Index der Onlinedokumentation zu suchen.

Dieser Hinweis beschreibt die Steuerleistenklassen in MFC: die allgemeine [CControlBar](#_mfcnotes_ccontrolbar), [CStatusBar](#_mfcnotes_cstatusbar), [CToolBar](#_mfcnotes_ctoolbar), [CDialogBar](#_mfcnotes_cdialogbar)und `CDockBar`.

## <a name="ccontrolbar"></a><a name="_mfcnotes_ccontrolbar"></a> CControlBar

A `ControlBar` ist `CWnd`eine -abgeleitete Klasse, die:

- am oberen oder unteren Rand eines Rahmenfensters ausgerichtet ist.

- Sie kann untergeordnete Elemente enthalten, die entweder HWND-basierte Steuerelemente sind (z. B. `CDialogBar`) oder nicht-`HWND` -basierte Elemente (z. B. `CToolBar`, `CStatusBar`).

Steuerleisten unterstützen die zusätzlichen Formatvorlagen:

- CBRS_TOP (Standardeinstellung) die Steuerleiste an die Oberseite anheften.

- CBRS_BOTTOM Pin die Steuerleiste nach unten.

- CBRS_NOALIGN Positionieren Sie die Steuerleiste nicht neu, wenn die Größe des übergeordneten Elements geändert wird.

Von `CControlBar` abgeleitete Klassen bieten interessantere Implementierungen:

- `CStatusBar` Eine Statusleiste, die Elemente sind Statusleistenbereiche, die Text enthalten.

- `CToolBar` Eine Symbolleiste, die Elemente sind in einer Reihe ausgerichtete Bitmapschaltflächen.

- `CDialogBar` Ein symbolleistenähnlicher Frame mit standardmäßigen Windows-Steuerelementen (erstellt aus einer Dialogfeldvorlagen-Ressource).

- `CDockBar`Ein generalisierter Andockbereich für andere `CControlBar` abgeleitete Objekte. Die spezifischen in dieser Klasse verfügbaren Memberfunktionen und -variablen werden wahrscheinlich in zukünftigen Versionen geändert.

Alle Steuerleistenobjekte/Fenster werden untergeordnete Fenster eines übergeordneten Rahmenfensters sein. Sie werden normalerweise als gleichgeordnete Elemente dem Clientbereich des Frames (z.B. einem MDI-Client oder einer Ansicht) hinzugefügt. Die ID einer Steuerleiste als untergeordnetes Fenster ist wichtig. Das Standardlayout der Steuerleiste funktioniert nur bei Steuerleisten mit IDs im Bereich von AFX_IDW_CONTROLBAR_FIRST bis AFX_IDW_CONTROLBAR_LAST. Beachten Sie: Es sind zwar 256 Steuerleisten-IDs verfügbar, doch die ersten 32 davon sind für spezielle Zwecke bestimmt, da sie direkt von der Seitenansichtarchitektur unterstützt werden.

Die `CControlBar` -Klasse bietet die Standardimplementierung für:

- Ausrichten von Steuerleisten am oberen und unteren Rand bzw. den Seiten des Frames.

- Zuweisen von Steuerelementarrays.

- Unterstützung der Implementierung abgeleiteter Klassen.

C++-Steuerleistenobjekte werden in der Regel als Mitglieder einer `CFrameWnd` -abgeleiteten Klasse eingebettet und bereinigt, wenn übergeordneter `HWND` und übergeordnetes Objekt zerstört werden. Wenn Sie ein Steuerleistenobjekt auf dem Heap belegen müssen, legen Sie für den Member *m_bAutoDestruct* einfach **TRUE** fest, damit die Steuerleiste „**dieses löscht**“, wenn der `HWND` zerstört wird.

> [!NOTE]
> Wenn Sie eine `CControlBar`eigene -abgeleitete Klasse erstellen, anstatt eine der `CStatusBar`abgeleiteten MFC-Klassen wie , `CToolBar`oder `CDialogBar`zu verwenden, müssen Sie den *m_dwStyle* Datenmember festlegen. Dies kann in der `Create`Außerkraftsetzung von erfolgen:

```
// CMyControlBar is derived from CControlBar
BOOL CMyControlBar::Create(CWnd* pParentWnd,
    DWORD dwStyle,
    UINT nID)
{
    m_dwStyle = dwStyle;

.
.
.
}
```

**Steuerleistenlayout-Algorithmus**

Der Steuerleistenlayout-Algorithmus ist sehr einfach. Das Rahmenfenster sendet eine Meldung WM_SIZEPARENT an alle untergeordneten Elemente im Steuerleistenbereich. Zusammen mit dieser Meldung wird ein Zeiger auf das Clientrechteck des übergeordneten Elements übergeben. Diese Meldung wird in Z-Reihenfolge an die untergeordneten Elemente gesendet. Die untergeordneten Elemente der Steuerleiste verwenden diese Informationen, um sich selbst zu positionieren und den Clientbereich des übergeordneten Elements zu reduzieren. Das finale Rechteck, das für den normalen Clientbereich übrig bleibt (weniger Steuerleisten), wird zum Positionieren des Hauptclientfensters verwendet (normalerweise ein MDI-Client-, Ansichts- oder Splitterfenster).

Ausführliche Informationen finden Sie unter `CWnd::RepositionBars` und `CFrameWnd::RecalcLayout` .

MFC private Windows-Nachrichten, einschließlich WM_SIZEPARENT, sind in [Technical Note 24](../mfc/tn024-mfc-defined-messages-and-resources.md)dokumentiert.

## <a name="cstatusbar"></a><a name="_mfcnotes_cstatusbar"></a>CStatusBar

Eine Statusleiste ist eine Steuerleiste mit einer Reihe von Textausgabebereichen. Es gibt zwei allgemeine Verfahren zum Verwenden von Textausgabebereichen:

- Als Meldungszeile

     (z. B. die standardmäßige Menü-Hilfemeldungszeile). Auf diese wird in der Regel über einen 0-basierten Index zugegriffen.

- Als Statusindikatoren

     (z. B. KAP-, NUM- und ROLL-Indikator). Auf diese wird in der Regel über die String-/Befehls-ID zugegriffen.

Die Schriftart für die Statusleiste ist 10 Punkt MS Sans Serif (vorgegeben vom Windows Interface Application Design Guide oder der laut Schriftarten-Mapper am besten übereinstimmenden 10 Punkt Swiss-Proportionalschriftart). Für bestimmte Windows-Versionen, z. B. die japanische Edition, werden andere Schriftarten ausgewählt.

Die in der Statusleiste verwendeten Farben entsprechen auch der Empfehlung des Windows Interface Application Design Guide. Diese Farben sind nicht hartcodiert und ändern sich dynamisch gemäß der Benutzeranpassung in der Systemsteuerung.

|Element|Windows-COLOR-Wert|RGB-Standard|
|----------|-------------------------|-----------------|
|Statusleisten-Hintergrund|COLOR_BTNFACE|RGB(192, 192, 192)|
|Statusleistentext|COLOR_BTNTEXT|RGB(000, 000, 000)|
|Statusleistenränder oben/links|COLOR_BTNHIGHLIGHT|RGB(255, 255, 255)|
|Statusleistenränder unten/links|COLOR_BTNSHADOW|RGB(128, 128, 128)|

**CCmdUI-Unterstützung für CStatusBar**

Die Art und Weise, wie Indikatoren in der Regel aktualisiert werden, erfolgt über den ON_UPDATE_COMMAND_UI Mechanismus. Im Leerlauf ruft die Statusleiste den ON_UPDATE_COMMAND_UI Handler mit der Zeichenfolgen-ID des Indikatorbereichs auf.

Der ON_UPDATE_COMMAND_UI-Handler kann aufrufen:

- `Enable`: Aktivieren oder deaktivieren Sie den Bereich. Ein deaktivierter Bereich sieht genau so aus wie ein aktivierter Bereich, doch der Text ist nicht sichtbar (d. h. der Textindikator ist deaktiviert).

- `SetText`: So ändern Sie den Text. Wenden Sie dies mit Vorsicht an, da der Bereich nicht automatisch angepasst wird.

Unter Klasse [CStatusBar](../mfc/reference/cstatusbar-class.md) in der *Klassenbibliotheksreferenz* finden Sie weitere Informationen zur `CStatusBar` -Erstellung und Anpassung von APIs. Die Anpassung der Statusleisten sollte im Wesentlichen erfolgen, bevor die Statusleiste zuerst angezeigt wird.

Die Statusleiste unterstützt nur einen einzigen, dehnbaren Bereich, in der Regel den ersten Bereich. Die Größe dieses Bereichs ist wirklich eine Mindestgröße. Überschreitet die Statusleiste die minimale Größe aller Bereiche, wird jede zusätzliche Breite dem dehnbaren Bereich zugewiesen. Die Standardanwendung mit einer Statusleiste verfügt über rechtsbündige Indikatoren für KAP, NUM und ROLL, da der erste Bereich dehnbar ist.

## <a name="ctoolbar"></a><a name="_mfcnotes_ctoolbar"></a>CToolBar

Eine Symbolleiste ist eine Steuerleiste mit einer Reihe von Bitmapschaltflächen, die Trennlinien enthalten können. Zwei Schaltflächenformatvorlagen werden unterstützt: PushButtons und Kontrollkästchen. Die Funkgruppenfunktionalität kann mit Kontrollkästchen-Schaltflächen und ON_UPDATE_COMMAND_UI erstellt werden.

Alle Bitmapschaltflächen der Symbolleiste stammen aus einer einzigen Bitmap. Die Bitmap muss für jede Schaltfläche ein Bild oder eine Glyphe enthalten. In der Regel entspricht die Reihenfolge der Bilder/Glyphen in der Bitmap der Reihenfolge, in der sie auf dem Bildschirm dargestellt werden. (Dies können Sie mit den Anpassungs-APIs ändern.)

Die Schaltflächen müssen gleich groß sein. Der Standardwert beträgt 24 x 22 Pixel. Die Bilder/Glyphen müssen gleich groß sein und Seite an Seite in der Bitmap liegen. Die Standardgröße für Bilder/Glyphen beträgt 16 x 15 Pixel. Aus diesem Grund benötigen Sie für eine Symbolleiste mit 10 Schaltflächen (in Standardgröße) eine Bitmap mit einer Breite von 160 Pixeln und einer Höhe von 15 Pixeln.

Jede Schaltfläche verfügt nur über ein einziges Bild/eine einzige Glyphe. Die verschiedenen Schaltflächenstatus und Formatvorlagen (z. B. gedrückt, oben, unten, deaktiviert, deaktiviert unten, unbestimmt) werden von dem einen Bild/der einen Glyphe aus algorithmisch generiert. Theoretisch kann jede Farbbitmap oder DIB verwendet werden. Der Algorithmus zum Generieren der verschiedenen Schaltflächenstatus funktioniert am besten, wenn das ursprüngliche Bild in Graustufen vorliegt. Im allgemeinen MFC-Beispiel [CLIPART](../overview/visual-cpp-samples.md) finden Sie standardmäßige Symbolleistenschaltflächen und Symbolleistenschaltflächen-ClipArt als Beispiel.

Die in der Symbolleiste verwendeten Farben entsprechen auch der Empfehlung des Windows Interface Application Design Guide. Diese Farben sind nicht hartcodiert und ändern sich dynamisch gemäß der Benutzeranpassung in der Systemsteuerung.

|Element|Windows-COLOR-Wert|RGB-Standard|
|----------|-------------------------|-----------------|
|Symbolleistenhintergrund|COLOR_BTNFACE|RGB(192,192,192)|
|Symbolleisten-Schaltflächen oben/links|COLOR_BTNHIGHLIGHT|RGB(255,255,255)|
|Symbolleisten-Schaltflächen unten/rechts|COLOR_BTNSHADOW|RGB(128,128,128)|

Darüber hinaus werden die Symbolleistenbitmap-Schaltflächen neu eingefäbt, als wären sie standardmäßige Windows-Schaltflächen-Steuerelemente. Diese Neueinfärbung tritt auf, wenn die Bitmap aus der Ressource geladen wird, und als Reaktion auf eine Änderung der Systemfarben infolge der Benutzeranpassung in der Systemsteuerung. Die folgenden Farben in einer Bitmap für die Symbolleiste werden automatisch geändert werden, sodass sie mit Vorsicht verwendet werden sollten. Wenn Sie nicht wünschen, dass ein Teil der Bitmap neu gefärbt wird, verwenden Sie eine Farbe, die am ehesten einem der zugeordneten RGB-Werte entspricht. Die Zuordnung erfolgt basierend auf genauen RGB-Werte.

|RGB-Wert|Dynamisch zugeordneter COLOR-Wert|
|---------------|------------------------------------|
|RGB(000, 000, 000)|COLOR_BTNTEXT|
|RGB(128, 128, 128)|COLOR_BTNSHADOW|
|RGB(192, 192, 192)|COLOR_BTNFACE|
|RGB(255, 255, 255)|COLOR_BTNHIGHLIGHT|

Unter Klasse [CToolBar](../mfc/reference/ctoolbar-class.md) in der *Klassenbibliotheksreferenz* finden Sie weitere Informationen zur `CToolBar` -Erstellung und Anpassung von APIs. Die Anpassung der Symbolleisten sollte im Wesentlichen erfolgen, bevor die Symbolleiste zuerst angezeigt wird.

Mit den Anpassungs-APIs können Sie Schaltflächen-IDs, Formatvorlagen sowie Abstandhalterbreite anpassen, und mit ihnen können Sie auch festlegen, welches Bild/welche Glyphe für welche Schaltfläche verwendet wird. Standardmäßig müssen Sie diese APIs nicht verwenden.

## <a name="ccmdui-support-for-ctoolbar"></a>CCmdUI-Unterstützung für CToolBar

Die Art und Weise, wie Symbolleistenschaltflächen immer aktualisiert werden, erfolgt über den ON_UPDATE_COMMAND_UI-Mechanismus. Im Leerlauf ruft die Symbolleiste den ON_UPDATE_COMMAND_UI Handler mit der Befehls-ID dieser Schaltfläche auf. ON_UPDATE_COMMAND_UI wird nicht für Trennzeichen aufgerufen, aber es wird für Druckknöpfe und Kontrollkästchen-Tasten aufgerufen.

Der ON_UPDATE_COMMAND_UI-Handler kann aufrufen:

- `Enable`: Um die Schaltfläche zu aktivieren oder zu deaktivieren. Dies funktioniert gleichermaßen für PushButtons und Kontrollkästchen.

- `SetCheck`: Um den Aktivierungszustand einer Schaltfläche festzulegen. Wenn dies für eine Symbolleisten-Schaltfläche aufgerufen wird, wird sie in ein Kontrollkästchen umgewandelt. `SetCheck` nimmt einen Parameter entgegen, der den Wert 0 (nicht aktiviert), 1 (aktiviert) oder 2 (unbestimmt) haben kann.

- `SetRadio`: Kurzform für `SetCheck`.

Die Kontrollkästchen sind „AUTO“-Kontrollkästchen; wenn der Benutzer sie drückt, wechseln sie sofort den Status. „Aktiviert“ ist der „Unten“- bzw. heruntergedrückte Status. Es ist keine Möglichkeit in die Benutzeroberfläche integriert, eine Schaltfläche in den Status „Unbestimmt“ zu setzen; dies muss durch Code erfolgen.

Die Anpassungs-APIs ermöglichen es Ihnen, den Status einer bestimmten Symbolleistenschaltfläche zu ändern, vorzugsweise sollten Sie diese Zustände im ON_UPDATE_COMMAND_UI-Handler für den Befehl ändern, den die Symbolleistenschaltfläche darstellt. Denken Sie daran, dass die Verarbeitung im Leerlauf den Status von Symbolleistenschaltflächen mit dem ON_UPDATE_COMMAND_UI-Handler ändert, sodass alle Änderungen an diesen Zuständen, die über SetButtonStyle vorgenommen werden, nach dem nächsten Leerlauf verloren gehen können.

Symbolleistenschaltflächen senden WM_COMMAND Nachrichten wie normale Schaltflächen oder Menüelemente und werden normalerweise von einem ON_COMMAND Handler in derselben Klasse behandelt, die den ON_UPDATE_COMMAND_UI-Handler bereitstellt.

Es gibt vier Formatvorlagen für Symbolleistenschaltflächen (TBBS_ Werte), die für Anzeigestatus verwendet werden:

- TBBS_CHECKED: Das Kontrollkästchen ist derzeit aktiviert (unten).

- TBBS_INDETERMINATE: Das Kontrollkästchen ist derzeit unbestimmt.

- TBBS_DISABLED: Die Schaltfläche ist derzeit deaktiviert.

- TBBS_PRESSED: Die Schaltfläche ist derzeit gedrückt.

Die sechs offiziellen Schaltflächen-Formatvorlagen im Windows Interface Application Design Guide werden durch die folgenden TBBS-Werte dargestellt:

- Oben = 0

- Mouse Down = TBBS_PRESSED (&#124; jedem anderen Stil)

- Deaktiviert = TBBS_DISABLED

- Unten = TBBS_CHECKED

- Down Disabled = TBBS_CHECKED &#124; TBBS_DISABLED

- Unbestimmt = TBBS_INDETERMINATE

## <a name="cdialogbar"></a><a name="_mfcnotes_cdialogbar"></a> CDialogBar

Eine Dialogleiste ist eine Steuerleiste, die Windows-Standardsteuerelemente enthält. Sie verhält sich insofern wie ein Dialogfeld, als sie die Steuerelemente enthält und den Wechsel zwischen ihnen mit der Tabulatortaste unterstützt. Sie verhält sich auch in der Hinsicht wie ein Dialogfeld, dass die Leiste mithilfe einer Dialogfeldvorlage dargestellt wird.

Eine `CDialogBar` wird für die Seitenansicht-Symbolleiste verwendet, die standardmäßige PushButton-Steuerelemente enthält.

Die Verwendung einer `CDialogBar` ist vergleichbar mit der Verwendung einer `CFormView`. Sie müssen eine Dialogfeldvorlage für die Dialogleiste definieren und alle Formatvorlagen außer WS_CHILD entfernen. Beachten Sie, dass das Dialogfeld nicht sichtbar sein muss.

Die Steuerelementbenachrichtigungen für eine `CDialogBar` werden an das übergeordnete Element der Steuerleiste gesendet (wie Symbolleisten-Schaltflächen).

## <a name="ccmdui-support-for-cdialogbar"></a>CCmdUI-Unterstützung für CDialogBar

Dialogleistenschaltflächen sollten über den ON_UPDATE_COMMAND_UI Handlermechanismus aktualisiert werden. Im Leerlauf ruft die Dialogleiste den ON_UPDATE_COMMAND_UI Handler mit der Befehls-ID aller Schaltflächen auf, die eine ID >= 0x8000 (d. h. im Bereich der Befehls-IDs) haben.

Der ON_UPDATE_COMMAND_UI-Handler kann aufrufen:

- Enable: Zum Aktivieren oder Deaktivieren der Schaltfläche.

- SetText: Zum Ändern des Texts der Schaltfläche.

Anpassung kann über standardmäßige Fenstermanager-APIs erfolgen.

## <a name="see-also"></a>Siehe auch

[Technische Hinweise – nach Nummern geordnet](../mfc/technical-notes-by-number.md)<br/>
[Technische Hinweise – nach Kategorien geordnet](../mfc/technical-notes-by-category.md)
