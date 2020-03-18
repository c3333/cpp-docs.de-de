---
title: Hinzufügen eines Ereignishandlers
ms.date: 11/12/2018
f1_keywords:
- vc.codewiz.eventhandler.overview
helpviewer_keywords:
- event handlers, adding
- properties [Visual Studio], MSBuild
- MSBuild, properties
- event handler wizard [C++]
ms.assetid: 050bebf0-a9e0-474b-905c-796fe5ac8fc3
ms.openlocfilehash: 0d852991c29281a7ecf912bd3d764d9916ef10f7
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447507"
---
# <a name="add-an-event-handler"></a>Hinzufügen eines Ereignishandlers

Sie können einen neuen Ereignishandler über den Ressourcen-Editor hinzufügen oder einen vorhandenen Ereignishandler mithilfe des [Ereignishandler-Assistenten](#event-handler-wizard) für ein Dialogfeld-Steuerelement bearbeiten.

Sie können der Klasse, die das Dialogfeld implementiert, mithilfe des [Eigenschaftenfensters](/visualstudio/ide/reference/properties-window) ein Ereignis hinzufügen. Wenn Sie das Ereignis einer anderen Klasse hinzufügen möchten, verwenden Sie den Ereignishandler-Assistenten.

**So fügen Sie einem Dialogfeld-Steuerelement einen Ereignishandler hinzu:**

1. Führen Sie einen Doppelklick auf die Dialogfeldressource in der [Ressourcenansicht](../windows/how-to-create-a-resource-script-file.md#create-resources) aus, um die Dialogfeldressource zu öffnen, die das Steuerelement im [Dialog-Editor](../windows/dialog-editor.md) enthält.

1. Klicken Sie mit der rechten Maustaste auf das Steuerelement aus, das das Benachrichtigungsereignis verarbeiten soll.

1. Klicken Sie im Kontextmenü auf **Ereignishandler hinzufügen**, um den Ereignishandler-Assistenten anzuzeigen.

1. Wählen Sie das Ereignis im Feld **Nachrichtentyp** aus, das der im Feld **Klassenliste** ausgewählten Klasse hinzugefügt werden soll.

1. Akzeptieren Sie den Standardnamen im Feld **Handlerfunktionsname**, oder geben Sie einen Namen Ihrer Wahl ein.

1. Klicken Sie auf **Hinzufügen und bearbeiten**, um den Ereignishandler dem Projekt hinzuzufügen und den Text-Editor bei der neuen Funktion zum Hinzufügen des entsprechenden Ereignishandlercodes zu öffnen.

   Wenn der ausgewählte Nachrichtentyp bereits über einen Ereignishandler für die ausgewählte Klasse verfügt, ist die Option **Hinzufügen und bearbeiten** nicht verfügbar, jedoch ist die Option **Code bearbeiten** verfügbar. Klicken Sie auf **Code bearbeiten**, um den Text-Editor bei der vorhandenen Funktion zu öffnen.

Alternativ können Sie Ereignishandler über das [Eigenschaftenfenster](/visualstudio/ide/reference/properties-window) hinzufügen. Weitere Informationen finden Sie unter [Adding Event Handlers for Dialog Box Controls (Hinzufügen von Ereignishandlern für Dialogfeld-Steuerelemente)](../windows/adding-event-handlers-for-dialog-box-controls.md).

## <a name="in-this-section"></a>In diesem Abschnitt

- [Ereignishandler-Assistent](#event-handler-wizard)

## <a name="event-handler-wizard"></a>Ereignishandler-Assistent

Dieser Assistent fügt einer beliebigen Klasse einen Ereignishandler für ein Dialogfeld-Steuerelement hinzu. Wenn Sie einen Ereignishandler über das [Eigenschaftenfenster](/visualstudio/ide/reference/properties-window) hinzufügen, können Sie ihn nur der Klasse hinzufügen, die das Dialogfeld implementiert. Weitere Informationen finden Sie unter [Adding Event Handlers for Dialog Box Controls (Hinzufügen von Ereignishandlern für Dialogfeld-Steuerelemente)](../windows/adding-event-handlers-for-dialog-box-controls.md).

- **Befehlsname**

  Identifiziert das ausgewählte Steuerelement, für das der Ereignishandler hinzugefügt wird. Dieses Feld ist nicht verfügbar.

- **Nachrichtentyp**

  Zeigt die Liste der aktuell verfügbaren Meldungshandler für das ausgewählte Steuerelement an.

- **Handlerfunktionsname**

  Zeigt den Namen der Funktion an, die zur Behandlung des Ereignisses hinzugefügt wird. Der Name basiert standardmäßig auf dem Nachrichtentyp und dem Befehl, und `On` wird vorangestellt. Beispielsweise zeigt der Nachrichtentyp `IDC_BUTTON1` für die Schaltfläche namens `BN_CLICKED` den Handlerfunktionsnamen `OnBnClickedButton1` an.

- **Klassenliste**

  Zeigt die verfügbaren Klassen an, denen Sie einen Ereignishandler hinzufügen können. Die Klasse für das ausgewählte Dialogfeld wird rot angezeigt.

- **Handlerbeschreibung**

  Gibt eine Beschreibung für das im Feld **Nachrichtentyp** ausgewählte Element an. Dieses Feld ist nicht verfügbar.

- **Hinzufügen und Bearbeiten**

  Fügt den Meldungshandler zu der ausgewählten Klasse oder dem ausgewählten Objekt hinzu. Öffnet außerdem den Text-Editor bei der neuen Funktion, damit Sie den Handlercode für Benachrichtigungen des Steuerelements hinzufügen oder bearbeiten können.

- **Code bearbeiten**

  Öffnet den Text-Editor bei der ausgewählten vorhandenen Funktion, damit Sie den Handlercode für Benachrichtigungen des Steuerelements hinzufügen oder bearbeiten können.
