---
title: Plattformübergreifende mobile Entwicklung mit C++
ms.date: 11/14/2019
ms.assetid: 0bb872d6-981b-4c96-9143-fcec5336bf0d
ms.openlocfilehash: dd2ea678d7689fac60bcee3555772b87df06e31b
ms.sourcegitcommit: a673f6a54cc97e3d4cd032b10aa8dce7f0539d39
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2020
ms.locfileid: "79469986"
---
# <a name="cross-platform-mobile-development-with-c"></a>Plattformübergreifende mobile Entwicklung mit C++

Mit den in Visual Studio verfügbaren plattformübergreifenden Tools können Sie native C++-Apps für iOS-, Android- und Windows-Geräte entwickeln. **Mobile Entwicklung mit C++** ist eine im Visual Studio-Installer verfügbare Workload. Mit ihr werden die SDKs und Tools installiert, die Sie für die plattformübergreifende Entwicklung freigegebener Bibliotheken und nativer Apps benötigen. Nach ihrer Installation können Sie mit C++ Code erstellen, der auf iOS- und Android-Geräten und -Plattformen, sowie unter Windows, Windows Store und auf der Xbox ausgeführt wird.

Das Schreiben von Code für mehrere Plattformen ist oft mühsam. Die primären Entwicklungssprachen und Tools für iOS, Android und Windows sind auf jeder Plattform unterschiedlich. Alle Plattformen unterstützen jedoch das Schreiben von Code in C++. Dies ist der gemeinsame Nenner, der ermöglicht, Kerncode plattformübergreifend zu wiederzuverwenden. In C++ geschriebener systemeigener Code kann sowohl leistungsfähiger als auch beständiger gegen Reverse Engineering sein. Die Wiederverwendung von Code spart Zeit und Mühe beim Erstellen von Apps für mehrere Plattformen.

Die Verwendung von C++ für die plattformübergreifende mobile Entwicklung hat mehrere Vorteile:

- **Einfache Installation.** Der Visual Studio-Installer ruft die erforderlichen Tools von Drittanbietern und SDKs ab, die Sie zum Erstellen von Apps oder Bibliotheken für Android und iOS benötigen, und installiert diese. Konfiguration und Setup sind einfach und erfolgen größtenteils automatisch.

- **Eine leistungsstarke und vertraute Buildumgebung.** Erstellen Sie freigebbare plattformübergreifende Projektmappen und Projekte einfach mit Visual Studio-Vorlagen. Verwalten Sie die Eigenschaften für alle Projekte mit einer gemeinsamen Oberfläche. Bearbeiten Sie den gesamten Code im Visual Studio-Editor, und nutzen Sie die integrierte plattformübergreifende IntelliSense-Funktion für die Codevervollständigung und Fehlerhervorhebung.

- **Einheitliche Funktionen für das Debuggen.** Verwenden Sie die erstklassigen Debugtools in Visual Studio, um Code auf C++ allen Plattformen zu überwachen und zu durchlaufen: Android-Geräte und-Emulatoren, IOS-Simulatoren und-Geräte sowie Windows-oder Windows Store-Geräte und-Emulatoren.

## <a name="get-the-tools"></a>Tools herunterladen

Die mobile Entwicklung mit C++ ist eine zu Visual Studio gehörende installierbare Workload. Erforderliche Komponenten und Installationsanweisungen finden Sie unter [Installieren der plattformübergreifenden mobilen Entwicklung mit C++](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md). Um Code für iOS zu erstellen, benötigen Sie auch einen Macintosh-Computer und ein Apple iOS-Entwicklerkonto. Weitere Informationen finden Sie unter [Installieren und Konfigurieren von Tools zum Erstellen mit iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md).

## <a name="come-up-to-speed"></a>Optimales Leistungsniveau

Für alle, die bislang in der Android- oder iOS- Entwicklung zu Hause waren, steht hilfreiches Material für die ersten Schritte zur Verfügung. Visual Studio ist eine ausdrucksvolle und leistungsfähige Entwicklungsumgebung. Informationen dazu, wie Sie das Programm nutzen können, finden Sie unter [Get started for Android developers (Erste Schritte für Android-Entwickler)](/previous-versions/windows/apps/dn275875\(v=win.10\)) bzw. [Get started for iOS developers (Erste Schritte für iOS-Entwickler)](/previous-versions/windows/apps/jj657966\(v=win.10\)). In diesen Artikeln werden Sie mit Visual Studio und den Konzepten vertraut gemacht, die Sie benötigen, um plattformübergreifende Apps für Windows und Windows Store zu entwickeln. Informationen zu den ersten Schritten beim Schreiben Ihrer ersten plattformübergreifenden App für iOS und Android finden Sie unter [Erstellen einer OpenGL ES-Anwendung für Android und iOS](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md).

Die Workload „Mobile-Entwicklung mit C++“ umfasst mehrere Vorlagen, die Ihnen bei den ersten Schritten mit Ihren Apps helfen:

- Anwendung mit systemeigener Aktivität (Android)

  Erstellt eine vollständige C++ OpenGL-App in Form eines Android-Projekts mit systemeigener Aktivität.

- OpenGLES-Anwendung (Android, iOS)

  Erstellt eine Projektmappe mit einem Satz von Projekten zum Erstellen einer Android-App mit systemeigener Aktivität und einer iOS-Apps. Diese Apps verwenden plattformspezifische Bibliotheken mit gemeinsamem C++ OpenGL ES-Code zum Zeichnen des gleichen sich drehenden Würfels in jeder App.

- Freigegebene Bibliothek (Android, iOS)

  Erstellt eine Projektmappe mit Projekten zum Erstellen einer Datei für eine dynamische Bibliothek für Android (.so) und einer Datei für eine statische Bibliothek für iOS (.a) mithilfe von gemeinsamem C++-Code in einem freigegebenen Projekt.

- Basisanwendung (Android, Ant)

  Erstellt ein „Hello World“-App-Projekt für Android, das nur Java-Quellcode und das Ant-Buildsystem verwendet.

- Basisanwendung (Android, Gradle)

  Erstellt ein „Hello World“-App-Projekt für Android, das nur Java-Quellcode und das Gradle-Buildsystem verwendet.

- Basisbibliothek (Android, Ant)

  Erstellt ein „Hello World“-Bibliotheksprojekt für Android, das nur Java-Quellcode und das Ant-Buildsystem verwendet.

- Basisbibliothek (Android, Gradle)

  Erstellt ein „Hello World“-Bibliotheksprojekt für Android, das nur Java-Quellcode und das Gradle-Buildsystem verwendet.

- Dynamische freigegebene Bibliothek (Android)

  Erstellt eine Datei für eine dynamische Bibliothek für Android (.so) mithilfe von C++-Code.

- OpenGLES 2-Anwendung (iOS)

  Erstellt eine Projektmappe mit Projekten zum Erstellen einer OpenGL ES 2 iOS-App. Die App verwendet zum Zeichnen eines sich drehenden Würfels in einer iOS-App eine Bibliothek mit C++ OpenGL ES-Code. Diese App ist ein guter Ausgangspunkt für den Import von C++-Bibliotheken in die iOS-App.

- Statische Bibliothek (Android)

  Erstellt ein Projekt zum Erstellen einer statischen Bibliothek für Android. Sie können nur eine dynamische Bibliothek in einer Android-App verknüpfen, aber Sie können eine beliebige Anzahl von statischen Bibliotheken verknüpfen.

- Statische Bibliothek (iOS)

  Erstellt ein Projekt zum Erstellen einer statischen Bibliothek für iOS.

- Makefile-Projekt (Android)

  Erstellt einen Projektwrapper für Android Makefile-Projekte.

## <a name="try-out-sample-code"></a>Testen des Beispielcodes

Laden Sie Beispiele herunter, die zeigen, wie freigegebene Codebibliotheken erstellt werden, die Sie in Windows-, Android- und iOS-Apps verwenden können. Sehen Sie sich außerdem Beispiele an, wie Sie komplette Android-Apps mit nativer Aktivität erstellen können. Informationen zu den ersten Schritten finden Sie unter [Beispiele für plattformübergreifende Mobile-Entwicklung](../cross-platform/cross-platform-mobile-development-examples.md).

## <a name="see-also"></a>Weitere Informationen

[Installieren der plattformübergreifenden mobile Entwicklung mit C++](../cross-platform/install-visual-cpp-for-cross-platform-mobile-development.md)\
[Installieren und Konfigurieren von Tools zum Entwickeln mit iOS](../cross-platform/install-and-configure-tools-to-build-using-ios.md)\
[Erstellen einer Android-App mit nativer Aktivität](../cross-platform/create-an-android-native-activity-app.md)\
[Erstellen einer OpenGL ES-Anwendung für Android und iOS](../cross-platform/build-an-opengl-es-application-on-android-and-ios.md)\
[Cross-platform mobile development examples (Beispiele für die plattformübergreifende Mobile-Entwicklung)](../cross-platform/cross-platform-mobile-development-examples.md)
