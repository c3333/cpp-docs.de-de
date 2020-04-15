---
title: Meldungszuordnungen (MFC)
ms.date: 09/07/2019
helpviewer_keywords:
- message maps [MFC], MFC
- Windows messages [MFC], message maps
- messages [MFC], Windows
- MFC, messages
ms.assetid: 3f9855e4-9d7d-4b64-8f3f-a19ea3cf79ba
ms.openlocfilehash: 8080becf1a1a153322bfd03cbd7006eaf2ce4e13
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356574"
---
# <a name="message-maps-mfc"></a>Meldungszuordnungen (MFC)

Dieser Abschnitt des Verweises listet alle [Nachrichtenzuordnungsmakros](../../mfc/reference/message-map-macros-mfc.md) und alle CWnd-Meldungszuordnungseinträge zusammen mit den entsprechenden Memberfunktionsprototypen auf: [CWnd](../../mfc/reference/cwnd-class.md)

|Category|BESCHREIBUNG|
|--------------|-----------------|
|ON\_COMMAND-Nachrichtenhandler|Behandelt `WM_COMMAND` Nachrichten, die von Benutzermenüauswahlen oder Menüzugriffstasten generiert werden.|
|[Meldungshandler für Benachrichtigungen von untergeordneten Fenstern](../../mfc/reference/child-window-notification-message-handlers.md)|Verarbeiten Benachrichtigungen von untergeordneten Fenstern.|
|[WM_ Nachrichtenhandler](../../mfc/reference/handlers-for-wm-messages.md)|Behandeln `WM_` sie Nachrichten, z. `WM_PAINT`B. .|
|[Benutzerdefinierte Meldungshandler](../../mfc/reference/user-defined-handlers.md)|Verarbeiten benutzerdefinierte Meldungen.|

(Eine Erläuterung der in diesem Verweis verwendeten Terminologie und Konventionen finden Sie unter [Verwenden des Nachrichtenzuordnungsquerverweises](../../mfc/reference/how-to-use-the-message-map-cross-reference.md).)

Da Windows ein meldungsorientiertes Betriebssystem ist, bezieht sich ein Großteil der Programmierung für die Windows-Umgebung auf die Verarbeitung von Meldungen. Bei jeder Tastatureingabe bzw. jedem Mausklick wird eine Meldung an die Anwendung gesendet, die das Ereignis dann verarbeiten muss.

Microsoft Foundation Class-Bibliothek bietet ein Programmiermodell, das für die meldungsbasierte Programmierung optimiert wurde. In diesem Modell wird mithilfe von "Meldungszuordnungen" festgelegt, welche Funktionen die verschiedenen Meldungen für eine bestimmte Klasse verarbeiten. Meldungszuordnungen enthalten ein oder mehrere Makros, die angeben, welche Meldungen von welchen Funktionen verarbeitet werden. Eine Meldungszuordnung, die ein `ON_COMMAND`-Makro enthält, kann z. B. wie folgt aussehen:

[!code-cpp[NVC_MFCMessageMaps#16](../../mfc/reference/codesnippet/cpp/message-maps-mfc_1.cpp)]

Das `ON_COMMAND`-Makro wird zur Verarbeitung von Befehlsmeldungen verwendet, die von Menüs, Schaltflächen und Zugriffstasten generiert werden. [Makros](../../mfc/reference/message-map-macros-mfc.md) sind verfügbar, um Folgendes zu zuordnen:

## <a name="windows-messages"></a>Windows-Meldungen

- Steuerelementbenachrichtigungen

- Benutzerdefinierte Meldungen

## <a name="command-messages"></a>Befehlsmeldungen

- Registrierte benutzerdefinierte Meldungen

- Meldungen zur Benutzeroberflächen-Aktualisierung

## <a name="ranges-of-messages"></a>Meldungsbereiche

- Befehle

- Aktualisierungshandlermeldungen

- Steuerelementbenachrichtigungen

Meldungszuordnungsmakros sind zwar wichtig, Sie müssen sie im Allgemeinen jedoch nicht direkt verwenden. Dies liegt daran, dass der [Klassen-Assistent](mfc-class-wizard.md) automatisch Nachrichtenzuordnungseinträge in Ihren Quelldateien erstellt, wenn Sie damit Nachrichtenverarbeitungsfunktionen zuordnen. Jedes Mal, wenn Sie einen Nachrichtenzuordnungseintrag bearbeiten oder hinzufügen möchten, können Sie den Klassen-Assistenten verwenden.

> [!NOTE]
> Der Klassen-Assistent unterstützt keine Nachrichtenzuordnungsbereiche. Sie müssen diese Meldungszuordnungseinträge selbst schreiben.

Meldungszuordnungen sind jedoch ein wichtiger Teil der Microsoft Foundation Class-Bibliothek, und Sie sollten ihre Funktionsweise kennen. Weitere Informationen finden Sie in der zur Verfügung stehenden Dokumentation.

## <a name="see-also"></a>Siehe auch

[Strukturen, Stile, Rückrufe und Meldungszuordnungen](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)
