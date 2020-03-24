---
title: Schwerwiegender Fehler C1092
ms.date: 11/04/2016
f1_keywords:
- C1092
helpviewer_keywords:
- C1092
ms.assetid: bcaa87f0-fbfc-4a33-844b-3b9f5d67f279
ms.openlocfilehash: af43ddb83e872762f720b156644e0d466957a8a7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203878"
---
# <a name="fatal-error-c1092"></a>Schwerwiegender Fehler C1092

Bearbeiten und Fortfahren unterstützt keine Änderungen an Datentypen. Build erforderlich

Seit dem letzten erfolgreichen Build wurde ein Datentyp geändert oder hinzugefügt.

- "Bearbeiten und Fortfahren" unterstützt keine Änderungen an vorhandenen Datentypen, einschließlich Klassen-, Struktur-oder Enumeration-Definitionen. Sie müssen das Debuggen abbrechen und die Anwendung erstellen.

- "Bearbeiten und Fortfahren" unterstützt das Hinzufügen neuer Datentypen nicht, wenn eine Programm Datenbankdatei (z. b. "VC*x*0. pdb" C++ , wobei " *x* " die Hauptversion von Visual verwendet) schreibgeschützt ist. Zum Hinzufügen von Datentypen muss der Compiler die PDB-Datei im Schreibmodus öffnen.

### <a name="to-remove-this-error-without-ending-the-current-debug-session"></a>So entfernen Sie diesen Fehler, ohne die aktuelle Debugsitzung zu beenden

1. Ändern Sie den Datentyp wieder in den Zustand, den er vor dem Fehler hatte.

1. Wählen Sie im Menü **Debuggen** den Befehl **Codeänderungen übernehmen**aus.

### <a name="to-remove-this-error-without-changing-your-source-code"></a>So entfernen Sie diesen Fehler, ohne den Quellcode zu ändern

1. Wählen Sie im Menü **Debuggen** die Option **Debuggen beenden**.

1. Wählen Sie im Menü **Erstellen** den Befehl **Erstellen**aus.

Weitere Informationen hierzu finden Sie unter [Unterstützte Codeänderungen](/visualstudio/debugger/supported-code-changes-cpp).
