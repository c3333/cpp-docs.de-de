---
title: Freigeben oder Wiederverwenden von Visual Studio-Projekteinstellungen - C++
ms.date: 07/17/2019
helpviewer_keywords:
- project properties [C++], reusable
ms.openlocfilehash: bcf54be0531c7150c1506eb6f5dda2b5bc95161f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328693"
---
# <a name="share-or-reuse-visual-studio-project-settings"></a>Freigeben oder Wiederverwenden von Visual Studio-Projekteinstellungen

Um eine benutzerdefinierte Gruppe von Einstellungen zu erstellen, die Sie für andere freigeben oder in mehreren Projekten wiederverwenden können, verwenden Sie **Property Manager,** um ein *Eigenschaftenblatt* (.props-Datei) zu erstellen, um die Einstellungen für jede Art von Projekt zu speichern, das Sie wiederverwenden oder für andere freigeben möchten. Die Verwendung von Eigenschaftenblättern ist weit weniger fehleranfällig als andere Möglichkeiten zum Erstellen von "globalen" Einstellungen.

> [!IMPORTANT]
> **USER-Dateien und mit ihnen verbundene Schwierigkeiten**
>
> In früheren Versionen von Visual Studio wurden globale Eigenschaftenblätter mit der USER-Erweiterung verwendet. Diese befanden sich in dem Ordner \<Benutzerprofil>\AppData\Local\Microsoft\MSBuild\v4.0\. Diese Dateien werden nicht mehr empfohlen, da sie Eigenschaften für Projektkonfigurationen pro Benutzer pro Computer festlegen. Solche "globalen" Einstellungen können Builds beeinträchtigen, insbesondere wenn Sie mehr als eine Zielplattform auf dem Buildcomputer verwenden. Wenn Sie beispielsweise ein MFC-Projekt und ein Windows Phone-Projekt haben, wären die USER-Eigenschaften für eines von ihnen ungültig. Wiederverwendbare Eigenschaftenblätter sind flexibler und stabiler.
>
> USER-Dateien werden noch von Visual Studio installiert und nehmen an der Eigenschaftenvererbung teil, sie sind jedoch standardmäßig leer. Die beste Methode besteht darin, den Verweis auf sie in **Property Manager** zu löschen, um sicherzustellen, dass Ihre Projekte unabhängig von benutzer- und computerfreundlichen Einstellungen ausgeführt werden.

Um **Property Manager**anzuzeigen, wählen Sie in der Menüleiste**Eigenschaften-Manager** **anzeigen** > oder andere**Windows-Eigenschaften-Manager****Other Windows** >  **anzeigen,** > je nach Ihren Einstellungen.

Wenn Sie über einen häufig verwendeten Satz von Eigenschaften verfügen, die Sie auf mehrere Projekte anwenden möchten, können Sie **property Manager** verwenden, um sie in einer wiederverwendbaren *Eigenschaftenblattdatei* zu erfassen, die konventionell über eine .props-Dateinamenerweiterung verfügt. Sie können das Blatt (oder die Blätter) auf neue Projekte anwenden, sodass Sie dessen Eigenschaften nicht von Grund auf neu festlegen müssen.

![Kontextmenü des Eigenschaften-Managers](media/sharingnew.png "TeilenNeu")

Unter jedem Konfigurationsknoten werden Knoten für jedes Eigenschaftenblatt angezeigt, das für diese Konfiguration gilt. Das System fügt Eigenschaftenblätter, die Werte festlegen, basierend auf den Optionen fest, die Sie im App-Wizard beim Erstellen des Projekts auswählen. Klicken Sie mit der rechten Maustaste auf einen beliebigen Knoten, und wählen Sie „Eigenschaften“ aus, um anzuzeigen, welche Eigenschaften für diesen Knoten gelten. Sämtliche Eigenschaftenblätter werden automatisch in das „Haupteigenschaftenblatt“ des Projekts (ms.cpp.props) importiert und in der Reihenfolge ausgewertet, in der sie im Eigenschaften-Manager angezeigt werden. Sie können sie verschieben, um die Reihenfolge der Auswertung zu ändern. Eigenschaftenblätter, die später ausgewertet werden, überschreiben die Werte der zuvor ausgewerteten Blätter. Weitere Informationen zur Auswertungsreihenfolge in der .vcxproj-Datei, den .props- und .targets-Dateien, Umgebungsvariablen und der Befehlszeile finden Sie unter [Project-Eigenschaftsvererbung.](project-property-inheritance.md)

Wenn Sie **Neues Projekteigenschaftenblatt hinzufügen** auswählen und dann z. B. das Eigenschaftenblatt MyProps.props auswählen, wird ein Dialogfeld auf der Eigenschaftenseite angezeigt. Beachten Sie, dass es für das MyProps-Eigenschaftenblatt gilt. Alle Änderungen, die Sie vornehmen, werden in das Blatt und nicht in die Projektdatei (VCXPROJ) geschrieben.

Eigenschaften in einem Eigenschaftenblatt werden überschrieben, wenn die gleiche Eigenschaft direkt in der VCXPROJ-Datei festgelegt ist.

Sie können ein Eigenschaftenblatt so oft wie nötig importieren. Mehrere Projekte in einer Projektmappe können Einstellungen aus demselben Eigenschaftenblatt erben, und ein Projekt kann über mehrere Blätter verfügen. Eigenschaftenblätter selbst können Einstellungen von einem anderen Eigenschaftenblatt erben.

Sie können auch ein Eigenschaftenblatt für mehrere Konfigurationen erstellen. Erstellen Sie dazu für jede Konfiguration ein Eigenschaftenblatt, öffnen Sie das Kontextmenü für eine dieser Konfigurationen, wählen **Vorhandene Eigenschaftenblätter**hinzufügen aus, und fügen Sie dann die anderen Blätter hinzu. Wenn Sie jedoch ein allgemeines Eigenschaftenblatt verwenden, beachten Sie, dass beim Festlegen einer Eigenschaft für alle Konfigurationen festgelegt wird, auf die das Blatt angewendet wird, und dass die IDE nicht anzeigt, welche Projekte oder andere Eigenschaftenblätter von einem bestimmten Eigenschaftenblatt erben.

In großen Projektmappen mit zahlreichen Projekten kann es hilfreich sein, ein Eigenschaftenblatt auf Projektmappenebene zu erstellen. Wenn Sie der Projektmappe ein Projekt hinzufügen, verwenden Sie **Property Manager,** um dieses Eigenschaftenblatt zum Projekt hinzuzufügen. Bei Bedarf können Sie auf Projektebene ein neues Eigenschaftenblatt hinzufügen, über das projektspezifische Werte festgelegt werden.

> [!IMPORTANT]
> Eine .props-Datei ist standardmäßig nicht an der Quellcodeverwaltung beteiligt, da sie nicht als Projektelement erstellt wird. Wenn Sie die Datei in die Quellcodeverwaltung aufnehmen möchten, können Sie sie manuell als Projektmappenelement hinzufügen.

#### <a name="to-create-a-property-sheet"></a>So erstellen Sie ein Eigenschaftenblatt

1. Wählen Sie in der Menüleiste **View** > **Eigenschaften-Manager** **anzeigen** > oder andere > **Windows-Eigenschaften-Manager**anzeigen .**Other Windows** Der **Property Manager** wird geöffnet.

2. Um den Umfang des Eigenschaftenblatts zu definieren, wählen Sie das Element aus, auf das es angewendet wird. Dies kann eine bestimmte Konfiguration oder ein anderes Eigenschaftenblatt sein. Öffnen Sie das Kontextmenü für dieses Element, und wählen Sie dann **Neues Projekteigenschaftenblatt hinzufügen**aus. Geben Sie einen Namen und den Speicherort an.

3. Öffnen Sie in **Property Manager**das neue Eigenschaftenblatt, und legen Sie dann die Eigenschaften fest, die Sie einschließen möchten.
