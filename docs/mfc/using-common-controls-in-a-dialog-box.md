---
title: Verwenden von Standardsteuerelementen in einem Dialogfeld
ms.date: 11/04/2016
helpviewer_keywords:
- common controls [MFC], in dialog boxes
- dialog box controls [MFC], common controls
- Windows common controls [MFC], in dialog boxes
ms.assetid: 17713caf-09f8-484a-bf54-5f48bf09cce9
ms.openlocfilehash: 1a3dcb7151952b52affcfeb838ced15f0d116fce
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500342"
---
# <a name="using-common-controls-in-a-dialog-box"></a>Verwenden von Standardsteuerelementen in einem Dialogfeld

Die allgemeinen Windows-Steuerelemente können in [Dialogfeldern](../mfc/dialog-boxes.md), Formular Ansichten, Daten Satz Ansichten und beliebigen anderen Fenstern basierend auf einer Dialogfeld Vorlage verwendet werden. Das folgende Verfahren, mit geringfügigen Änderungen, funktioniert auch für Formulare.

## <a name="procedures"></a>Prozeduren

#### <a name="to-use-a-common-control-in-a-dialog-box"></a>So verwenden Sie ein gemeinsames Steuerelement in einem Dialogfeld

1. Platzieren Sie das Steuerelement [mit dem Dialog-Editor](../mfc/using-the-dialog-editor-to-add-controls.md)in der Dialogfeld Vorlage.

1. Fügen Sie der Dialogfeld Klasse eine Member-Variable hinzu, die das Steuerelement darstellt. Aktivieren Sie im Dialogfeld Element **Variable hinzufügen** die **Kontroll Variable** , und stellen Sie sicher, dass das **Steuer** Element für die **Kategorie**ausgewählt ist.

1. Wenn dieses allgemeine Steuerelement Eingaben für das Programm bereitstellt, deklarieren Sie zusätzliche Element Variablen in der Dialogfeld Klasse, um diese Eingabewerte zu verarbeiten.

    > [!NOTE]
    >  Sie können diese Element Variablen mithilfe des Kontextmenüs in Klassenansicht hinzufügen (Weitere Informationen finden Sie unter [Hinzufügen einer Element Variablen](../ide/adding-a-member-variable-visual-cpp.md)).

1. Legen Sie in [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) für die Dialogfeld Klasse die Anfangsbedingungen für das allgemeine Steuerelement fest. Verwenden Sie die im vorherigen Schritt erstellte Member-Variable, und legen Sie den Anfangswert und andere Einstellungen mithilfe der-Element Funktionen fest. Ausführliche Informationen zu den Einstellungen finden Sie in den folgenden Beschreibungen der Steuerelemente.

   Sie können auch den [Dialog Datenaustausch](../mfc/dialog-data-exchange-and-validation.md) (DDX) verwenden, um Steuerelemente in einem Dialogfeld zu initialisieren.

1. Verwenden Sie in Handler für Steuerelemente im Dialogfeld die Member-Variable, um das Steuerelement zu bearbeiten. Ausführliche Informationen zu-Methoden finden Sie in den folgenden Beschreibungen der-Steuerelemente.

    > [!NOTE]
    >  Die Element Variable ist nur so lange vorhanden, wie das Dialogfeld selbst vorhanden ist. Nachdem das Dialogfeld geschlossen wurde, können Sie das Steuerelement nicht mehr nach Eingabe Werten Abfragen. Um mit Eingabe Werten von einem allgemeinen Steuerelement zu arbeiten, überschreiben `OnOK` Sie in der Dialogfeld Klasse. Fragen Sie in der außer Kraft Setzung das Steuerelement nach Eingabe Werten ab, und speichern Sie diese Werte in den Element Variablen der Dialogfeld Klasse.

    > [!NOTE]
    >  Sie können auch den Dialogfeld Datenaustausch verwenden, um Werte aus den Steuerelementen in einem Dialogfeld festzulegen oder abzurufen.

## <a name="remarks"></a>Bemerkungen

Das Hinzufügen einiger allgemeiner Steuerelemente zu einem Dialogfeld führt dazu, dass das Dialogfeld nicht mehr funktionsfähig ist. Weitere Informationen zur Behandlung dieser Situation finden Sie unter [Hinzufügen von Steuerelementen zu einem Dialog](../windows/adding-editing-or-deleting-controls.md) Feld.

## <a name="what-do-you-want-to-do"></a>Was möchten Sie tun?

- [Manuelles Hinzufügen von Steuerelementen zu einem Dialogfeld anstelle von mit dem Dialog-Editor](../mfc/adding-controls-by-hand.md)

- [Ableiten von Steuerelementen von einem der standardmäßigen allgemeinen Windows-Steuerelemente](../mfc/deriving-controls-from-a-standard-control.md)

- [Verwenden eines allgemeinen Steuer Elements als untergeordnetes Fenster](../mfc/using-a-common-control-as-a-child-window.md)

- [Empfangen von Benachrichtigungs Meldungen von einem Steuerelement](../mfc/receiving-notification-from-common-controls.md)

- [Verwenden von Dialog Datenaustausch (DDX)](../mfc/dialog-data-exchange-and-validation.md)

## <a name="see-also"></a>Weitere Informationen

[Erstellen und Verwenden von Steuerelementen](../mfc/making-and-using-controls.md)<br/>
[Steuerelemente](../mfc/controls-mfc.md)
