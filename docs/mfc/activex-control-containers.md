---
title: ActiveX-Steuerelementcontainer
ms.date: 09/12/2018
helpviewer_keywords:
- ActiveX control containers [MFC]
- OLE controls [MFC], containers
ms.assetid: 0eb1a713-e607-4c79-a0c7-67c5f1fd5fab
ms.openlocfilehash: 42fa18c41ebd960aa8de080df00556ad5c909d40
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620753"
---
# <a name="activex-control-containers"></a>ActiveX-Steuerelementcontainer

Ein ActiveX-Steuerelement Container ist ein Container, der ActiveX-Steuerelemente vollständig unterstützt und Sie in seine eigenen Fenster oder Dialogfelder integrieren kann. Ein ActiveX-Steuerelement ist ein wiederverwendbares Softwareelement, das Sie in vielen Entwicklungsprojekten verwenden können. Steuerelemente ermöglichen dem Benutzer der Anwendung den Zugriff auf Datenbanken, das Überwachen von Daten und das Treffen verschiedener Auswahlmöglichkeiten in Ihren Anwendungen. Weitere Informationen zu ActiveX-Steuerelementen finden Sie im Artikel [MFC-ActiveX](mfc-activex-controls.md)-Steuerelemente.

>[!IMPORTANT]
> ActiveX ist eine ältere Technologie, die nicht für die neue Entwicklung verwendet werden sollte. Weitere Informationen finden Sie unter [ActiveX](activex-controls.md)-Steuerelemente.

Steuerelement Container nehmen in der Regel zwei Formen in einem Projekt an:

- Dialogfelder und Dialogfelder, wie z. b. Formular Ansichten, bei denen ein ActiveX-Steuerelement an einer beliebigen Stelle im Dialogfeld verwendet wird.

- Fenster in einer Anwendung, in der ein ActiveX-Steuerelement in einer Symbolleiste oder an einer anderen Stelle im Benutzer Fenster verwendet wird.

Der ActiveX-Steuerelement Container interagiert mit dem-Steuerelement über verfügbar gemachte [Methoden](mfc-activex-controls-methods.md) und [Eigenschaften](mfc-activex-controls-properties.md). Auf diese Methoden und Eigenschaften, auf die der Steuerelement Container zugreifen und diese ändern kann, wird über eine Wrapper Klasse im Container Projekt des ActiveX-Steuer Elements zugegriffen. Das eingebettete ActiveX-Steuerelement kann auch mit dem Container interagieren, indem [Ereignisse](mfc-activex-controls-events.md) ausgelöst werden, um den Container zu benachrichtigen, dass eine Aktion aufgetreten ist. Der Steuerelement Container kann wählen, ob diese Benachrichtigungen ausgeführt werden sollen oder nicht.

In weiteren Artikeln werden verschiedene Themen erörtert, von der Erstellung eines ActiveX-Steuerelement Container Projekts bis zu grundlegenden Implementierungs Problemen im Zusammenhang mit ActiveX-Steuerelement Visual C++ Containern, die

- [Erstellen eines MFC-ActiveX-Steuerelement Containers](reference/creating-an-mfc-activex-control-container.md)

- [Container für ActiveX-Steuerelemente](containers-for-activex-controls.md)

- [ActiveX-Steuerelementcontainer: Manuelles Aktivieren von ActiveX-Steuerelementcontainern](activex-control-containers-manually-enabling-activex-control-containment.md)

- [ActiveX-Steuerelementcontainer: Einfügen eines Steuerelements in eine Steuerelementcontainer-Anwendung](inserting-a-control-into-a-control-container-application.md)

- [ActiveX-Steuerelementcontainer: Verbinden eines ActiveX-Steuerelements mit einer Membervariablen](activex-control-containers-connecting-an-activex-control-to-a-member-variable.md)

- [ActiveX-Steuerelement Container: Behandeln von Ereignissen aus einem ActiveX-Steuerelement](activex-control-containers-handling-events-from-an-activex-control.md)

- [ActiveX-Steuerelementcontainer: Anzeigen und Ändern von Steuerelementeigenschaften](activex-control-containers-viewing-and-modifying-control-properties.md)

- [ActiveX-Steuerelementcontainer: Programmieren von ActiveX-Steuerelementen in einem ActiveX-Steuerelementcontainer](programming-activex-controls-in-a-activex-control-container.md)

- [ActiveX-Steuerelementcontainer: Verwenden von Steuerelementen in Containern, die keine Dialogfelder sind](activex-control-containers-using-controls-in-a-non-dialog-container.md)

Weitere Informationen zum Verwenden von ActiveX-Steuerelementen in einem Dialogfeld finden Sie in den Themen des [Dialog-Editors](../windows/dialog-editor.md) .

Eine Liste der Artikel, in denen die Details der Entwicklung von ActiveX-Steuerelementen mithilfe Visual C++ und der MFC-ActiveX-Steuerelement Klassen erläutert werden, finden Sie unter [MFC](mfc-activex-controls.md) Die Artikel sind nach funktionalen Kategorien gruppiert.

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](mfc-activex-controls.md)
