---
title: 'Exemplarische Vorgehensweise: Erstellen einer UWP-App mithilfe von WRL und Media Foundation'
ms.date: 04/23/2019
ms.topic: reference
ms.assetid: 0336c550-fbeb-4dc4-aa9b-660f9fc45382
ms.openlocfilehash: 272092982c5e9cc57f52043e08c8bd384c43ea96
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "82031510"
---
# <a name="walkthrough-creating-a-uwp-app-using-wrl-and-media-foundation"></a>Exemplarische Vorgehensweise: Erstellen einer UWP-App mithilfe von WRL und Media Foundation

> [!NOTE]
> Für neue UWP-Apps und -Komponenten wird empfohlen, [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/), eine neue Standard-C++17-Sprachprojektion für Windows-Runtime-APIs, zu verwenden. C++/WinRT ist ab Version 1803 im Windows 10 SDK verfügbar. C++/WinRT ist vollständig in Headerdateien implementiert und wurde entwickelt, um Ihnen erstklassigen Zugriff auf die moderne Windows-API zu bieten.

In diesem Tutorial erfahren Sie, wie Sie die Windows-Runtime-C++-Vorlagenbibliothek (WRL) verwenden, um eine UWP-App (Universelle Windows-Plattform) zu erstellen, die [Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk)verwendet.

In diesem Beispiel wird eine benutzerdefinierte Media Foundation-Transformation erstellt, in der ein Graustufeneffekt auf Bilder angewendet wird, die über eine Webcam erfasst werden.  Die App verwendet C++ zum Definieren der benutzerdefinierten Transformation und C# zum Verwenden der Komponente für das Transformieren der erfassten Bilder.

> [!NOTE]
> Anstelle von C# können Sie auch JavaScript, Visual Basic oder C++ verwenden, um die benutzerdefinierte Transformierenkomponente zu verwenden.

In den meisten Fällen können Sie C++/CX verwenden, um Windows-Runtime zu erstellen. Manchmal müssen Sie jedoch die WRL verwenden. Wenn Sie beispielsweise eine Medienerweiterung für Microsoft Media Foundation erstellen, müssen Sie eine Komponente erstellen, die sowohl COM- als auch Windows-Runtime-Schnittstellen implementiert. Da C++/CX nur Windows-Runtime-Objekte erstellen kann, müssen Sie zum Erstellen einer Medienerweiterung die WRL verwenden, da sie die Implementierung von COM- und Windows-Runtime-Schnittstellen ermöglicht.

> [!NOTE]
> Auch wenn dieses Codebeispiel lang ist, stellt es das erforderliche Minimum dar, um eine nützliche Media Foundation-Transformation zu erstellen. Sie können es als Ausgangspunkt für Ihre eigene benutzerdefinierte Transformation verwenden. Dieses Beispiel wird aus dem [Beispiel Medienerweiterungen](https://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096)angepasst, das Medienerweiterungen verwendet, um Effekte auf Videos anzuwenden, Videos zu dekodieren und Schemahandler zu erstellen, die Medienstreams erzeugen.

## <a name="prerequisites"></a>Voraussetzungen

- In Visual Studio 2017 und höher ist die UWP-Unterstützung eine optionale Komponente. Um es zu installieren, öffnen Sie Visual Studio Installer im Windows-Startmenü, und suchen Sie Ihre Version von Visual Studio. Wählen Sie **Ändern** aus, und stellen Sie dann sicher, dass die Kachel **"Universelle Windows-Plattformentwicklung"** aktiviert ist. Überprüfen Sie unter **Optionale Komponenten** **C++-Tools für UWP (v141)** für Visual Studio 2017 oder **C++-Tools für UWP (v142)** für Visual Studio 2019. Überprüfen Sie dann die Version des Windows SDK, das Sie verwenden möchten.

- Erfahrungen mit der [Windows-Runtime](/uwp/api/).

- Erfahrungen mit COM.

- Eine Webcam.

## <a name="key-points"></a>Wesentliche Punkte

- Verwenden Sie zum Erstellen einer benutzerdefinierten Media Foundation-Komponente eine MIDL-Definitionsdatei (Microsoft Interface Definition Language) zum Definieren einer Schnittstelle, Implementieren dieser Schnittstelle und zum Einstellen derselben, dass sie aus anderen Komponenten aktiviert werden kann.

- Die `namespace` `runtimeclass` Attribute und der `NTDDI_WIN8` [Versionsattributwert](/windows/win32/Midl/version) sind wichtige Bestandteile der MIDL-Definition für eine Media Foundation-Komponente, die WRL verwendet.

- [Microsoft::WRL::RuntimeClass](runtimeclass-class.md) ist die Basisklasse für die benutzerdefinierte Media Foundation-Komponente. Der [Microsoft::WRL::RuntimeClassType::WinRtClassicComMix-Enumwert,](runtimeclasstype-enumeration.md) der als Vorlagenargument bereitgestellt wird, markiert die Klasse für die Verwendung sowohl als Windows-Runtime-Klasse als auch als klassische COM-Laufzeitklasse.

- Das [InspectableClass-Makro](inspectableclass-macro.md) implementiert grundlegende COM-Funktionen `QueryInterface` wie Referenzzählung und die Methode und legt den Name und die Vertrauensstufe der Laufzeitklasse fest.

- Verwenden Sie die Microsoft::WRL::[Modulklasse,](module-class.md) um DLL-Einstiegspunktfunktionen wie [DllGetActivationFactory](/windows/win32/winrt/functions), [DllCanUnloadNow](/windows/win32/api/combaseapi/nf-combaseapi-dllcanunloadnow)und [DllGetClassObject](/windows/win32/api/combaseapi/nf-combaseapi-dllgetclassobject)zu implementieren.

- Verknüpfen Sie die Komponenten-DLL mit „runtimeobject.lib“. Geben Sie auch [/WINMD](../../cppcx/compiler-and-linker-options-c-cx.md) in der Linkerzeile an, um Windows-Metadaten zu generieren.

- Verwenden Sie Projektverweise, um WRL-Komponenten für UWP-Apps zugänglich zu machen.

### <a name="to-use-the-wrl-to-create-the-media-foundation-grayscale-transform-component"></a>So verwenden Sie die WRL zum Erstellen der Graustufentransformationskomponente media Foundation

1. Erstellen Sie in Visual Studio ein **Leereprojekt.** Benennen Sie das Projekt, z. B. *MediaCapture*.

1. Fügen Sie der Projektmappe ein **DLL-Projekt (Universal Windows)** hinzu. Benennen Sie das Projekt, z. B. *GrayscaleTransform*.

1. Fügen Sie dem Projekt eine **Midl-Dateidatei (.idl)** hinzu. Benennen Sie die Datei, z. B. *GrayscaleTransform.idl*.

1. Fügen Sie diesen Code zu GrayscaleTransform.idl hinzu:

   [!code-cpp[wrl-media-capture#1](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_1.idl)]

1. Verwenden Sie den folgenden Code, um den Inhalt von `pch.h`zu ersetzen:

   [!code-cpp[wrl-media-capture#2](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_2.h)]

1. Fügen Sie dem Projekt eine neue `BufferLock.h`Headerdatei hinzu, benennen Sie sie , und ersetzen Sie dann den Inhalt durch diesen Code:

   [!code-cpp[wrl-media-capture#3](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_3.h)]

1. `GrayscaleTransform.h`wird in diesem Beispiel nicht verwendet. Sie können ihn bei Bedarf aus dem Projekt entfernen.

1. Verwenden Sie den folgenden Code, um den Inhalt von `GrayscaleTransform.cpp`zu ersetzen:

   [!code-cpp[wrl-media-capture#4](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_4.cpp)]

1. Fügen Sie dem Projekt eine neue Moduldefinitionsdatei hinzu, benennen Sie sie `GrayscaleTransform.def`, und fügen Sie dann diesen Code hinzu:

   ```
   EXPORTS
       DllCanUnloadNow                     PRIVATE
       DllGetActivationFactory             PRIVATE
       DllGetClassObject                   PRIVATE
   ```

1. Verwenden Sie den folgenden Code, um den Inhalt von `dllmain.cpp`zu ersetzen:

   [!code-cpp[wrl-media-capture#6](../codesnippet/CPP/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_6.cpp)]

1. Legen Sie im Dialogfeld **Eigenschaftenseiten** des Projekts die folgenden **Linker-Eigenschaften** fest.

   1. Geben Sie unter **Eingabe**für `GrayScaleTransform.def`die **Moduldefinitionsdatei**an.

   1. Auch **Input**unter Eingabe `runtimeobject.lib` `mfuuid.lib`, `mfplat.lib` hinzufügen , und zur Eigenschaft **Zusätzliche Abhängigkeiten.**

   1. Legen Sie unter **Windows-Metadaten** **Windows-Metadaten** auf **Ja (/WINMD)** fest.

### <a name="to-use-the-wrl-the-custom-media-foundation-component-from-a-c-app"></a>So verwenden Sie die WRL-Komponente der benutzerdefinierten Media Foundation-Komponente aus einer C-App

1. Fügen Sie der `MediaCapture` Projektmappe ein neues Projekt für die leere App **(Universelle s)** hinzu. Benennen Sie das Projekt, z. B. *MediaCapture*.

1. Fügen Sie im **MediaCapture-Projekt** `GrayscaleTransform` einen Verweis auf das Projekt hinzu. Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen oder Entfernen von Referenzen mithilfe des Referenz-Managers](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager).

1. Wählen `Package.appxmanifest`Sie auf der Registerkarte **Funktionen** die Option **Mikrofon** und **Webcam**aus. Beide Funktionen sind erforderlich, um Fotos von der Webcam zu erfassen.

1. Fügen `MainPage.xaml`Sie diesen Code dem [Stammgrid-Element](/uwp/api/windows.ui.xaml.controls.grid) hinzu:

   [!code-xml[wrl-media-capture#7](../codesnippet/Xaml/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_7.xaml)]

1. Verwenden Sie den folgenden Code, um den Inhalt von `MainPage.xaml.cs`zu ersetzen:

   [!code-cs[wrl-media-capture#8](../codesnippet/CSharp/walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation_8.cs)]

Die folgende Abbildung `MediaCapture app`zeigt die .

![MediaCapture-App zeichnet ein Foto auf](../media/wrl_media_capture.png "WRL_Media_Capture")

## <a name="next-steps"></a>Nächste Schritte

Im Beispiel wird gezeigt, wie Fotos von der standardmäßigen Webcam nacheinander erfasst werden. Das [Beispiel für Medienerweiterungen](https://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096) führt mehr aus. Es veranschaulicht die Aufzählung von Webcamgeräten und die Arbeit mit lokalen Schemahandlern, und es veranschaulicht zusätzliche Medieneffekte, die bei einzelnen Fotos und Videostreams funktionieren.

## <a name="see-also"></a>Weitere Informationen

[Windows Runtime C++ Template Library (WRL)](windows-runtime-cpp-template-library-wrl.md)<br/>
[Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk)<br/>
[Beispiel für Medienerweiterungen](https://code.msdn.microsoft.com/windowsapps/Media-extensions-sample-7b466096)
