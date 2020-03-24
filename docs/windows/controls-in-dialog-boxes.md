---
title: Dialog Feld-SteuerC++Elemente () | Microsoft-Dokumentation
ms.date: 02/15/2019
f1_keywords:
- Custom Control
helpviewer_keywords:
- controls [C++], dialog boxes
- dialog box controls [C++], about dialog box controls
- dialog box controls
- controls [C++], templates
- custom controls [C++], dialog boxes
- custom controls [C++]
- dialog box controls [C++], custom (user) controls
- Dialog Editor [C++], custom controls
ms.assetid: e216c4f9-2fd4-429d-889a-8ebce7bad177
ms.openlocfilehash: c79021387de2c8bc8f7f106a93797b7efb07d6df
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160410"
---
# <a name="dialog-box-controls-c"></a>Dialog Feld-SteuerC++Elemente ()

Sie können einem Dialogfeld Steuerelemente hinzufügen, indem Sie die Registerkarte " **Dialog-Editor** " im [Fenster "Toolbox](/visualstudio/ide/reference/toolbox) " verwenden, mit der Sie das gewünschte Steuerelement auswählen und auf das Dialogfeld ziehen können. Standardmäßig ist das Fenster **Toolbox** auf automatisch ausblenden festgelegt. Wenn der **Dialog-Editor** geöffnet ist, wird er als Registerkarte am linken Rand der Projekt Mappe angezeigt. Sie können das **Toolbox** Fenster jedoch an die Position anheften, indem Sie die Schaltfläche **automatisch im Hintergrund** in der oberen rechten Ecke des Fensters auswählen. Weitere Informationen zum Steuern des Verhaltens dieses Fensters finden Sie unter [Fensterverwaltung](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

Die schnellste Möglichkeit zum Hinzufügen von Steuerelementen zu einem Dialogfeld, zum Neupositionieren vorhandener Steuerelemente oder zum Verschieben von Steuerelementen von einem Dialogfeld zu einem anderen besteht darin, die Drag & Drop-Methode zu verwenden. Die Position des Steuer Elements wird in einer gepunkteten Linie angezeigt, bis Sie im Dialogfeld abgelegt wird. Wenn Sie einem Dialogfeld mit der Drag-and-Drop-Methode ein Steuerelement hinzufügen, erhält das Steuerelement eine Standardhöhe, die für diese Art von Steuerelement geeignet ist.

Wenn Sie ein Steuerelement zu einem Dialogfeld hinzufügen oder es neu positionieren, kann die endgültige Platzierung durch Führungslinien oder Ränder bestimmt werden, oder es wird festgelegt, ob das Layoutraster aktiviert ist.

Nachdem Sie dem Dialogfeld ein Steuerelement hinzugefügt haben, können Sie Eigenschaften wie die Beschriftung im [Eigenschaften Fenster](/visualstudio/ide/reference/properties-window)ändern. Sie können auch mehrere Steuerelemente auswählen und ihre Eigenschaften gleichzeitig ändern.

Weitere Informationen über den **Dialog-Editor**finden Sie unter Vorgehensweise beim [hinzufügen, bearbeiten oder löschen](adding-editing-or-deleting-controls.md)von Steuerelementen, [Layoutsteuerelementen](../windows/arrangement-of-controls-on-dialog-boxes.md)und [Definieren von Steuerelement Zugriff und-Werten](../windows/defining-mnemonics-access-keys.md).

Weitere Informationen zu Steuerelementen und Dialogfeldern finden Sie unter [Steuerelement Klassen](../mfc/control-classes.md), [Dialog Feld Klassen](../mfc/dialog-box-classes.md)und Stile der Bild Lauf [Leiste](../mfc/reference/styles-used-by-mfc.md#scroll-bar-styles).

Die Standard Steuerelemente, die in der **Toolbox** mit Standard Ereignissen verfügbar sind, lauten:

|Steuerelementname|Standard Ereignis|
|---|---|
|[Button-Steuerelement](../mfc/reference/cbutton-class.md)|BN_CLICKED|
|[Kontrollkästchen-Steuerelement](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[Kombinations Feld-Steuerelement](../mfc/reference/ccombobox-class.md)|CBN_SELCHANGE|
|[Steuerelement bearbeiten](../mfc/reference/cedit-class.md)|EN_CHANGE|
|Gruppenfeld|(–)|
|[Listenfeld-Steuerelement](../mfc/reference/clistbox-class.md)|LBN_SELCHANGE|
|[Optionsfeld-Steuerelement](../mfc/reference/styles-used-by-mfc.md#button-styles)|BN_CLICKED|
|[Statisches Text Steuerelement](../mfc/reference/cstatic-class.md)|(–)|
|[Bild-Steuerelement](../mfc/reference/cpictureholder-class.md)|(–)|
|[Rich Edit 2,0-Steuerelement](../mfc/using-cricheditctrl.md)|EN_CHANGE|
|[ScrollBar-Steuerelement](../mfc/reference/cscrollbar-class.md)|NM_THEMECHANGED|

> [!NOTE]
> Weitere Informationen zur Verwendung des **RichEdit 1,0** -Steuer Elements mit MFC finden Sie unter [Verwenden des RichEdit 1,0-Steuer Elements mit MFC](../windows/using-the-richedit-1-0-control-with-mfc.md) und [Beispielen für Rich-Edit-Steuer](../mfc/rich-edit-control-examples.md)Elemente.

Die [allgemeinen Windows](../mfc/controls-mfc.md) -Steuerelemente, die in der **Toolbox** verfügbar sind, um mehr Funktionalität bereitzustellen:

|Steuerelementname|Standard Ereignis|
|---|---|
|[Slider-Steuerelement](../mfc/slider-control-styles.md)|NM_CUSTOMDRAW|
|[Dreh Steuerelement](../mfc/using-cspinbuttonctrl.md)|UDN_DELTAPOS|
|[Fortschrittskontrolle](../mfc/styles-for-the-progress-control.md)|NM_CUSTOMDRAW|
|[Hot Key-Steuerelement](../mfc/using-a-hot-key-control.md)|NM_OUTOFMEMORY|
|[Listen Steuerelement](../mfc/list-control-and-list-view.md)|LVN_ITEMCHANGE|
|[Tree-Steuerelement](../mfc/tree-control-styles.md)|TVN_SELCHANGE|
|[Register Steuerelement](../mfc/tab-controls-and-property-sheets.md)|TCN_SELCHANGE|
|[Animations Steuerelement](../mfc/using-an-animation-control.md)|ACN_START|
|[Steuerelement für Datums-und Uhrzeit](../mfc/creating-the-date-and-time-picker-control.md)|DTN_DATETIMECHANGE|
|[Monatskalender-Steuerelement](../mfc/month-calendar-control-examples.md)|MCN_SELCHANGE|
|[IP-Adress Steuerung](../mfc/reference/cipaddressctrl-class.md)|IPN_FIELDCHANGED|
|[Erweitertes Kombinations Feld-Steuerelement](../mfc/creating-an-extended-combo-box-control.md)||
|Benutzerdefiniertes Steuerelement|TTN_GETDISPINFO|

## <a name="custom-controls"></a>Benutzerdefinierte Steuerelemente

Mit dem **Dialog-Editor** können Sie vorhandene benutzerdefinierte Steuerelemente oder Benutzer Steuerelemente in einer Dialog Feld Vorlage verwenden.

> [!NOTE]
> Benutzerdefinierte Steuerelemente in diesem Sinne sollten nicht mit ActiveX-Steuerelementen verwechselt werden. ActiveX-Steuerelemente wurden mitunter als benutzerdefinierte OLE-Steuerelemente bezeichnet Außerdem sollten Sie diese Steuerelemente nicht mit den vom Besitzer gezeichneten Steuerelementen in Windows verwechseln.

Diese Funktion soll es Ihnen ermöglichen, andere Steuerelemente als die von Windows bereitgestellten zu verwenden. Zur Laufzeit wird das Steuerelement einer Fenster Klasse (nicht der gleichen C++ Klasse) zugeordnet. Eine allgemeinere Methode, dieselbe Aufgabe auszuführen, besteht darin, ein beliebiges Steuerelement, z. b. ein statisches Steuerelement, in Ihrem Dialogfeld zu installieren. Entfernen Sie dann zur Laufzeit in der [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) -Funktion das Steuerelement, und ersetzen Sie es durch ihr eigenes benutzerdefiniertes Steuerelement.

> [!NOTE]
> Dies ist eine alte Technik. Heutzutage empfiehlt es sich in den meisten Fällen, ein ActiveX-Steuerelement oder eine Unterklasse mit einem allgemeinen Windows-Steuerelement zu schreiben.

Für diese benutzerdefinierten Steuerelemente sind Sie auf Folgendes beschränkt:

- Festlegen der Position im Dialogfeld.

- Eingeben einer Beschriftung.

- Identifizieren des Namens der Windows-Klasse des Steuer Elements, da der Anwendungscode das Steuerelement mit diesem Namen registrieren muss.

- Eingeben eines 32-Bit-hexadezimal Werts, der den Stil des Steuer Elements festlegt.

- Festlegen des erweiterten Stils.

## <a name="requirements"></a>Requirements (Anforderungen)

Win32

## <a name="see-also"></a>Weitere Informationen

[Dialog-Editor](../windows/dialog-editor.md)

<!--
[Adding Event Handlers for Dialog Box Controls](../windows/adding-event-handlers-for-dialog-box-controls.md)<br/>
[Dialog Box Controls and Variable Types](../ide/dialog-box-controls-and-variable-types.md)<br/>
[Controls](../mfc/controls-mfc.md)<br/>-->
