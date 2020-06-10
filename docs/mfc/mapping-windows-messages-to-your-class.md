---
title: Zuordnen von Windows-Meldungen zu einer Klasse
ms.date: 09/06/2019
helpviewer_keywords:
- MFC dialog boxes [MFC], Windows messages
- message maps [MFC], in dialog class
- Windows messages [MFC], mapping in dialog classes
- messages to dialog class [MFC]
- mappings [MFC], messages to dialog class [MFC]
- message maps [MFC], mapping Windows messages to classes
- messages to dialog class [MFC], mapping
- Class Wizard [MFC]
ms.assetid: a4c6fd1f-1d33-47c9-baa0-001755746d6d
ms.openlocfilehash: 6b1155945c4248c5ac2755d60d8887f890e6d324
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618298"
---
# <a name="mapping-windows-messages-to-your-class"></a>Zuordnen von Windows-Meldungen zu einer Klasse

Wenn Sie das Dialogfeld zum Verarbeiten von Windows-Meldungen benötigen, überschreiben Sie die entsprechenden Handlerfunktionen. Wählen Sie hierzu in **Projektmappen-Explorer**die Registerkarte **Klassenansicht** aus, klicken Sie mit der rechten Maustaste auf die Klasse, die das Dialogfeld darstellt, und wählen Sie [Klassen-Assistent](reference/mfc-class-wizard.md)aus. Verwenden Sie den Assistenten, um [die Nachrichten](reference/mapping-messages-to-functions.md) der Dialogfeld Klasse zuzuordnen. Dadurch wird ein Meldungs Zuordnungs Eintrag für jede Nachricht geschrieben, und die Member der nachrichtenhandlermember werden der Klasse hinzugefügt. Verwenden Sie den Code-Editor, um Code in den Meldungs Handlern zu schreiben.

Sie können auch Member-Funktionen von [CDialog](reference/cdialog-class.md) und deren Basisklassen überschreiben, insbesondere [CWnd](reference/cwnd-class.md).

## <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- [Nachrichten Behandlung und-Zuordnung](message-handling-and-mapping.md)

- [Häufig überschriebene Element Funktionen](commonly-overridden-member-functions.md)

- [Häufig hinzugefügte Member-Funktionen](commonly-added-member-functions.md)

## <a name="see-also"></a>Siehe auch

[Dialog Felder](dialog-boxes.md)<br/>
[Arbeiten mit Dialogfeldern in MFC](life-cycle-of-a-dialog-box.md)
