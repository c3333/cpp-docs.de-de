---
title: Gemischte (systemeigene und verwaltete) Assemblys
ms.date: 09/18/2018
helpviewer_keywords:
- interop [C++], mixed assemblies
- /clr compiler option [C++], mixed assemblies
- managed code [C++], interoperability
- interoperability [C++], mixed assemblies
- mixed DLL loading [C++]
- mixed assemblies [C++], about mixed assemblies
- assemblies [C++], mixed
- mixed assemblies [C++]
- native code [C++], .NET interoperatibility
ms.assetid: 4299dfce-392f-4933-8bf0-5da2f0d1c282
ms.openlocfilehash: eee54a6101a83a64c221ae016f69931e7fd7829b
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2020
ms.locfileid: "86403698"
---
# <a name="mixed-native-and-managed-assemblies"></a>Gemischte (native und verwaltete) Assemblys

Gemischte Assemblys können sowohl nicht verwaltete Maschinenanweisungen als auch MSIL-Anweisungen enthalten. Dadurch können Sie aufrufen und von .NET-Komponenten aufgerufen werden, wobei die Kompatibilität mit nativen C++-Bibliotheken beibehalten wird. Mithilfe gemischter Assemblys können Entwickler Anwendungen erstellen, die eine Mischung aus .net und System eigenem C++-Code verwenden.

Beispielsweise kann eine vorhandene Bibliothek, die ausschließlich aus nativem C++-Code besteht, auf die .NET-Plattform gebracht werden, indem nur ein Modul mit dem **/CLR** -Compilerschalter neu kompiliert wird. Dieses Modul kann dann .NET-Features verwenden, bleibt aber mit dem Rest der Anwendung kompatibel. Es ist sogar möglich, zwischen der verwalteten und der systemeigenen Kompilierung für eine Funktionsweise in derselben Datei zu entscheiden (siehe [verwaltete, nicht verwaltete](../preprocessor/managed-unmanaged.md)).

Visual C++ unterstützt nur die Generierung gemischter verwalteter Assemblys mithilfe der **/CLR** -Compileroption. Die Compileroptionen **/clr: pure** und **/clr: Safe** sind in Visual Studio 2015 veraltet und werden in Visual Studio 2017 nicht unterstützt. Wenn Sie reine oder überprüfbare verwaltete Assemblys benötigen, empfiehlt es sich, diese mithilfe von c# zu erstellen.

Frühere Versionen des Microsoft C++-compilertoolsets unterstützten die Generierung von drei unterschiedlichen Typen verwalteter Assemblys: gemischt, rein und überprüfbar. Die beiden letzteren werden im [reinen und überprüfbaren Code (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)erläutert.

## <a name="in-this-section"></a>In diesem Abschnitt

[Vorgehensweise: Migrieren zu/CLR](../dotnet/how-to-migrate-to-clr.md)<br/>
Beschreibt die empfohlenen Schritte zum Einführen bzw. Aktualisieren der .NET-Funktionen in der Anwendung.

[Vorgehensweise: Kompilieren von MFC-und ATL-Code mithilfe von/CLR](../dotnet/how-to-compile-mfc-and-atl-code-by-using-clr.md)<br/>
Erläutert, wie vorhandene MFC- und ATL-Programme für die Common Language Runtime kompiliert werden können.

[Initialisierung gemischter Assemblys](../dotnet/initialization-of-mixed-assemblies.md)<br/>
Beschreibt das Problem der "Ladeprogrammsperren" und die entsprechenden Lösungen.

[Bibliotheks Unterstützung für gemischte Assemblys](../dotnet/library-support-for-mixed-assemblies.md)<br/>
Erläutert, wie Native Bibliotheken in **/CLR** -Kompilierungen verwendet werden.

[Überlegungen zur Leistung](../dotnet/performance-considerations-for-interop-cpp.md)<br/>
Beschreibt, wie sich gemischte Assemblys und das Marshalling von Daten auf die Leistung auswirken.

[Anwendungs Domänen und Visual C++](../dotnet/application-domains-and-visual-cpp.md)<br/>
Erörtert die Visual C++-Unterstützung für Anwendungsdomänen.

[Doppeltes Thunking](../dotnet/double-thunking-cpp.md)<br/>
Erörtert, wie sich ein systemeigener Einstiegspunkt für eine verwaltete Funktion auf die Leistung auswirkt.

[Vermeiden von Ausnahmen beim Herunterfahren von CLR bei Verwendung von mit/CLR erstellten COM-Objekten](../dotnet/avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr.md)<br/>
Erläutert, wie eine verwaltete Anwendung, die ein mit **/CLR**kompiliertes com-Objekt verwendet, ordnungsgemäß heruntergefahren wird.

[Gewusst wie: Erstellen einer teilweise vertrauenswürdigen Anwendung durch Entfernen der Abhängigkeit von der CRT-Bibliotheks-dll](../dotnet/create-a-partially-trusted-application.md)<br/>
Erläutert das Erstellen einer teilweise vertrauenswürdigen Common Language Runtime-Anwendung mithilfe von Visual C++ durch Entfernen der Abhängigkeit von msvcm90.dll.

Weitere Informationen zu Codierungs Richtlinien für gemischte Assemblys finden Sie unter [Übersicht über die Interoperabilität von verwaltetem/nicht verwaltetem Code](/previous-versions/dotnet/articles/ms973872(v=msdn.10)).

## <a name="see-also"></a>Weitere Informationen

- [Native und .NET-Interoperabilität](../dotnet/native-and-dotnet-interoperability.md)
