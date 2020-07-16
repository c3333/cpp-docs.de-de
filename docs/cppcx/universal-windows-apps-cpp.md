---
title: Universelle Windows-Apps (C++)
ms.date: 03/30/2018
ms.assetid: 357121cc-d390-4bae-b34a-39614861a9f4
ms.topic: overview
ms.openlocfilehash: 25b89d2d9cb99e05145e60f9c9b1a6324fbbeb39
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404599"
---
# <a name="universal-windows-apps-c"></a>Universelle Windows-Apps (C++)

Der universelle Windows-Plattform (UWP) ist die moderne Programmierschnittstelle für Windows. Mit der UWP-Anwendung können Sie eine Anwendung oder Komponente einmal schreiben und auf jedem Windows 10-Gerät bereitstellen. Sie können eine Komponente in C++ schreiben, und Anwendungen, die in einer beliebigen anderen UWP-kompatiblen Sprache geschrieben wurden, können Sie verwenden.

Der größte Teil der UWP-Dokumentation finden Sie in der Windows-Inhaltsstruktur unter [universelle Windows-Plattform Dokumentation](/windows/uwp/). Dort finden Sie Start Lernprogramme sowie Referenz Dokumentation.

Für neue UWP-apps und-Komponenten empfiehlt sich die Verwendung von [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/), einer neuen standardmäßigen C++ 17-sprach Projektion für Windows-Runtime-APIs. C++/WinRT ist im Windows 10 SDK ab Version 1803 erhältlich. C++/WinRT wird vollständig in Headerdateien implementiert und wurde entwickelt, um Ihnen erstklassigen Zugriff auf die moderne Windows-API zu ermöglichen. Anders als bei der C++/CX-Implementierung verwendet C++/WinRT nicht die standardmäßige Syntax oder Microsoft-Spracherweiterungen und nutzt den C++-Compiler in vollem Umfang, um eine hochoptimierte Ausgabe zu erstellen. Weitere Informationen finden Sie unter [Introduction to C++/WinRT](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt).

Mit dem Desktop Bridge-App Converter können Sie Ihre vorhandene Desktop Anwendung für die Bereitstellung über das Microsoft Store verpacken. Weitere Informationen finden Sie unter [Verwenden von Visual C++ Runtime in Centennial Project](https://devblogs.microsoft.com/cppblog/using-visual-c-runtime-in-centennial-project/) und [Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root).

## <a name="uwp-apps-that-use-ccx"></a>UWP-apps, die C++/CX verwenden

|||
|-|-|
|[C++-/CX-Sprachreferenz](visual-c-language-reference-c-cx.md)|Beschreibt den Satz von Erweiterungen, die den C++-Verbrauch von Windows-Runtime-APIs vereinfachen und die Fehlerbehandlung ermöglichen, die auf Ausnahmen basiert.|
|[Entwickeln von apps und Bibliotheken (C++/CX)](building-apps-and-libraries-c-cx.md)|Beschreibt das Erstellen von DLLs und statischen Bibliotheken, auf die von einer C++/CX-App oder Komponente zugegriffen werden kann.|
|[Tutorial: Erstellen einer UWP-app "Hello, World" in C++/CX](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)|Eine exemplarische Vorgehensweise mit den grundlegenden Konzepten der UWP-App-Entwicklung in C++/CX. |
|[Erstellen von Windows-Runtime Komponenten in C++/CX](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)|Beschreibt, wie DLLs erstellt werden, die von anderen UWP-apps und-Komponenten verwendet werden können.|
|[UWP-Spielprogrammierung](/windows/uwp/gaming/)|Beschreibt, wie DirectX und C++/CX zum Erstellen von Spielen verwendet werden.|

## <a name="uwp-apps-that-use-the-windows-runtime-c-template-library-wrl"></a>UWP-apps, die die Windows-Runtime C++ Template Library (WRL) verwenden

Die Windows-Runtime C++-Vorlagen Bibliothek stellt die COM-Schnittstellen auf niedriger Ebene bereit, mit denen ISO C++-Code in einer Ausnahme freien Umgebung auf die Windows-Runtime zugreifen kann. In den meisten Fällen wird empfohlen, dass Sie C++/WinRT oder C++/CX anstelle der Windows-Runtime C++-Vorlagen Bibliothek für die UWP-App-Entwicklung verwenden. Weitere Informationen zur Windows-Runtime C++-Vorlagen Bibliothek finden Sie unter [Windows-Runtime C++ Template Library (WRL)](wrl/windows-runtime-cpp-template-library-wrl.md).

## <a name="see-also"></a>Weitere Informationen

[C++ in Visual Studio](../overview/visual-cpp-in-visual-studio.md)<br/>
[Übersicht über die Windows-Programmierung in C++](../windows/overview-of-windows-programming-in-cpp.md)<br/>
