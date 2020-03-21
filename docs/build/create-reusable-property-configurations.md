---
title: Freigeben oder wieder verwenden von Visual Studio-Projekteinstellungen-C++
ms.date: 07/17/2019
helpviewer_keywords:
- project properties [C++], reusable
ms.openlocfilehash: 451e22997f81753abf0c8d55d3b9e8d097cc6d5d
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078702"
---
# <a name="share-or-reuse-visual-studio-project-settings"></a>Freigeben oder Wiederverwenden von Visual Studio-Projekteinstellungen

Um eine benutzerdefinierte Gruppe von Einstellungen zu erstellen, die Sie für andere Benutzer freigeben oder in mehreren Projekten wieder verwenden können, verwenden Sie **Eigenschaften-Manager** , um ein *Eigenschaften Blatt* (.-Eigenschaften Datei) zu erstellen, um die Einstellungen für jede Art von Projekt zu speichern, die Sie wieder verwenden oder für andere Benutzer freigeben möchten. Die Verwendung von Eigenschaften Blättern ist weitaus weniger fehleranfällig als andere Möglichkeiten zum Erstellen von "globalen" Einstellungen.

> [!IMPORTANT]
> **USER-Dateien und mit ihnen verbundene Schwierigkeiten**
>
> In früheren Versionen von Visual Studio wurden globale Eigenschaftenblätter mit der USER-Erweiterung verwendet. Diese befanden sich in dem Ordner \<Benutzerprofil>\AppData\Local\Microsoft\MSBuild\v4.0\. Diese Dateien werden nicht mehr empfohlen, da sie Eigenschaften für Projektkonfigurationen pro Benutzer pro Computer festlegen. Solche "globalen" Einstellungen können Builds beeinträchtigen, insbesondere wenn Sie mehr als eine Zielplattform auf dem Buildcomputer verwenden. Wenn Sie beispielsweise ein MFC-Projekt und ein Windows Phone-Projekt haben, wären die USER-Eigenschaften für eines von ihnen ungültig. Wiederverwendbare Eigenschaftenblätter sind flexibler und stabiler.
>
> USER-Dateien werden noch von Visual Studio installiert und nehmen an der Eigenschaftenvererbung teil, sie sind jedoch standardmäßig leer. Die empfohlene Vorgehensweise besteht darin, den Verweis auf diese Dateien im **Eigenschaften-Manager** zu löschen, um sicherzustellen, dass die Projekte unabhängig von den benutzer- und computerbezogenen Einstellungen funktionieren. Das ist wichtig, um das richtige Verhalten in einer SCC-Umgebung (Quellcodeverwaltung) zu gewährleisten.

Um **Eigenschaften-Manager**anzuzeigen, wählen Sie in der Menüleiste **anzeigen** > **Eigenschaften-Manager** oder **anzeigen** > **anderen Windows** > **Eigenschaften-Manager**, abhängig von den Einstellungen.

Wenn Sie allgemeine, häufig verwendete Eigenschaften haben, die Sie in mehreren Projekten verwenden möchten, können Sie diese über den **Eigenschaften-Manager** in einer wiederverwendbaren *Eigenschaftenblattdatei* erfassen, deren Erweiterung gemäß der Konvention „.props“ lautet. Sie können das Blatt (oder die Blätter) auf neue Projekte anwenden, sodass Sie dessen Eigenschaften nicht von Grund auf neu festlegen müssen.

![Eigenschaften-Manager Kontextmenü](media/sharingnew.png "Sharingnew")

Unter jedem Konfigurationsknoten werden Knoten für jedes Eigenschaftenblatt angezeigt, das für diese Konfiguration gilt. Das System fügt Eigenschaftenblätter, die Werte festlegen, basierend auf den Optionen fest, die Sie im App-Wizard beim Erstellen des Projekts auswählen. Klicken Sie mit der rechten Maustaste auf einen beliebigen Knoten, und wählen Sie „Eigenschaften“ aus, um anzuzeigen, welche Eigenschaften für diesen Knoten gelten. Sämtliche Eigenschaftenblätter werden automatisch in das „Haupteigenschaftenblatt“ des Projekts (ms.cpp.props) importiert und in der Reihenfolge ausgewertet, in der sie im Eigenschaften-Manager angezeigt werden. Sie können sie verschieben, um die Reihenfolge der Auswertung zu ändern. Eigenschaftenblätter, die später ausgewertet werden, überschreiben die Werte der zuvor ausgewerteten Blätter. Weitere Informationen zur Reihenfolge der Auswertung in der vcxproj-Datei, zu den.-Eigenschaften und Targets-Dateien, Umgebungsvariablen und der Befehlszeile finden Sie unter [Vererbung von Projekteigenschaften](project-property-inheritance.md) .

Wenn Sie auf **Neues Projekteigenschaftenblatt hinzufügen** klicken und dann beispielsweise das Eigenschaftenblatt „MyProps.props“ auswählen, wird das Dialogfeld „Eigenschaftenseiten“ geöffnet. Beachten Sie, dass es für das MyProps-Eigenschaftenblatt gilt. Alle Änderungen, die Sie vornehmen, werden in das Blatt und nicht in die Projektdatei (VCXPROJ) geschrieben.

Eigenschaften in einem Eigenschaftenblatt werden überschrieben, wenn die gleiche Eigenschaft direkt in der VCXPROJ-Datei festgelegt ist.

Sie können ein Eigenschaftenblatt so oft wie nötig importieren. Mehrere Projekte in einer Projektmappe können Einstellungen aus demselben Eigenschaftenblatt erben, und ein Projekt kann über mehrere Blätter verfügen. Eigenschaftenblätter selbst können Einstellungen von einem anderen Eigenschaftenblatt erben.

Sie können auch ein Eigenschaftenblatt für mehrere Konfigurationen erstellen. Erstellen Sie dazu ein Eigenschaftenblatt für jede Konfiguration, öffnen Sie das Kontextmenü einer Konfiguration, wählen Sie **Vorhandenes Eigenschaftenblatt hinzufügen** aus, und fügen Sie die anderen Blätter hinzu. Wenn Sie jedoch ein gemeinsames Eigenschaften Blatt verwenden, beachten Sie, dass es beim Festlegen einer Eigenschaft für alle Konfigurationen festgelegt wird, auf die das Blatt angewendet wird, und dass die IDE nicht anzeigt, welche Projekte oder anderen Eigenschaften Blätter von einem bestimmten Eigenschaften Blatt erben.

In großen Projektmappen mit zahlreichen Projekten kann es hilfreich sein, ein Eigenschaftenblatt auf Projektmappenebene zu erstellen. Wenn Sie der Projektmappe ein Projekt hinzufügen, fügen Sie über den **Eigenschaften-Manager** das Eigenschaftenblatt dem Projekt hinzu. Bei Bedarf können Sie auf Projektebene ein neues Eigenschaftenblatt hinzufügen, über das projektspezifische Werte festgelegt werden.

> [!IMPORTANT]
> Eine.-Eigenschaften Datei wird standardmäßig nicht an der Quell Code Verwaltung beteiligt, da Sie nicht als Projekt Element erstellt wird. Wenn Sie die Datei in die Quellcodeverwaltung aufnehmen möchten, können Sie sie manuell als Projektmappenelement hinzufügen.

#### <a name="to-create-a-property-sheet"></a>So erstellen Sie ein Eigenschaftenblatt

1. Wählen Sie in der Menüleiste > **Eigenschaften-Manager** **anzeigen oder** > **anderen Windows** - > **Eigenschaften-Manager** **anzeigen** aus. Der **Eigenschaften-Manager** wird geöffnet.

2. Um den Umfang des Eigenschaftenblatts zu definieren, wählen Sie das Element aus, auf das es angewendet wird. Dies kann eine bestimmte Konfiguration oder ein anderes Eigenschaftenblatt sein. Öffnen Sie das Kontextmenü für dieses Element, und wählen Sie **Neues Projekteigenschaftenblatt hinzufügen** aus. Geben Sie einen Namen und den Speicherort an.

3. Öffnen Sie im **Eigenschaften-Manager**das neue Eigenschaftenblatt, und legen Sie dann die Eigenschaften fest, die Sie einschließen möchten.
