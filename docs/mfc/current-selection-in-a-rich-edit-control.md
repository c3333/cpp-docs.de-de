---
title: Die aktuelle Auswahl in einem RichEdit-Steuerelement
ms.date: 11/04/2016
helpviewer_keywords:
- current selection in CRichEditCtrls
- CRichEditCtrl class [MFC], current selection in
- rich edit controls [MFC], current selection in
- selection, current in CRichEditCtrl
ms.assetid: f6b2a2b6-5481-4ad3-9720-6dd772ea6fc8
ms.openlocfilehash: 9591f1aeb4e159b9b4f70945d6248a3b8d1dc827
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626489"
---
# <a name="current-selection-in-a-rich-edit-control"></a>Die aktuelle Auswahl in einem RichEdit-Steuerelement

Der Benutzer kann Text in einem Rich-Edit-Steuerelement ([CRichEditCtrl](reference/cricheditctrl-class.md)) mit der Maus oder der Tastatur auswählen. Bei der aktuellen Auswahl handelt es sich um den Bereich der ausgewählten Zeichen oder um die Position der Einfügemarke, wenn keine Zeichen ausgewählt sind. Eine Anwendung kann Informationen zur aktuellen Auswahl, zum Festlegen der aktuellen Auswahl, zum Bestimmen der aktuellen Auswahl und zum ein-oder Ausblenden der Auswahl Markierung anzeigen.

Verwenden Sie die [GetSEL](reference/cricheditctrl-class.md#getsel) -Member-Funktion, um die aktuelle Auswahl in einem Rich-Edit-Steuerelement zu bestimmen. Um die aktuelle Auswahl festzulegen, verwenden Sie die [SetSel](reference/cricheditctrl-class.md#setsel) -Member-Funktion. Die [charrange](/windows/win32/api/richedit/ns-richedit-charrange) -Struktur wird mit diesen Funktionen verwendet, um einen Zeichenbereich anzugeben. Zum Abrufen von Informationen über den Inhalt der aktuellen Auswahl können Sie die [GetSelectionType](reference/cricheditctrl-class.md#getselectiontype) -Member-Funktion verwenden.

Standardmäßig wird ein Rich-Edit-Steuerelement angezeigt und ausgeblendet, wenn es den Fokus erhält und den Fokus verliert. Sie können die Auswahl Markierung jederzeit mithilfe der Member-Funktion [HideSelection](reference/cricheditctrl-class.md#hideselection) anzeigen oder ausblenden. Beispielsweise kann eine Anwendung ein Such Dialogfeld bereitstellen, um Text in einem Rich-Edit-Steuerelement zu finden. Die Anwendung wählt den übereinstimmenden Text aus, ohne das Dialogfeld zu schließen. in diesem Fall muss Sie verwendet werden, `HideSelection` um die Auswahl hervorzuheben.

Um den ausgewählten Text in einem Rich-Edit-Steuerelement zu erhalten, verwenden Sie die [GetSelText](reference/cricheditctrl-class.md#getseltext) -Member-Funktion. Der Text wird in das angegebene Zeichen Array kopiert. Sie müssen sicherstellen, dass das Array groß genug ist, um den ausgewählten Text und ein abschließendes NULL-Zeichen zu speichern.

Sie können in einem Rich-Edit-Steuerelement mithilfe der [FindText](reference/cricheditctrl-class.md#findtext) -Member-Funktion nach einer Zeichenfolge suchen, indem Sie die [FINDTEXTEX](/windows/win32/api/richedit/ns-richedit-findtextexw) -Struktur verwenden, die mit dieser Funktion verwendet wird, sowie die zu suchende Zeichenfolge. Sie können diese Optionen auch so angeben, ob bei der Suche die Groß-/Kleinschreibung beachtet wird.

## <a name="see-also"></a>Siehe auch

[Verwenden von CRichEditCtrl](using-cricheditctrl.md)<br/>
[Steuerelemente](controls-mfc.md)
