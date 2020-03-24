---
title: 'Gewusst wie: Aktivieren und Verwenden einer Windows-Runtime-Komponente mit WRL'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 54828f02-6af3-45d1-b965-d0104442f8d5
ms.openlocfilehash: 7f49c1362bea12576df6039b9e9f0b455cb4fae4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213953"
---
# <a name="how-to-activate-and-use-a-windows-runtime-component-using-wrl"></a>Gewusst wie: Aktivieren und Verwenden einer Windows-Runtime-Komponente mit WRL

In diesem Dokument wird gezeigt, wie Sie C++ die Windows-Runtime Template Library (WRL) verwenden, um die Windows-Runtime zu initialisieren und eine Windows-Runtime Komponente zu aktivieren und zu verwenden.

Um eine Komponente zu verwenden, müssen Sie einen Schnittstellenzeiger auf den Typ abrufen, der von der Komponente implementiert wird. Und da es sich bei der zugrunde liegenden Technologie des Windows-Runtime um die Component Object Model (com) handelt, müssen Sie den com-Regeln folgen, um eine Instanz des Typs beizubehalten. Beispielsweise müssen Sie den *Verweis Zähler* verwalten, der bestimmt, wann der Typ aus dem Arbeitsspeicher gelöscht wird.

Um die Verwendung des Windows-Runtime zu vereinfachen, bietet C++ Windows-Runtime Vorlagen Bibliothek die Vorlage für den intelligenten Zeiger, [comptr\<t >](comptr-class.md), die automatisch eine Verweis Zählung ausführt. Wenn Sie eine Variable deklarieren, geben Sie `ComPtr<`*Schnittstellennamen*`>` *Bezeichners*an. Um auf einen Schnittstellenmember zuzugreifen, wenden Sie den Pfeilmemberzugriffsoperator (`->`) auf den Bezeichner an.

> [!IMPORTANT]
> Wenn Sie eine Schnittstellenfunktion aufgerufen haben, testen Sie immer den HRESULT-Rückgabewert.

## <a name="activating-and-using-a-windows-runtime-component"></a>Aktivieren und Verwenden einer Windows Runtime-Komponente

In den folgenden Schritten wird die `Windows::Foundation::IUriRuntimeClass`-Schnittstelle verwendet, um zu veranschaulichen, wie eine aktivierungfactory für eine Windows-Runtime Komponente erstellt, eine Instanz dieser Komponente erstellt und ein Eigenschafts Wert abgerufen wird. Außerdem wird gezeigt, wie die Windows-Runtime initialisiert wird. Im Folgenden finden Sie das vollständige Beispiel.

> [!IMPORTANT]
> Obwohl Sie in der Regel die C++ Windows-Runtime Vorlagen Bibliothek in einer universelle Windows-Plattform-app (UWP) verwenden, wird in diesem Beispiel eine Konsolen-App zur Veranschaulichung verwendet. Funktionen wie `wprintf_s` sind in einer UWP-APP nicht verfügbar. Weitere Informationen zu den Typen und Funktionen, die Sie in einer UWP-App verwenden können, finden Sie unter CRT-Funktionen, die in universelle Windows-Plattform-apps und [Win32 und com für UWP-apps](/uwp/win32-and-com/win32-and-com-for-uwp-apps) [nicht unterstützt](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) werden.

#### <a name="to-activate-and-use-a-windows-runtime-component"></a>So aktivieren und verwenden Sie eine Windows Runtime-Komponente

1. Fügen Sie (`#include`) alle erforderlichen Windows-Runtime, C++ Windows-Runtime Vorlagen Bibliothek oder C++ Standard Bibliotheks Header ein.

   [!code-cpp[wrl-consume-component#2](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_1.cpp)]

   Es wird empfohlen, den Code mithilfe der `using namespace`-Direktive in der CPP-Datei verständlicher zu gestalten.

2. Initialisieren Sie den Thread, in dem die App ausgeführt wird. Jede App muss ihren Thread und ihr Threadingmodell initialisieren. In diesem Beispiel wird die [Microsoft:: WRL:: Wrappers:: roinitializewrapper](roinitializewrapper-class.md) -Klasse verwendet, um die Windows-Runtime zu initialisieren und [RO_INIT_MULTITHREADED](/windows/win32/api/roapi/ne-roapi-ro_init_type) als Threading Modell festgelegt. Die `RoInitializeWrapper`-Klasse ruft `Windows::Foundation::Initialize` auf, wenn sie erstellt, und `Windows::Foundation::Uninitialize`, wenn sie zerstört wird.

   [!code-cpp[wrl-consume-component#3](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_2.cpp)]

   In der zweiten Anweisung gibt der [roinitializewrapper:: HRESULT](roinitializewrapper-class.md#hresult) -Operator die `HRESULT` vom Aufruf`Windows::Foundation::Initialize`zurück.

3. Erstellen Sie eine *aktivierungsfactory* für die `ABI::Windows::Foundation::IUriRuntimeClassFactory`-Schnittstelle.

   [!code-cpp[wrl-consume-component#4](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_3.cpp)]

   Der Windows-Runtime verwendet voll qualifizierte Namen, um Typen zu identifizieren. Der `RuntimeClass_Windows_Foundation_Uri`-Parameter ist eine Zeichenfolge, die vom Windows-Runtime bereitgestellt wird und den erforderlichen Lauf Zeit Klassennamen enthält.

4. Initialisieren Sie eine [Microsoft:: WRL:: Wrappers:: hstring](hstring-class.md) -Variable, die den URI-`"https://www.microsoft.com"`darstellt.

   [!code-cpp[wrl-consume-component#6](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_4.cpp)]

   In der Windows-Runtime weisen Sie keinen Arbeitsspeicher für eine Zeichenfolge zu, die der Windows-Runtime verwenden wird. Stattdessen erstellt die Windows-Runtime eine Kopie der Zeichenfolge in einem Puffer, den Sie verwaltet und für Vorgänge verwendet, und gibt dann ein Handle für den Puffer zurück, den Sie erstellt hat.

5. Erstellen Sie mit der `IUriRuntimeClassFactory::CreateUri`-Factorymethode ein `ABI::Windows::Foundation::IUriRuntimeClass`-Objekt.

   [!code-cpp[wrl-consume-component#7](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_5.cpp)]

6. Rufen Sie die `IUriRuntimeClass::get_Domain`-Methode auf, um den Wert der `Domain`-Eigenschaft abzurufen.

   [!code-cpp[wrl-consume-component#8](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_6.cpp)]

7. Drucken Sie den Domänennamen an die Konsole, und kehren Sie zurück. Alle `ComPtr`- und RAII-Objekte verlassen den Bereich und werden automatisch freigegeben.

   [!code-cpp[wrl-consume-component#9](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_7.cpp)]

   Die [windowsgetstringrawbuffer](/windows/win32/api/winstring/nf-winstring-windowsgetstringrawbuffer) -Funktion Ruft die zugrunde liegende Unicode-Form der URI-Zeichenfolge ab.

Im Folgenden sehen Sie das vollständige Beispiel:

[!code-cpp[wrl-consume-component#1](../codesnippet/CPP/how-to-activate-and-use-a-windows-runtime-component-using-wrl_8.cpp)]

## <a name="compiling-the-code"></a>Kompilieren des Codes

Um den Code zu kompilieren, kopieren Sie ihn, und fügen Sie ihn in ein Visual Studio-Projekt ein, oder fügen Sie ihn in eine Datei mit dem Namen `wrl-consume-component.cpp` ein, und führen Sie dann den folgenden Befehl in einem Visual Studio-Eingabe Aufforderungs Fenster aus.

`cl.exe wrl-consume-component.cpp runtimeobject.lib`

## <a name="see-also"></a>Weitere Informationen

[C++-Vorlagenbibliothek für Windows-Runtime (WRL)](windows-runtime-cpp-template-library-wrl.md)
