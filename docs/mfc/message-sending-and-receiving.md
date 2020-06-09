---
title: Senden und Empfangen von Meldungen
ms.date: 11/04/2016
helpviewer_keywords:
- Windows messages [MFC], handling in MFC
- control-notification messages [MFC]
- messages [MFC], receiving
- messages [MFC], MFC
- MFC, messages
- messages [MFC], sending
ms.assetid: 9ce189cb-b259-4c3b-b6f2-9cfbed18b98b
ms.openlocfilehash: 4da2fce68c1b6fd3827bc8b5d2a40dea5e5f117c
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626173"
---
# <a name="message-sending-and-receiving"></a>Senden und Empfangen von Meldungen

Beachten Sie den sendenden Teil des Prozesses und die Reaktion des Frameworks.

Die meisten Nachrichten ergeben sich aus der Benutzerinteraktion mit dem Programm. Befehle werden mit Mausklicks in Menü Elementen oder Symbolleisten Schaltflächen oder durch Tastenkombinationen für Tastenkombinationen generiert. Der Benutzer generiert außerdem Windows-Meldungen, z. b. das Verschieben oder Ändern der Größe eines Fensters. Andere Windows-Meldungen werden gesendet, wenn Ereignisse wie das Starten oder Beenden von Programmen auftreten, während Windows den Fokus erhält oder verliert. Steuerelement-Benachrichtigungs Meldungen werden mit Mausklicks oder anderen Benutzerinteraktionen mit einem-Steuerelement generiert, z. b. eine Schaltfläche oder ein Listenfeld-Steuerelement in einem Dialogfeld.

Die `Run` Member-Funktion der-Klasse `CWinApp` Ruft Nachrichten ab und sendet Sie an das entsprechende Fenster. Die meisten Befehls Meldungen werden an das Hauptrahmen Fenster der Anwendung gesendet. Der `WindowProc` vordefinierte von der Klassenbibliothek Ruft die Nachrichten ab und leitet Sie abhängig von der Kategorie der empfangenen Nachricht unterschiedlich weiter.

Beachten Sie nun den empfangenden Teil des Prozesses.

Der erste Empfänger einer Nachricht muss ein Fenster Objekt sein. Windows-Meldungen werden normalerweise direkt von diesem Fenster Objekt verarbeitet. Befehls Meldungen, die normalerweise aus dem Hauptrahmen Fenster der Anwendung stammen, werden an die Befehls Ziel Kette weitergeleitet, die unter [Befehls Routing](command-routing.md)beschrieben wird.

Jedes Objekt, das Nachrichten oder Befehle empfangen können soll, verfügt über eine eigene Meldungs Zuordnung, die eine Nachricht oder einen Befehl mit dem Namen des zugehörigen Handlers verbindet.

Wenn ein Befehls Zielobjekt eine Nachricht oder einen Befehl empfängt, durchsucht es seine Meldungs Zuordnung nach einer Entsprechung. Wenn ein Handler für die Nachricht gefunden wird, wird der-Handler aufgerufen. Weitere Informationen zur Suche nach Nachrichten Zuordnungen finden Sie unter [wie das Framework](how-the-framework-searches-message-maps.md)Meldungs Zuordnungen durchsucht. Verweisen Sie erneut auf die Figure- [Befehle im Framework](user-interface-objects-and-command-ids.md).

## <a name="see-also"></a>Siehe auch

[So ruft das Framework einen Handler auf](how-the-framework-calls-a-handler.md)
