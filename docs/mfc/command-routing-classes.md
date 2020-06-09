---
title: Klassen zur Befehlsweiterleitung
ms.date: 11/04/2016
f1_keywords:
- vc.classes.command
helpviewer_keywords:
- MFC, command routing
- command routing [MFC], classes
ms.assetid: 4b50e689-2c54-4e6c-90f0-37333e22b2a1
ms.openlocfilehash: d7ff275d373cf50ab8ebe52ed454bd25cd473e11
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624827"
---
# <a name="command-routing-classes"></a>Klassen zur Befehlsweiterleitung

Wenn der Benutzer mit der Anwendung interagiert, indem er Menüs oder Schaltflächen der Steuerleiste mit der Maus auswählt, sendet die Anwendung Nachrichten vom betroffenen Benutzeroberflächen Objekt an ein entsprechendes Befehls Zielobjekt. Die von abgeleiteten Befehls Ziel `CCmdTarget` Klassen [umfassen CWinApp](reference/cwinapp-class.md), [CWnd](reference/cwnd-class.md), [CDocTemplate](reference/cdoctemplate-class.md), [CDocument](reference/cdocument-class.md), [CView](reference/cview-class.md)und die von ihnen abgeleiteten Klassen. Das Framework unterstützt das automatische Befehls Routing, sodass Befehle vom am besten geeigneten Objekt verarbeitet werden können, das derzeit in der Anwendung aktiv ist.

Ein Objekt der Klasse `CCmdUI` wird an die Befehls Ziele der Befehlszeilenschnittstelle ([ON_UPDATE_COMMAND_UI](reference/message-map-macros-mfc.md#on_update_command_ui)) übermittelt, damit Sie den Status der Benutzeroberfläche für einen bestimmten Befehl aktualisieren können (beispielsweise, um die Überprüfung aus Menü Elementen zu überprüfen oder zu entfernen). Sie können Member-Funktionen des- `CCmdUI` Objekts zum Aktualisieren des Status des UI-Objekts aufzurufen. Dieser Vorgang ist unabhängig davon, ob es sich bei dem Benutzeroberflächen Objekt, das einem bestimmten Befehl zugeordnet ist, um ein Menü Element oder eine Schaltfläche handelt.

[CCmdTarget](reference/ccmdtarget-class.md)<br/>
Dient als Basisklasse für alle Klassen von Objekten, die Nachrichten empfangen und darauf reagieren können.

[CCmdUI](reference/ccmdui-class.md)<br/>
Stellt eine programmgesteuerte Schnittstelle zum Aktualisieren von Benutzeroberflächen Objekten, z. b. Menü Elemente oder Steuer leisten Schaltflächen, bereit. Das Befehls Zielobjekt aktiviert, deaktiviert, überprüft und/oder löscht das Benutzeroberflächen Objekt mit diesem-Objekt.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](class-library-overview.md)
