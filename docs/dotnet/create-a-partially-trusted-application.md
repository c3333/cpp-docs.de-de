---
title: 'Gewusst wie: Erstellen einer teilweise vertrauenswürdigen Anwendung (C++/CLI)'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- partially trusted applications [C++]
- mixed assemblies [C++], partially trusted applications
- msvcm90[d].dll
- interoperability [C++], partially trusted applications
- interop [C++], partially trusted applications
- /clr compiler option [C++], partially trusted applications
ms.assetid: 4760cd0c-4227-4f23-a7fb-d25b51bf246e
ms.openlocfilehash: 9df3a751f4073472b9495425599aaf43878db99a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364403"
---
# <a name="how-to-create-a-partially-trusted-application-by-removing-dependency-on-the-crt-library-dll"></a>Gewusst wie: Erstellen einer teilweise vertrauenswürdigen Anwendung durch Entfernen der Abhängigkeit der CRT-Bibliotheks-DLL

In diesem Thema wird erläutert, wie Sie eine teilweise vertrauenswürdige Common Language Runtime-Anwendung mit Visual C++ erstellen, indem Sie die Abhängigkeit von msvcm90.dll entfernen.

Eine Visual C++-Anwendung, die mit **/clr** erstellt wurde, ist von msvcm90.dll abhängig, das Teil der C-Runtime-Bibliothek ist. Wenn Ihre Anwendung in einer teilweise vertrauenswürdigen Umgebung verwendet werden soll, erzwingt die CLR bestimmte Codezugriffssicherheitsregeln für Ihre DLL. Daher ist es notwendig, diese Abhängigkeit zu entfernen, da msvcm90.dll systemeigenen Code enthält und die Sicherheitsrichtlinie für den Codezugriff nicht erzwungen werden kann.

Wenn Ihre Anwendung keine Funktionen der C-Runtime-Bibliothek verwendet und Sie die Abhängigkeit von dieser Bibliothek aus Ihrem Code entfernen möchten, müssen Sie die Linkeroption **/NODEFAULTLIB:msvcmrt.lib** verwenden und entweder mit ptrustm.lib oder ptrustmd.lib verknüpfen. Diese Bibliotheken enthalten Objektdateien zum Initialisieren und Nichtinitialisieren einer Anwendung, Ausnahmeklassen, die vom Initialisierungscode verwendet werden, und verwalteten Ausnahmebehandlungscode. Durch das Verknüpfen in einer dieser Bibliotheken wird jede Abhängigkeit von msvcm90.dll entfernt.

> [!NOTE]
> Die Reihenfolge der Assembly-Uninitialisierung kann für Anwendungen unterschiedlich sein, die die ptrust-Bibliotheken verwenden. Bei normalen Anwendungen werden Assemblys in der Regel in umgekehrter Reihenfolge entladen, in der sie geladen werden, aber dies ist nicht garantiert. Bei Anwendungen mit teilweiser Vertrauenswürdigkeit werden Assemblys in der Regel in der gleichen Reihenfolge entladen, in der sie geladen werden. Auch dies ist nicht garantiert.

### <a name="to-create-a-partially-trusted-mixed-clr-application"></a>So erstellen Sie eine teilweise vertrauenswürdige gemischte (/clr) Anwendung

1. Um die Abhängigkeit von msvcm90.dll zu entfernen, müssen Sie für den Linker angeben, diese Bibliothek nicht einzuschließen, indem Sie die Linkeroption **/NODEFAULTLIB:msvcmrt.lib** verwenden. Informationen dazu finden Sie unter [/NODEFAULTLIB (Bibliotheken ignorieren)](../build/reference/nodefaultlib-ignore-libraries.md).

1. Fügen Sie den Linker-Eingabeabhängigkeiten eine der Ptrustm-Bibliotheken hinzu. Verwenden Sie ptrustm.lib, wenn Sie Ihre Anwendung im Freigabemodus erstellen. Verwenden Sie für den Debugmodus ptrustmd.lib. Informationen dazu, wie Sie dies mithilfe der Visual Studio-Entwicklungsumgebung oder programmgesteuert tun können, finden Sie unter [. Dateien als Linker-Eingabe libieren](../build/reference/dot-lib-files-as-linker-input.md).

## <a name="see-also"></a>Siehe auch

[Gemischte (native und verwaltete) Assemblys](../dotnet/mixed-native-and-managed-assemblies.md)<br/>
[Initialisierung gemischter Baugruppen](../dotnet/initialization-of-mixed-assemblies.md)<br/>
[Bibliotheksunterstützung für verschiedene Assemblys](../dotnet/library-support-for-mixed-assemblies.md)<br/>
[/link (Optionen an Linker übergeben)](../build/reference/link-pass-options-to-linker.md)
