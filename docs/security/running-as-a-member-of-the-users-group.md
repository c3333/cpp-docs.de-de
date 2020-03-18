---
title: Ausführen als Mitglied der Gruppe Benutzer
ms.date: 11/04/2016
helpviewer_keywords:
- Users Group [C++]
- security [C++], Users Group
- Windows accounts [C++]
- non administrator users [C++]
- user accounts [C++]
- administrator (not running as) [C++]
ms.assetid: e48a03ec-d345-49f6-809a-1a291eecbc81
ms.openlocfilehash: 117ef426950fc9aff5ae41e894f0d7ae898369cd
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445443"
---
# <a name="running-as-a-member-of-the-users-group"></a>Ausführen als Mitglied der Gruppe Benutzer

Dieses Thema zeigt, wie Sie durch Konfigurieren von Windows-Benutzerkonten als ein Mitglied der Gruppe Benutzer (im Gegensatz zur Gruppe Administratoren) die Sicherheit erhöhen und die Wahrscheinlichkeit einer Infektion mit bösartigem Code verringern.

## <a name="security-risks"></a>Sicherheitsrisiken

Eine Ausführung als Administrator macht ihr System anfällig für Sicherheitsangriffe, z. B. durch "Trojaner" oder "Pufferüberlauf". Schon das Besuchen einer Internetsite als Administrator kann dem System schaden, da von einer Internetsite heruntergeladener, bösartiger Code den Computer angreifen kann. Bei einem erfolgreichen Angriff erbt der Angreifer die Administratorrechte und kann anschließend z. B. alle Dateien löschen, die Festplatte formatieren oder ein neues Benutzerkonto mit Administratorzugriff erstellen.

## <a name="non-administrator-user-groups"></a>Benutzergruppen ohne Administratorrechte

Die von Entwicklern normalerweise verwendeten Windows-Benutzerkonten sollten entweder der Gruppe Benutzer oder der Gruppe Hauptbenutzer hinzugefügt werden. Entwickler sollten zusätzlich der Debuggergruppe hinzugefügt werden. Als Mitglied der Gruppe Benutzer können Sie Routineaufgaben ausführen, z. B. Programme ausführen und Internetsites besuchen, ohne dabei den Computer unnötigen Sicherheitsrisiken auszusetzen. Als Mitglied der Gruppe Hauptbenutzer können Sie darüber hinaus weitere Aufgaben ausführen, z. B. das Installieren von Anwendungen, die Installation eines Druckers und einen Großteil der Operationen der Systemsteuerung. Wenn Sie Verwaltungsaufgaben wie die Aktualisierung des Betriebssystems oder die Konfiguration von Systemparametern ausführen müssen, sollten Sie sich nur solange als Administrator anmelden, wie es für die Ausführung der Verwaltungsaufgabe erforderlich ist. Alternativ kann der Windows- **runas** -Befehl verwendet werden, um bestimmte Anwendungen mit administrativem Zugriff zu starten.

## <a name="exposing-customers-to-security-risks"></a>Sicherheitsrisiken für Kunden

Insbesondere für Entwickler ist es wichtig, nicht Mitglied der Gruppe Administratoren zu sein. Abgesehen vom Schutz der Entwicklungscomputer werden Entwickler auf diese Weise daran gehindert, unbeabsichtigt Anwendungscode zu schreiben, für dessen spätere Ausführung die Kunden Mitglieder der Gruppe Administratoren sein müssen. Wenn bei der Entwicklung Code eingeführt wird, der Administratorzugriff erfordert, schlägt die Ausführung des Codes zur Laufzeit fehl, und Sie werden in einer Warnung darauf hingewiesen, dass die Kunden für die Fortführung der Anwendung als Administratoren angemeldet sein müssen.

## <a name="code-that-requires-administrator-privileges"></a>Code, der Administratorrechte erfordert

Das Ausführen von bestimmtem Code erfordert Administratorzugriff. Nach Möglichkeit sollten Sie Alternativen für diesen Code finden. Beispiele für Codeoperationen, die Administratorzugriff erfordern:

- Schreiben in geschützte Bereiche des Dateisystems, z. B. in das Verzeichnis Windows oder das Verzeichnis Programme

- Schreiben in geschützte Bereiche der Registrierung, z. B. HKEY_LOCAL_MACHINE

- Installieren von Assemblys im globalen Assemblycache (GAC)

Im Allgemeinen sollten diese Aktionen auf Anwendungsinstallationsprogramme beschränkt werden. Auf diese Weise kann der Benutzer den Administratorstatus nur vorübergehend verwenden.

## <a name="debugging"></a>Debuggen

Sie können jede Anwendung, die Sie innerhalb von Visual Studio starten (systemeigen oder nicht verwaltet), als Benutzer ohne Administratorrechte debuggen, indem Sie Mitglied der Debuggergruppe werden. Dies schließt die Möglichkeit ein, sich an eine laufende Anwendung anzuhängen (mit dem Befehl An den Prozess anhängen). Für das Debuggen von systemeigenen oder verwalteten Anwendungen, die von einem anderen Benutzer gestartet wurden, müssen Sie hingegen Mitglied der Gruppe Administratoren sein.

## <a name="see-also"></a>Weitere Informationen

[Empfohlene Vorgehensweisen bezüglich der Sicherheit](security-best-practices-for-cpp.md)
