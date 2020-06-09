---
title: Zwischenablageoperationen in RichEdit-Steuerelementen
ms.date: 11/04/2016
helpviewer_keywords:
- pasting Clipboard data
- CRichEditCtrl class [MFC], paste operation
- cut operation in CRichEditCtrl class [MFC]
- CRichEditCtrl class [MFC], Clipboard operations
- copy operations in rich edit controls
- Clipboard, operations in CRichEditCtrl
- rich edit controls [MFC], Clipboard operations
ms.assetid: 15ce66bc-2636-4a35-a2ae-d52285dc1af6
ms.openlocfilehash: 3dea112ed32ae618991f6ff5f05823bd5be001b6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624857"
---
# <a name="clipboard-operations-in-rich-edit-controls"></a>Zwischenablageoperationen in RichEdit-Steuerelementen

Die Anwendung kann den Inhalt der Zwischenablage in ein Rich-Edit-Steuerelement ([CRichEditCtrl](reference/cricheditctrl-class.md)) einfügen, indem Sie entweder das beste verfügbare Zwischenablage Format oder ein bestimmtes Zwischenablage Format verwendet. Sie können auch bestimmen, ob ein Rich-Edit-Steuerelement in der Lage ist, ein Zwischenablage Format einzufügen.

Sie können den Inhalt der aktuellen Auswahl mithilfe der [Kopier](reference/cricheditctrl-class.md#copy) -oder [Ausschneide](reference/cricheditctrl-class.md#cut) Element Funktion kopieren oder Ausschneiden. Entsprechend können Sie den Inhalt der Zwischenablage mithilfe der Funktion Member [Einfügen](reference/cricheditctrl-class.md#paste) in ein Rich-Edit-Steuerelement einfügen. Das Steuerelement fügt das erste verfügbare Format, das es erkennt, ein, das vermutlich das beschreibende Format darstellt.

Wenn Sie ein bestimmtes Zwischenablage Format einfügen möchten, können Sie die " [PasteSpecial](reference/cricheditctrl-class.md#pastespecial) "-Member-Funktion verwenden. Diese Funktion ist nützlich für Anwendungen mit einem speziellen Befehl zum Einfügen, mit dem Benutzer das Zwischenablage Format auswählen können. Mithilfe der [CanPaste](reference/cricheditctrl-class.md#canpaste) -Member-Funktion können Sie ermitteln, ob ein bestimmtes Format vom Steuerelement erkannt wird.

Sie können auch verwenden `CanPaste` , um zu bestimmen, ob ein verfügbares Zwischenablage Format von einem Rich Edit-Steuerelement erkannt wird. Diese Funktion ist im- `OnInitMenuPopup` Handler nützlich. Eine Anwendung kann den Einfüge Befehl in Abhängigkeit davon aktivieren oder grauen, ob das Steuerelement ein beliebiges verfügbares Format einfügen kann.

Rich Edit-Steuerelemente registrieren zwei Zwischenablage Formate: Rich-Text-Format und ein Format namens RichEdit-Text und-Objekte. Eine Anwendung kann diese Formate mithilfe der [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) -Funktion registrieren, wobei die Werte **CF_RTF** und **CF_RETEXTOBJ** angegeben werden.

## <a name="see-also"></a>Siehe auch

[Verwenden von CRichEditCtrl](using-cricheditctrl.md)<br/>
[Steuerelemente](controls-mfc.md)
