---
title: Behandeln von Kommentaren in einem Dokument
ms.date: 11/04/2016
helpviewer_keywords:
- message maps [MFC], in document class
- command handling [MFC]
- documents [MFC], message maps
- message handling [MFC], WM_COMMAND messages
- command handling [MFC], commands in documents
- documents [MFC], handling messages in
ms.assetid: c7375584-27af-4275-b2fd-afea476785d0
ms.openlocfilehash: ed2ef635437408cacfd600d6cdba4b3731d575b4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625741"
---
# <a name="handling-commands-in-the-document"></a>Behandeln von Kommentaren in einem Dokument

Die Dokument Klasse kann auch bestimmte Befehle verarbeiten, die von Menü Elementen, Symbolleisten-Schaltflächen oder Zugriffstasten generiert werden. Standardmäßig `CDocument` verarbeitet die Befehle "Speichern" und "Speichern unter" im Menü "Datei" mithilfe der Serialisierung. Andere Befehle, die sich auf die Daten auswirken, können auch von den Element Funktionen Ihres Dokuments behandelt werden. Beispielsweise stellt die-Klasse im Scribble-Programm `CScribDoc` einen Handler für den Befehl "Alle löschen" bereit, mit dem alle derzeit im Dokument gespeicherten Daten gelöscht werden. Dokumente können über Meldungs Zuordnungen verfügen, aber im Gegensatz zu Ansichten können Dokumente standardmäßige Windows-Meldungen nicht verarbeiten – nur **WM_COMMAND** -Nachrichten oder "Befehle".

## <a name="see-also"></a>Siehe auch

[Verwenden von Dokumenten](using-documents.md)
