---
title: Erstellen der Dialogfeldressource
ms.date: 11/04/2016
helpviewer_keywords:
- dialog resources
- MFC dialog boxes [MFC], creating
- dialog templates [MFC], creating dialog resource
- templates [MFC], creating
- resources [MFC], creating dialog boxes
- MFC dialog boxes [MFC], dialog resource
ms.assetid: 0b83bd33-14d3-4611-8129-fccdae18053e
ms.openlocfilehash: efaef11cfdc036a201ced3357ca81b37a5dc29db
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619623"
---
# <a name="creating-the-dialog-resource"></a>Erstellen der Dialogfeldressource

Um das [Dialogfeld](dialog-boxes.md) zu entwerfen und die Dialogfeld Ressource zu erstellen, verwenden Sie den [Dialog-Editor](../windows/dialog-editor.md). Im Dialog-Editor können Sie folgende Aktionen ausführen:

- Passen Sie die Größe und den Speicherort des Dialog Felds an, wenn es angezeigt wird.

- Ziehen Sie verschiedene Arten von Steuerelementen aus einer Palette von Steuerelementen, und legen Sie Sie dort ab, wo Sie Sie im Dialogfeld möchten.

- Positionieren Sie die Steuerelemente auf der Symbolleiste mit den Schaltflächen Ausrichtung.

- Testen Sie das Dialogfeld, indem Sie die Darstellung und das Verhalten des Programms simulieren. Im Testmodus können Sie die Steuerelemente des Dialog Felds bearbeiten, indem Sie Text in Textfelder eingeben, auf Pushbuttons klicken usw.

Wenn Sie fertig sind, wird Ihre Dialogfeld Vorlagen-Ressource in der Ressourcen Skriptdatei Ihrer Anwendung gespeichert. Sie können Sie später bei Bedarf bearbeiten. Eine vollständige Beschreibung der Erstellung und Bearbeitung von Dialogfeld Ressourcen finden Sie in den Themen des [Dialog-Editors](../windows/dialog-editor.md) . Diese Technik wird auch zum Erstellen der Dialogfeld Vorlagen-Ressourcen für [CFormView](reference/cformview-class.md) -und [CRecordView](reference/crecordview-class.md) -Klassen verwendet.

Wenn die Darstellung des Dialog Felds für Sie geeignet ist, erstellen Sie eine Dialogfeld Klasse, und ordnen Sie Ihre Nachrichten zu, wie unter [Erstellen einer Dialogfeld Klasse mit Code-Assistenten](creating-a-dialog-class-with-code-wizards.md)erläutert.

## <a name="see-also"></a>Siehe auch

[Dialog Felder](dialog-boxes.md)<br/>
[Arbeiten mit Dialogfeldern in MFC](life-cycle-of-a-dialog-box.md)
