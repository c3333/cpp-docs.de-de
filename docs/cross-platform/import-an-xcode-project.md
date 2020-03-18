---
title: Importieren eines Xcode-Projekts
ms.date: 10/17/2019
ms.assetid: aa4b8161-d98f-4a1a-9db3-520133bfc82f
ms.openlocfilehash: 709060e053852f4518a842467ccfb7f0ed760ba2
ms.sourcegitcommit: a673f6a54cc97e3d4cd032b10aa8dce7f0539d39
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2020
ms.locfileid: "79470046"
---
# <a name="import-an-xcode-project"></a>Importieren eines Xcode-Projekts

Die Visual Studio-Tools für die plattformübergreifende, mobile Entwicklung mit C++ umfasst die Unterstützung für das Verschieben von Xcode-Projekten in Visual Studio, wo Sie plattformübergreifende Bibliotheken erstellen und den Code mit anderen Projekten nutzen können. Der Assistent „Aus Xcode importieren“ vereinfacht den Prozess des Importierens von Projekten und des Aufteilens des C++-Codes auf Ihre Xcode-Ziele, um diese als statische Bibliothek oder freigegebenes Codeprojekt zu verwenden. Sie können Ihren iOS-spezifischen Code in Visual Studio verwalten und trotzdem Xcode verwenden, um Storyboards und Builds auszuführen. Informationen darüber, wie Sie einfach Code zwischen Visual Studio und Xcode verschieben können, finden Sie unter [Synchronisieren von Änderungen zwischen Xcode und Visual Studio](sync-changes-between-xcode-and-visual-studio.md).

## <a name="use-the-import-from-xcode-wizard"></a>Verwenden des Assistenten „Aus Xcode importieren“

In diesem Artikel erfahren Sie, wie Sie ein Xcode-Projekt in Visual Studio verschieben, um von Codefreigabe und plattformübergreifende Lösungen zu profitieren. Als Vorbereitungsmaßnahme müssen Sie Ihren Mac mit Visual Studio koppeln, um Ihr Projekt importieren, exportieren und erstellen zu können. Ausführliche Anweisungen zur Kopplung finden Sie unter [Installieren und Konfigurieren von Tools zum Erstellen mit iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md). Außerdem müssen Sie entweder Ihr Xcode-Projekt über das Netzwerk freigeben oder es auf Ihren Computer, auf dem Visual Studio installiert ist, verschieben, um den Assistenten „Aus Code importieren“ zu verwenden.

### <a name="import-from-xcode"></a>Aus Xcode importieren

1. Wählen Sie im Menü **Datei** nacheinander **Neu**, **Importieren**, **Aus Xcode importieren** aus. Dadurch wird das Dialogfeld des Assistenten **Aus Xcode importieren** gestartet.

   ![Auswählen des zu importierenden Xcode-Zielprojekts](../cross-platform/media/cppmdd-u2-importxcode-choose.png "Auswählen des zu importierenden Xcode-Zielprojekts")

1. Klicken Sie im Bereich **Projekt auswählen** auf die Schaltfläche „Durchsuchen“, um eine Xcode-Datei mit der Erweiterung *.pbxproj* auszuwählen. Navigieren Sie im Dialogfeld **Xcode-Projektdatei auswählen** zur Projektdatei, und klicken Sie anschließend auf **Öffnen**.

   ![Auswählen einer Projektdatei im Dialogfeld „Xcode-Projektdatei auswählen“](../cross-platform/media/cppmdd-u2-importxcode-browse.png "Auswählen einer Projektdatei im Dialogfeld „Xcode-Projektdatei auswählen“")

   Klicken Sie im Assistenten „Aus Xcode importieren“ auf **Weiter**.

1. Wählen Sie im Bereich **Ziele** die Ziele des Xcode-Projekts, die in Visual Studio-Projekte importiert werden sollen. Xcode-Ziele ähneln Visual Studio-Projekten. Die meisten sind eine Sammlung von Code und Ressourcen zum Erzeugen einer Binärdatei. Der Assistent „Aus Xcode importieren“ ermöglicht nur das Importieren von Zielen, die eine Binärdatei, aber keine statische Bibliothek als Ziele erzeugen. Statische Bibliotheksziele mit Xcode sind Gegenstand des nächsten Schritts.

   ![Bereich „Ziele“ des Assistenten „Aus Xcode importieren“](../cross-platform/media/cppmdd-u2-importxcode-destination.jpg "Bereich „Ziele“ des Assistenten „Aus Xcode importieren“")

   Für jedes Ziel, das unter **Zu importierende Ziele** ausgewählt wurde, erkennt der Assistent automatisch C++-Codedateien, die in einem separaten statischen Bibliotheksprojekt aufgeteilt werden können, und fügt sie im Abschnitt **C++-Projektelemente** hinzu. Anderer Code und Ressourcen verbleiben im Abschnitt **Xcode-Projektelemente**. Diese werden nach Abschluss des Importprozesses durch den Assistenten zu separaten statischen Bibliotheks- und Anwendungsprojekten in Visual Studio. Standardmäßig werden Komponententest- und Frameworkziele vom Assistenten nicht in separate Projekte aufgeteilt.

   Verwenden Sie die Schaltflächen „nach oben“ und „nach unten“, um zu ändern, welche Dateien sich in jedem Projekt befinden. Wenn Sie mit den Dateien in jedem Projekt zufrieden sind, klicken Sie auf **Weiter**, um fortzufahren.

1. Wählen Sie Im Bereich **Bibliotheksziel** die statischen Bibliotheksziele des Xcode-Projekts aus, die in Visual Studio-Projekte importiert werden sollen. In diesem Bereich können Sie auswählen, welche Dateien in einem Projekt mit freigegebenem Code eingefügt und welche in einem statischen Bibliotheksprojekt abgelegt werden sollen. In jedem der Ziele in der Liste **Zu importierende Ziele** können Sie mithilfe der Schaltflächen „Nach oben“ und „Nach unten“ steuern, welche Dateien in den **Elementen für Projekte mit freigegebenem Code** und den **Projektelementen der statischen Bibliothek** abgelegt werden sollen.

   ![Bereich „Bibliotheksziele“ in „Aus Xcode importieren“](../cross-platform/media/cppmdd-u2-importxcode-library.jpg "Bereich „Bibliotheksziele“ in „Aus Xcode importieren“")

   Ein Projekt mit freigegebenem Code bietet eine Möglichkeit zum Freigeben eines Satzes von Quellcodedateien für unterschiedliche Projekte in Visual Studio. Der Code wird als Teil des Projekts erstellt, das ihn enthält, und nicht als eigenes Projekt. Projekte, die den freigegebenen Code enthalten, verfügen möglicherweise über unterschiedliche Architekturen und Konfigurationen. Ein Projekt mit freigegebenem Code ist die beste Möglichkeit zur Bereitstellung eines einzelnen Projekts, das Code enthält, der für viele Arten von Plattformen erstellt werden kann.

   Wenn Sie mit den Dateien in jedem Projekt zufrieden sind, klicken Sie auf **Weiter**, um fortzufahren.

1. Legen Sie im Bereich **Globale Eigenschaften** einen Suchpfad für Frameworks und einen Suchpfad zum Einbeziehen von Headern für alle iOS-Projekte in Visual Studio fest. Visual Studio verwendet diese Pfade für das Durchsuchen von Quellcode und für IntelliSense. Diese globalen Pfade sind nützlich, wenn Sie iOS-Projekte erstellen, die einen gemeinsamen Satz von Headern und Frameworks verwenden.

   ![Bereich „Globale Eigenschaften“ in „Aus Xcode importieren“](../cross-platform/media/cppmdd-u2-importxcode-global.jpg "Bereich „Globale Eigenschaften“ in „Aus Xcode importieren“")

   Diese globalen Pfade können auch in Visual Studio im Dialogfeld **Optionen** festgelegt werden. Wählen Sie im Menü **Tools** **Optionen** aus, um sie zu finden. Erweitern Sie im Dialogfeld **Optionen** nacheinander **Plattformübergreifend** > **C++**  > **iOS** > **Globale Eigenschaften**.

   Klicken Sie auf **Weiter**, um fortzufahren.

1. Der Bereich **Frameworks** wird verwendet, um die von Visual Studio zum Durchsuchen verwendeten Pfade und IntelliSense für Ihr Projekt zu konfigurieren. Die Pfade müssen in Visual Studio für jedes Framework zugänglich sein, auf das Ihr Xcode-Projekt verweist. Der Assistent prüft die Frameworkverweise in den Xcode-Projekten und zeigt an, ob Visual Studio das Framework finden kann. Jeder Pfad, den Sie bereits in den globalen Eigenschaften eingerichtet haben, sollte von Visual Studio erkannt werden. Die Ausnahmen werden in der Liste der Frameworks aufgeführt. Stellen Sie für jedes aufgelistete Framework mit einem X einen vom PC zugänglichen Pfad für Visual Studio bereit, um das Framework zu finden. Sie können die Schaltfläche „Durchsuchen“ ( **...** ) verwenden, um das Dialogfeld **Ordner auswählen** zum Suchen des Pfads zu nutzen. Der Frameworkpfad kann entweder auf eine lokale Kopie oder eine Freigabe verweisen, auf die über das Netzwerk auf Ihrem Mac zugegriffen werden kann.

   ![Bereich „Frameworks“ in „Aus Xcode importieren“](../cross-platform/media/cppmdd-u2-importxcode-frameworks.jpg "Bereich „Frameworks“ in „Aus Xcode importieren“")

   Klicken Sie auf **Weiter**, um fortzufahren.

1. Der Bereich **Projekteinstellungen** erlaubt es Ihnen, das Framework zu ändern, und beinhaltet Einstellungen für den Suchpfad für Header für jedes Projekt, das der Assistent erstellt. Verwenden Sie diesen Bereich, um projektspezifische Pfade, die sich von den globalen Einstellungen unterscheiden, festzulegen.

   Um einen Pfad für ein bestimmtes Projekt festzulegen, wählen Sie im Dropdownmenü **Zielprojekt** die Projektdatei aus. Legen Sie anschließend die Werte in den Steuerelementen **Suchpfad für Framework** und **Suchpfad für Header einbeziehen** fest. Sie können die Schaltfläche „Durchsuchen“ ( **...** ) neben jedem Steuerelement verwenden, um das Dialogfeld **Ordner auswählen** zum Suchen des Pfads zu nutzen.

   ![Bereich „Projekte“ in „Aus Xcode importieren“](../cross-platform/media/cppmdd-u2-importxcode-projects.jpg "Bereich „Projekte“ in „Aus Xcode importieren“")

   Wenn dieser PC in Visual Studio keinem Mac-Remotecomputer zugeordnet wurde, wird der Link **Remotecomputer konfigurieren** angezeigt. Ausführliche Anweisungen zur Kopplung finden Sie unter [Installieren und Konfigurieren von Tools zum Erstellen mit iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).

   Klicken Sie auf **Importieren**, um das Xcode-Projekt mithilfe der Einstellungen des Assistenten zu importieren.

   Der Assistent „Aus Xcode importieren“ erstellt in Visual Studio Projekte, die den ausgewählten Xcode-Projektzielen entsprechen. Der Code, der mit anderen C++-Projekten gemeinsam genutzt werden kann, wird in einen separat freigegebenen Code und statische Bibliotheksprojekte unterteilt. Der restliche Code wird in den iOS-Bibliotheks- und Anwendungsprojekten eingefügt, die von Visual Studio remote erstellt werden können. Weitere Informationen zum Verschieben von Code zwischen Visual Studio und Xcode finden Sie unter [Synchronisieren von Änderungen zwischen Xcode und Visual Studio](../cross-platform/sync-changes-between-xcode-and-visual-studio.md).

## <a name="see-also"></a>Weitere Informationen

- [Installieren der plattformübergreifenden mobilen Entwicklung mit C++](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)
