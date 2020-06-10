---
title: Verwalten von Menüs, Steuerleisten und Zugriffstasten
ms.date: 11/04/2016
helpviewer_keywords:
- MDI [MFC], frame windows
- control bars [MFC], updating in frame windows
- menus [MFC], updating as context changes
- user interface objects [MFC], updating
- accelerator tables [MFC]
- sharing menus [MFC]
- updating user-interface objects [MFC]
- frame windows [MFC], updating
- status bars [MFC], updating
ms.assetid: 97ca1997-06df-4373-b023-4f7ecd81047b
ms.openlocfilehash: 9945dc68ffd46bbf5e114a79467299e4b67e3659
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621330"
---
# <a name="managing-menus-control-bars-and-accelerators"></a>Verwalten von Menüs, Steuerleisten und Zugriffstasten

Das Rahmen Fenster verwaltet das Aktualisieren von Benutzeroberflächen Objekten, einschließlich Menüs, Symbolleisten-Schaltflächen, Statusleiste und Zugriffstasten. Außerdem wird die gemeinsame Nutzung der Menüleiste in MDI-Anwendungen verwaltet.

## <a name="managing-menus"></a>Verwalten von Menüs

Das Rahmen Fenster ist an der Aktualisierung von Benutzeroberflächen Elementen beteiligt, wobei der ON_UPDATE_COMMAND_UI Mechanismus verwendet wird, der in [Aktualisieren von Benutzeroberflächen Objekten](how-to-update-user-interface-objects.md)beschrieben wird. Schaltflächen auf Symbolleisten und anderen Steuer leisten werden während der Leerlauf Schleife aktualisiert. Menü Elemente in den Dropdown Menüs in der Menüleiste werden aktualisiert, kurz bevor das Menü ausfällt.

Für MDI-Anwendungen verwaltet das MDI-Rahmen Fenster die Menüleiste und die Beschriftung. Ein MDI-Rahmen Fenster besitzt ein Standardmenü, das als Menüleiste verwendet wird, wenn keine aktiven untergeordneten MDI-Fenster vorhanden sind. Wenn aktive untergeordnete Elemente vorhanden sind, wird die Menüleiste des MDI-Frame Fensters über das Menü des aktiven untergeordneten MDI-Fensters übernommen. Wenn eine MDI-Anwendung mehrere Dokumenttypen unterstützt, z. b. Diagramm-und Arbeitsblatt Dokumente, fügt jeder Typ seine eigenen Menüs in die Menüleiste ein und ändert die Beschriftung des Hauptrahmen Fensters.

[CMDIFrameWnd](reference/cmdiframewnd-class.md) stellt Standard Implementierungen für die Standard Befehle im Menü Fenster bereit, das für MDI-Anwendungen angezeigt wird. Insbesondere wird der neue Fenster Befehl (ID_WINDOW_NEW) implementiert, um ein neues Rahmen Fenster und eine Ansicht für das aktuelle Dokument zu erstellen. Sie müssen diese Implementierungen nur überschreiben, wenn Sie eine erweiterte Anpassung benötigen.

Mehrere untergeordnete MDI-Fenster desselben Dokument Typs Teilen Menü Ressourcen. Wenn mehrere untergeordnete MDI-Fenster von derselben Dokument Vorlage erstellt werden, können alle die gleiche Menü Ressource verwenden, die auf Systemressourcen in Windows gespeichert wird.

## <a name="managing-the-status-bar"></a>Verwalten der Status Leiste

Das Rahmen Fenster positioniert auch die Statusleiste innerhalb des Client Bereichs und verwaltet die Indikatoren der Statusleiste. Das Rahmen Fenster löscht und aktualisiert den Meldungs Bereich in der Statusleiste nach Bedarf und zeigt Eingabe Aufforderungs Zeichenfolgen an, wenn der Benutzermenü Elemente oder Symbolleisten Schaltflächen auswählt, wie in [Anzeigen von Befehls Informationen in der Statusleiste](how-to-display-command-information-in-the-status-bar.md)beschrieben.

## <a name="managing-accelerators"></a>Verwalten von Accelerators

Jedes Rahmen Fenster behält eine optionale Zugriffstasten Tabelle bei, die die Tastatur Zugriffstaste automatisch für Sie übernimmt. Dieser Mechanismus erleichtert das Definieren von Zugriffstasten (auch als Tastenkombinationen bezeichnet), die Menübefehle aufrufen.

## <a name="see-also"></a>Siehe auch

[Verwenden von Rahmenfenstern](using-frame-windows.md)
