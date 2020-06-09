---
title: Wie das Framework Code aufruft
ms.date: 11/04/2016
helpviewer_keywords:
- control flow [MFC], MFC framework and your code
- events [MFC], command routing in MFC
- command routing [MFC], framework
- command handling [MFC], calling handlers and code in MFC
- events [MFC], event-driven programming
- MFC, calling code from
- MFC, calling code
- application-specific events [MFC]
- command routing [MFC], MFC
ms.assetid: 39e68189-a580-40d0-9e35-bf5cd24a8ecf
ms.openlocfilehash: 318ca9558d705ca483d41867a1fe2ad46c36666f
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622596"
---
# <a name="how-the-framework-calls-your-code"></a>Wie das Framework Code aufruft

Es ist wichtig, dass Sie die Beziehung zwischen dem Quellcode und dem Code im MFC-Framework verstehen. Wenn die Anwendung ausgeführt wird, befindet sich der größte Teil des Steuerungs Flusses im Code des Frameworks. Das Framework verwaltet die Nachrichten Schleife, die Nachrichten von Windows abruft, wenn der Benutzer Befehle auswählt und Daten in einer Ansicht bearbeitet. Ereignisse, die das Framework selbst verarbeiten kann, verlassen sich überhaupt nicht auf Ihren Code. Das Framework weiß z. b., wie Fenster geschlossen werden und wie die Anwendung als Reaktion auf Benutzer Befehle beendet wird. Beim Verarbeiten dieser Aufgaben verwendet das Framework Meldungs Handler und C++ Virtual Functions, um Ihnen die Möglichkeit zu bieten, auf diese Ereignisse zu reagieren. Der Code ist jedoch nicht in der Steuerung. Das Framework ist.

Das Framework ruft den Code für anwendungsspezifische Ereignisse auf. Wenn der Benutzer z. b. einen Menübefehl auswählt, leitet das Framework den Befehl entlang einer Sequenz von C++-Objekten weiter: der aktuellen Ansicht und dem Rahmen Fenster, dem Dokument, das der Ansicht zugeordnet ist, der Dokument Vorlage des Dokuments und dem Anwendungs Objekt. Wenn eines dieser Objekte den Befehl verarbeiten kann, erfolgt dies, indem die entsprechende nachrichtenhandlerfunktion aufgerufen wird. Bei einem beliebigen Befehl kann der aufgerufene Code Ihr oder das Framework sein.

Diese Anordnung ist einem Programmierer, der mit der herkömmlichen Programmierung für Windows oder ereignisgesteuerte Programmierung vertraut ist, etwas vertraut.

In verwandten Themen erfahren Sie, was das Framework tut, wenn es die Anwendung initialisiert und ausführt und dann bereinigt, wenn die Anwendung beendet wird. Sie werden auch verstehen, wo der von Ihnen geschriebene Code passt.

Weitere Informationen finden Sie unter [Class CWinApp: die Anwendungsklasse](cwinapp-the-application-class.md) und die [Dokumentvorlagen sowie der Erstellungs Vorgang für Dokumente und Ansichten](document-templates-and-the-document-view-creation-process.md).

## <a name="see-also"></a>Siehe auch

[Erstellen im Framework](building-on-the-framework.md)
