---
title: Übersicht über das RichEdit-Steuerelement
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC]
ms.assetid: ad589b9f-a3fd-4820-bf1f-6b1965997e68
ms.openlocfilehash: 9ef696bc348dfb18b797b487224b97261020e11c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366870"
---
# <a name="overview-of-the-rich-edit-control"></a>Übersicht über das RichEdit-Steuerelement

> [!IMPORTANT]
> Wenn Sie ein Rich-Edit-Steuerelement in einem Dialogfeld verwenden (unabhängig davon, ob Ihre Anwendung SDI, MDI oder Dialog-basiert ist), müssen Sie [AfxInitRichEdit](../mfc/reference/application-information-and-management.md#afxinitrichedit) einmal aufrufen, bevor das Dialogfeld angezeigt wird. Ein typischer Ort zum Aufrufen dieser `InitInstance` Funktion befindet sich in der Memberfunktion Ihres Programms. Sie müssen es nicht jedes Mal aufrufen, wenn Sie das Dialogfeld anzeigen, nur zum ersten Mal. Sie müssen nicht `AfxInitRichEdit` anrufen, wenn `CRichEditView`Sie mit arbeiten.

Rich Edit-Steuerelemente ([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)) bieten eine Programmierschnittstelle zum Formatieren von Text. Eine Anwendung muss jedoch alle Benutzeroberflächenkomponenten implementieren, die erforderlich sind, um formatierungsvorgänge für den Benutzer verfügbar zu machen. Das heißt, das Rich-Edit-Steuerelement unterstützt das Ändern der Zeichen- oder Absatzattribute des markierten Textes. Einige Beispiele für Zeichenattribute sind fett, Kursivschrift, Schriftfamilie und Punktgröße. Beispiele für Absatzattribute sind Ausrichtung, Ränder und Tabstopps. Es liegt jedoch an Ihnen, die Benutzeroberfläche bereitzustellen, unabhängig davon, ob es sich um Symbolleistenschaltflächen, Menüelemente oder ein Dialogfeld für Formatzeichen handelt. Es gibt auch Funktionen zum Abfragen des Rich-Edit-Steuerelements für die Attribute der aktuellen Auswahl. Verwenden Sie diese Funktionen, um die aktuellen Einstellungen für die Attribute anzuzeigen, z. B. das Festlegen eines Häkchens auf der Befehlsbenutzeroberfläche, wenn die Auswahl das Formatierungsattribut "Fettzeichen" aufweist.

Weitere Informationen zur Zeichen- und Absatzformatierung finden Sie weiter unten in diesem Thema unter [Zeichenformatierung](../mfc/character-formatting-in-rich-edit-controls.md) und [Absatzformatierung.](../mfc/paragraph-formatting-in-rich-edit-controls.md)

Rich-Edit-Steuerelemente unterstützen fast alle Vorgänge und Benachrichtigungen, die mit mehrzeiligen Bearbeitungssteuerelementen verwendet werden. Daher können Anwendungen, die bereits Bearbeitungssteuerelemente verwenden, leicht geändert werden, um umfangreiche Bearbeitungssteuerelemente zu verwenden. Zusätzliche Meldungen und Benachrichtigungen ermöglichen Anwendungen den Zugriff auf die Funktionen, die für umfangreiche Bearbeitungssteuerelemente eindeutig sind. Informationen zu Bearbeitungssteuerelementen finden Sie unter [CBearbeiten](../mfc/reference/cedit-class.md).

Weitere Informationen zu Benachrichtigungen finden Sie weiter unten in diesem Thema unter [Benachrichtigungen aus einem Rich Edit Control.](../mfc/notifications-from-a-rich-edit-control.md)

## <a name="see-also"></a>Siehe auch

[Verwenden von CRichEditCtrl](../mfc/using-cricheditctrl.md)<br/>
[Steuerelemente](../mfc/controls-mfc.md)
