---
title: C++/CX-Sprachreferenz
ms.date: 09/15/2017
ms.assetid: 3f6abf92-4e5e-4ed8-8e11-f9252380d30a
ms.openlocfilehash: f28270ace3965a3cf89e250a873af14e48390708
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507425"
---
# <a name="ccx-language-reference"></a>C++/CX-Sprachreferenz

C++/CX ist ein Satz von Erweiterungen für die C++-Sprache, die die Erstellung von Windows-apps und Windows-Runtime Komponenten in einer Ausdrucksweise ermöglichen, die so nah wie möglich an modern C++ ist. Verwenden Sie C++/CX, um Windows-apps und-Komponenten in nativem Code zu schreiben, die problemlos mit Visual c#, Visual Basic und JavaScript und anderen Sprachen, die die Windows-Runtime unterstützen, interagieren können. In den seltenen Fällen, die direkten Zugriff auf die unformatierten COM-Schnittstellen oder nicht Ausnahme Code erfordern, können Sie die [Windows-Runtime C++ Template Library (WRL)](./wrl/windows-runtime-cpp-template-library-wrl.md)verwenden.

> [!NOTE]
> **/WinRT ist die empfohlene Alternative zu C++/CX. [ C++](/windows/uwp/cpp-and-winrt-apis/index)** Dabei handelt es sich um eine neue, standardmäßige c++ 17-sprach Projektion für Windows-Runtime-APIs, die im neuesten Windows 10 SDK ab Version 1803 verfügbar ist. C++/WinRT wird vollständig in Header Dateien implementiert und wurde entwickelt, um Ihnen erstklassigen Zugriff auf die moderne Windows-API zu ermöglichen.
>
> Mit C++/WinRT können Sie mithilfe eines beliebigen Standard kompatiblen C++ 17-Compilers Windows-Runtime-APIs verwenden und erstellen. C++/WinRT führt in der Regel zu einer besseren Leistung und erzeugt kleinere Binärdateien als jede andere Sprachoption für die Windows-Runtime. Wir unterstützen C++/CX und WRL weiterhin, empfehlen jedoch dringend die Verwendung von C++/WinRT für neue Anwendungen. Weitere Informationen finden Sie unter [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/index).

Mithilfe von C++/CX können Sie Folgendes erstellen:

- C++ universelle Windows-Plattform-Apps (UWP), die XAML verwenden, um die Benutzeroberfläche zu definieren und den systemeigenen Stapel zu verwenden. Weitere Informationen finden Sie unter [Erstellen einer "Hello World"-app in C++ (UWP)](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp).

- C++ Windows-Runtime Komponenten, die von JavaScript-basierten Windows-Apps verwendet werden können. Weitere Informationen finden Sie unter [Creating Windows Runtime Components in C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

- Windows-DirectX-Spiele und grafikintensive Apps. Weitere Informationen finden Sie unter [Erstellen eines einfachen UWP-Spiels mit DirectX](/windows/uwp/gaming/tutorial--create-your-first-uwp-directx-game).

## <a name="related-articles"></a>Verwandte Artikel

| Link | Beschreibung |
|--|--|
| [Kurzübersicht](../cppcx/quick-reference-c-cx.md) | Tabelle mit Schlüsselwörtern und Operatoren für C++/CX. |
| [Typensystem](../cppcx/type-system-c-cx.md) | Beschreibt grundlegende C++/CX-Typen und-Programmierungskonstrukte und erläutert, wie C++/CX verwendet wird, um Windows-Runtime Typen zu nutzen und zu erstellen |
| [Erstellen von Apps und Bibliotheken](../cppcx/building-apps-and-libraries-c-cx.md) | Erläutert, wie die IDE verwendet wird, um apps zu erstellen und mit statischen Bibliotheken und DLLs zu verknüpfen. |
| [Interoperabilität mit anderen Sprachen](../cppcx/interoperating-with-other-languages-c-cx.md) | Erläutert, wie Komponenten, die mit C++/CX geschrieben werden, mit-Komponenten verwendet werden können, die in JavaScript, einer beliebigen verwalteten Sprache oder der Windows-Runtime C++-Vorlagen Bibliothek geschrieben sind. |
| [Threading und Marshalling](../cppcx/threading-and-marshaling-c-cx.md) | Erläutert, wie Sie das Threading- und Marshallingverhalten von Komponenten, die Sie erstellen, angeben können. |
| [Namespaces-Referenz](../cppcx/namespaces-reference-c-cx.md) | Referenzdokumentation für den Standardnamespace, den Plattformnamespace, den Platform::Collections-Namespace und die zugehörigen Namespaces. |
| [In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) | Listet die CRT-Funktionen auf, die nicht für die Verwendung in Windows Runtime-Apps verfügbar sind. |
| [Erste Schritte mit Windows 10-Apps](/windows/uwp/get-started/) | Bietet Anleitung auf hoher Ebene zu Windows 10-Apps und Links zu weiterführenden Informationen. |
| [C++/CX Teil 0 von \[ n \] : eine Einführung](https://devblogs.microsoft.com/cppblog/ccx-part-0-of-n-an-introduction/)<br /><br />[C++/CX Teil 1 von \[ n \] : einfache Klasse](https://devblogs.microsoft.com/cppblog/ccx-part-1-of-n-a-simple-class/)<br /><br />[C++/CX Teil 2 von \[ n \] : Typen mit hüten](https://devblogs.microsoft.com/cppblog/ccx-part-2-of-n-types-that-wear-hats/)<br /><br />[C++/CX Teil 3 von \[ n \] : in Bearbeitung](https://devblogs.microsoft.com/cppblog/ccx-part-3-of-n-under-construction/)<br /><br />[C++/CX Teil 4 von \[ n \] : statische Element Funktionen](https://devblogs.microsoft.com/cppblog/ccx-part-4-of-n-static-member-functions/)| Eine einführende Blog Reihe zu C++/CX. |
