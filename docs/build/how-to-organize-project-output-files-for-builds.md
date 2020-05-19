---
title: 'Vorgehensweise: Organisieren von Projektausgabedateien für Builds'
ms.date: 05/06/2019
helpviewer_keywords:
- C++, output files
- output files, organizing
ms.assetid: 521d95ea-2dcc-4da0-b5eb-ac3e57941446
ms.openlocfilehash: 13aa3d1f8e2993ca34163ecbc0515948db56eb79
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328527"
---
# <a name="how-to-organize-project-output-files-for-builds"></a>Vorgehensweise: Organisieren von Projektausgabedateien für Builds

In diesem Thema werden empfohlene Vorgehensweisen zum Organisieren von Projektausgabedateien beschrieben. Wenn Projektausgabedateien falsch eingerichtet werden, können Buildfehler auftreten. Außerdem werden in diesem Thema die Vor- und Nachteile der einzelnen Möglichkeiten zum Organisieren von Projektausgabedateien erörtert.

## <a name="referencing-clr-assemblies"></a>Verweisen auf CLR-Assemblys

#### <a name="to-reference-assemblies-with-using"></a>So verweisen Sie mit #using auf Assemblys

1. Sie können direkt aus dem Code heraus auf eine Assembly verweisen, indem Sie eine #using-Anweisung wie `#using <System.Data.dll>` verwenden. Weitere Information finden Sie unter [#using Directive (#using-Direktive)](../preprocessor/hash-using-directive-cpp.md).

   Die angegebene Datei kann eine DLL-, EXE, .NETMODULE oder OBJ-Datei sein, solange sie in MSIL ist. Die Komponente, auf die verwiesen wird, kann in einer beliebigen Sprache erstellt sein. Mit dieser Option erhalten Sie Zugriff auf IntelliSense, da die Metadaten aus MSIL extrahiert werden. Die fragliche Datei muss sich im Pfad für das Projekt befinden, ansonsten wird das Projekt nicht kompiliert, und IntelliSense ist nicht verfügbar. Eine einfache Möglichkeit zum Bestimmen, ob eine Datei sich im Pfad befindet, besteht darin, mit der rechten Maustaste auf die #using-Zeile zu klicken und den Befehl **Dokument öffnen** auszuwählen. Wenn die Datei nicht gefunden werden kann, erhalten Sie eine Benachrichtigung.

   Wenn Sie nicht den vollständigen Pfad zur Datei eingeben möchten, können Sie mit der **/AI**-Compileroption den Suchpfad für #using-Verweise bearbeiten. Weitere Informationen finden Sie unter [/AI (Metadatenverzeichnisse festlegen)](reference/ai-specify-metadata-directories.md).

#### <a name="to-reference-assemblies-with-fu"></a>So verweisen Sie mit /FU auf Assemblys

1. Anstatt wie oben beschrieben direkt aus einer Codedatei auf eine Assembly zu verweisen, können Sie auch die **/FU**-Compileroption verwenden. Der Vorteil dieses Verfahrens besteht darin, dass Sie nicht jeder einzelnen Datei eine separate, auf eine bestimmte Assembly verweisende #using-Anweisung hinzufügen müssen.

   Öffnen Sie die **Eigenschaftenseiten** für das Projekt, um diese Option festzulegen. Erweitern Sie den Knoten **Konfigurationseigenschaften** und anschließend den Knoten **C/C++** , und wählen Sie **Erweitert** aus. Fügen Sie neben **#using erzwingen** die gewünschten Assemblys hinzu. Weitere Informationen finden Sie unter [/FU (Name der expliziten #using-Datei)](reference/fu-name-forced-hash-using-file.md).

#### <a name="to-reference-assemblies-with-add-new-reference"></a>So verweisen Sie mit "Neuen Verweis hinzufügen" auf Assemblys

1. Dies ist die einfachste Möglichkeit, CLR-Assemblys zu nutzen. Vergewissern Sie sich zunächst, dass das Projekt mit der **/CLR**-Compileroption kompiliert wird. Klicken Sie anschließend im **Projektmappen-Explorer** auf das Projekt, und klicken Sie auf **Hinzufügen** und dann auf **Verweise**. Das Dialogfeld **Eigenschaftenseiten** wird angezeigt.

1. Wählen Sie im Dialogfeld **Eigenschaftenseiten** die Option **Neuen Verweis hinzufügen** aus. Daraufhin wird ein Dialogfeld angezeigt, in dem alle im aktuellen Projekt verfügbaren .NET-Assemblys, COM-Assemblys und sonstigen Assemblys aufgelistet werden. Wählen Sie die gewünschte Assembly aus, und klicken Sie auf **OK**.

   Sobald ein Projektverweis festgelegt ist, werden die entsprechenden Abhängigkeiten automatisch behandelt. Da eine Assembly Metadaten enthält, ist es auch nicht erforderlich, den Elementen, die von verwalteten Assemblys verwendet werden, eine Headerdatei oder einen Prototyp hinzuzufügen.

## <a name="referencing-native-dlls-or-static-libraries"></a>Verweisen auf systemeigene DLLs oder statische Bibliotheken

#### <a name="to-reference-native-dlls-or-static-libraries"></a>So verweisen Sie auf systemeigene DLLs oder statische Bibliotheken

1. Verweisen Sie mit der #include-Anweisung auf die entsprechende Headerdatei im Code. Die Headerdatei muss sich im include-Pfad befinden oder dem aktuellen Projekt angehören. Weitere Information finden Sie unter [#include Directive (C/C++) (#include-Direktive (C/C++))](../preprocessor/hash-include-directive-c-cpp.md).

1. Sie können auch Projektabhängigkeiten festlegen. Das Festlegen von Projektabhängigkeiten garantiert zwei Dinge: Zum einen gewährleistet es, dass Projekte in der richtigen Reihenfolge erstellt werden, damit ein Projekt immer die benötigten abhängigen Dateien findet. Zum anderen wird implizit das Ausgabeverzeichnis des abhängigen Projekts zum Pfad hinzugefügt, damit Dateien zum Zeitpunkt der Verknüpfung mühelos gefunden werden können.

1. Um die Anwendung bereitzustellen, müssen Sie die DLL an einer geeigneten Stelle platzieren. Folgende Möglichkeiten stehen zur Auswahl:

   1. In demselben Pfad wie die ausführbare Datei.

   1. An einer beliebigen Stelle im Systempfad (der **path**-Umgebungsvariable).

   1. In der parallelen Assembly. Weitere Informationen finden Sie unter [Building C/C++ Side-by-side Assemblies (Erstellen von parallelen C/C++-Assemblys)](building-c-cpp-side-by-side-assemblies.md).

## <a name="working-with-multiple-projects"></a>Arbeiten mit mehreren Projekten

Projekte werden standardmäßig so erstellt, dass alle Ausgabedateien in einem Unterverzeichnis des Projektverzeichnisses erstellt werden. Das Verzeichnis wird auf Basis der Buildkonfiguration benannt (z.B. Debuggen oder Release). Damit nebengeordnete Projekte erfolgreich aufeinander verweisen können, müssen in jedem Projekt die Ausgabeverzeichnisse des jeweils anderen Projekts dem Pfad hinzugefügt werden. Dies erfolgt beim Festlegen der Projektabhängigkeiten automatisch. Wenn Sie allerdings keine Abhängigkeiten verwenden, müssen Sie bei der Behandlung dieses Aspekts mit Sorgfalt vorgehen, da die Verwaltung von Builds sehr komplex werden kann. Wenn ein Projekt beispielsweise über Debug- und Releasekonfigurationen verfügt und eine externe Bibliothek aus einem nebengeordneten Projekt umfasst, muss je nach Konfiguration, die erstellt wird, eine andere Bibliotheksdatei verwendet werden. Eine feste Programmierung dieser Pfade kann sich also als kompliziert erweisen.

Alle wichtigen Ausgabedateien (z. B. ausführbare Dateien, Incremental Linker-Dateien und PDB-Dateien) werden in ein gemeinsames Projektmappenverzeichnis kopiert. Zur Vereinfachung der Verknüpfung und Bereitstellung werden demnach bei der Arbeit mit einer Lösung, die mehrere C++-Projekte mit äquivalenten Konfigurationen umfasst, alle Ausgabedateien zentral zusammengefasst. Wenn Sie diese Dateien zusammenhalten, können Sie sicher sein, dass die Anwendung/Bibliothek erwartungsgemäß funktioniert (da gewährleistet ist, dass sich die Dateien im Pfad befinden).

Bei der Bereitstellung in einer Produktionsumgebung kann der Speicherort der Ausgabedateien ein ernstes Problem darstellen. Während der Ausführung von Projekten in der IDE müssen die Pfade zu den enthaltenen Bibliotheken nicht notwendigerweise mit denjenigen in der Produktionsumgebung übereinstimmen. Wenn der Code beispielsweise `#using "../../lib/debug/mylib.dll"` umfasst und Sie dann mylib.dll an einer anderen relativen Position bereitstellen, generiert die Anwendung zur Laufzeit einen Fehler. Um dies zu verhindern, sollten Sie in #include-Anweisungen in Ihrem Code keine relativen Pfade verwenden. Es wird empfohlen sicherzustellen, dass die erforderlichen Dateien sich im Projektbuildpfad befinden und dass die entsprechenden Produktionsdateien korrekt platziert sind.

#### <a name="how-to-specify-where-output-files-go"></a>So geben Sie den Speicherort von Ausgabedateien an

1. Die Einstellungen für den Speicherort der Projektausgabe finden Sie in den **Eigenschaftenseiten** des Projekts. Erweitern Sie den Knoten neben **Konfigurationseigenschaften**, und klicken Sie auf **Allgemein**. Das Ausgabeverzeichnis wird neben dem **Ausgabeverzeichnis** angegeben. Weitere Informationen finden Sie unter [General Property Page (Project) (Eigenschaftenseite „Allgemein“ (Projekt))](reference/general-property-page-project.md).

## <a name="see-also"></a>Siehe auch

[C++-Projektvorlagen](reference/visual-cpp-project-types.md)
