---
title: Übersicht über das RichEdit-Steuerelement
ms.date: 11/04/2016
helpviewer_keywords:
- rich edit controls [MFC]
ms.assetid: ad589b9f-a3fd-4820-bf1f-6b1965997e68
ms.openlocfilehash: b99a5c6faaae4679b6aef67f240febbfb0f596e8
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617710"
---
# <a name="overview-of-the-rich-edit-control"></a>Übersicht über das RichEdit-Steuerelement

> [!IMPORTANT]
> Wenn Sie ein Rich-Edit-Steuerelement in einem Dialogfeld verwenden (unabhängig davon, ob es sich um eine SDI-, MDI-oder Dialogfeld basierte Anwendung handelt), müssen Sie [afxiniterchedit](reference/application-information-and-management.md#afxinitrichedit) einmal aufzurufen, bevor das Dialogfeld angezeigt wird. Eine typische Stelle zum Abrufen dieser Funktion ist die Member-Funktion Ihres Programms `InitInstance` . Sie müssen Sie nicht für jedes Mal aufrufen, wenn Sie das Dialogfeld nur beim ersten Mal anzeigen. Wenn Sie mit arbeiten, müssen Sie nicht aufzurufen `AfxInitRichEdit` `CRichEditView` .

Rich Edit-Steuerelemente ([CRichEditCtrl](reference/cricheditctrl-class.md)) stellen eine Programmierschnittstelle zum Formatieren von Text bereit. Allerdings muss eine Anwendung alle Benutzeroberflächen Komponenten implementieren, die für das verfügbar machen von Formatierungs Vorgängen für den Benutzer erforderlich sind. Das heißt, das Rich Edit-Steuerelement unterstützt das Ändern der Zeichen-oder Absatz Attribute des ausgewählten Texts. Einige Beispiele für Zeichen Attribute sind fett formatiert, kursiv, Schriftfamilie und Punktgröße. Beispiele für Absatz Attribute sind Ausrichtung, Ränder und Tabstopps. Allerdings müssen Sie die Benutzeroberfläche bereitstellen, unabhängig davon, ob es sich um Symbolleisten-Schaltflächen, Menü Elemente oder ein Dialogfeld für Formatierungszeichen handelt. Es gibt auch Funktionen zum Abfragen des Rich Edit-Steuer Elements für die Attribute der aktuellen Auswahl. Verwenden Sie diese Funktionen, um die aktuellen Einstellungen für die Attribute anzuzeigen, indem Sie z. b. ein Häkchen auf der Befehls Benutzeroberfläche festlegen, wenn die Auswahl das Fett formatierte Zeichen Formatierungs Attribut aufweist.

Weitere Informationen zur Zeichen-und Absatz Formatierung finden Sie unter [Zeichen Formatierung](character-formatting-in-rich-edit-controls.md) und [Absatz Formatierung](paragraph-formatting-in-rich-edit-controls.md) weiter unten in diesem Thema.

Rich Edit-Steuerelemente unterstützen fast alle Vorgänge und Benachrichtigungs Meldungen, die mit mehrzeiligen Bearbeitungs Steuerelementen verwendet werden. Daher können Anwendungen, die bereits Bearbeitungs Steuerelemente verwenden, problemlos geändert werden, um Rich Edit-Steuerelemente zu verwenden. Zusätzliche Meldungen und Benachrichtigungen ermöglichen Anwendungen den Zugriff auf die Funktionalität, die für Rich-Edit-Steuerelemente eindeutig ist. Weitere Informationen zum Bearbeiten von Steuerelementen finden Sie unter [CEdit](reference/cedit-class.md).

Weitere Informationen zu Benachrichtigungen finden Sie unter [Benachrichtigungen von einem Rich Edit-Steuer](notifications-from-a-rich-edit-control.md) Element weiter unten in diesem Thema.

## <a name="see-also"></a>Siehe auch

[Verwenden von CRichEditCtrl](using-cricheditctrl.md)<br/>
[Steuerelemente](controls-mfc.md)
