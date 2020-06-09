---
title: Formatieren von Zeichen in RichEdit-Steuerelementen
ms.date: 11/04/2016
helpviewer_keywords:
- formatting [MFC], characters
- rich edit controls [MFC], character formatting in
- CRichEditCtrl class [MFC], character formatting in
ms.assetid: c80f4305-75ad-45f9-8d17-d83d0fe79be5
ms.openlocfilehash: 0b9d925b6ba3157177b7012d1e303ef7b7ddab46
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624934"
---
# <a name="character-formatting-in-rich-edit-controls"></a>Formatieren von Zeichen in RichEdit-Steuerelementen

Sie können Element Funktionen des Rich Edit-Steuer Elements ([CRichEditCtrl](reference/cricheditctrl-class.md)) zum Formatieren von Zeichen und zum Abrufen von Formatierungsinformationen verwenden. Für Zeichen können Sie Schriftart, Größe, Farbe und Effekte angeben, z. b. Fett, kursiv und geschützt.

Sie können die Zeichen Formatierung mithilfe der Member-Funktionen [SetSelectionCharFormat](reference/cricheditctrl-class.md#setselectioncharformat) und [SetWordCharFormat](reference/cricheditctrl-class.md#setwordcharformat) anwenden. Verwenden Sie zum Bestimmen der aktuellen Zeichen Formatierung für den ausgewählten Text die Member-Funktion von [GetSelectionCharFormat](reference/cricheditctrl-class.md#getselectioncharformat) . Die [Charformat](/windows/win32/api/richedit/ns-richedit-charformata) -Struktur wird mit diesen Element Funktionen zum Angeben von Zeichen Attributen verwendet. Eines der wichtigen Member von **Charformat** ist **dwMask**. In `SetSelectionCharFormat` und `SetWordCharFormat` gibt **dwMask** an, welche Zeichen Attribute von diesem Funktions aufrut festgelegt werden. `GetSelectionCharFormat`meldet die Attribute des ersten Zeichens in der Auswahl. **dwMask** gibt die Attribute an, die in der gesamten Auswahl einheitlich sind.

Sie können auch die "Standard Zeichen Formatierung" erhalten und festlegen. Hierbei handelt es sich um die Formatierung, die auf alle nachträglich eingefügten Zeichen angewendet wird. Wenn eine Anwendung z. b. die Standard Zeichenformatierung auf "Fett" festlegt und der Benutzer dann ein Zeichen eingibt, ist dieses Zeichen fett formatiert. Um die Standard Zeichen Formatierung abzurufen und festzulegen, verwenden Sie die Member-Funktionen [getdefaultcharformat](reference/cricheditctrl-class.md#getdefaultcharformat) und [SetDefaultCharFormat](reference/cricheditctrl-class.md#setdefaultcharformat) .

Mit dem "geschützten" Zeichen Attribut wird die Darstellung von Text nicht geändert. Wenn der Benutzer versucht, geschützten Text zu ändern, sendet ein Rich Edit-Steuerelement das übergeordnete Fenster an eine **EN_PROTECTED** Benachrichtigungs Meldung, sodass das übergeordnete Fenster die Änderung zulassen oder verhindern kann. Um diese Benachrichtigungs Meldung zu erhalten, müssen Sie Sie mithilfe der Member-Funktion " [setteventmask](reference/cricheditctrl-class.md#seteventmask) " aktivieren. Weitere Informationen zur Ereignis Maske finden Sie unter [Benachrichtigungen von einem Rich Edit-Steuer](notifications-from-a-rich-edit-control.md)Element weiter unten in diesem Thema.

Die Vordergrundfarbe ist ein Zeichen Attribut, aber die Hintergrundfarbe ist eine Eigenschaft des Rich-Edit-Steuer Elements. Um die Hintergrundfarbe festzulegen, verwenden Sie die [SetBackgroundColor](reference/cricheditctrl-class.md#setbackgroundcolor) -Member-Funktion.

## <a name="see-also"></a>Siehe auch

[Verwenden von CRichEditCtrl](using-cricheditctrl.md)<br/>
[Steuerelemente](controls-mfc.md)
