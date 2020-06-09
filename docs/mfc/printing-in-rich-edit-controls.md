---
title: Drucken mit RichEdit-Steuerelementen
ms.date: 11/04/2016
helpviewer_keywords:
- printing [MFC], CRichEditCtrl
- rich edit controls [MFC], printing
- CRichEditCtrl class [MFC], printing
ms.assetid: dbda0e40-018f-424e-b5d8-7b489aaf27af
ms.openlocfilehash: f275078fbef9026363305bb714da3a2af333c91f
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619822"
---
# <a name="printing-in-rich-edit-controls"></a>Drucken mit RichEdit-Steuerelementen

Sie können ein Rich Edit-Steuerelement ([CRichEditCtrl](reference/cricheditctrl-class.md)) anweisen, seine Ausgabe für ein angegebenes Gerät (z. b. einen Drucker) zu bieten Sie können auch das Ausgabegerät angeben, für das ein Rich-Edit-Steuerelement seinen Text formatiert.

Um einen Teil des Inhalts eines Rich-Edit-Steuer Elements für ein bestimmtes Gerät zu formatieren, können Sie die Funktion " [FormatRange](reference/cricheditctrl-class.md#formatrange) -Member" verwenden. Die Format [Bereichs](/windows/win32/api/richedit/ns-richedit-formatrange) Struktur, die mit dieser Funktion verwendet wird, gibt den zu formatierenden Textbereich und den Gerätekontext (DC) für das Zielgerät an.

Nachdem Sie Text für ein Ausgabegerät formatiert haben, können Sie die Ausgabe mithilfe der [DisplayBand](reference/cricheditctrl-class.md#displayband) -Member-Funktion an das Gerät senden. Durch die wiederholte Verwendung von `FormatRange` und `DisplayBand` kann eine Anwendung, die den Inhalt eines Rich-Edit-Steuer Elements druckt, die Bandbreiten Implementierung implementieren. (Bei der Aufteilung erfolgt die Ausgabe in kleinere Teile für Druckzwecke.)

Sie können die Member-Funktion [SetTargetDevice](reference/cricheditctrl-class.md#settargetdevice) verwenden, um das Zielgerät anzugeben, für das ein Rich-Edit-Steuerelement den Text formatiert. Diese Funktion ist nützlich für WYSIWYG (was Sie sehen, was Sie erhalten), in dem eine Anwendung Text mit den Schriftart Metriken des Standard Druckers und nicht mit dem Bildschirm positioniert.

## <a name="see-also"></a>Siehe auch

[Verwenden von CRichEditCtrl](using-cricheditctrl.md)<br/>
[Steuerelemente](controls-mfc.md)
