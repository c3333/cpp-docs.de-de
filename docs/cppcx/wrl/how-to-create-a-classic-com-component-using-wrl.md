---
title: 'Gewusst wie: Erstellen einer klassischen COM-Komponente mit WRL'
description: Verwenden Sie die Windows-Runtime C++ Template Library (WRL), um grundlegende klassische COM-Komponenten für die Verwendung in Desktop-Apps zu erstellen.
ms.date: 10/23/2020
ms.topic: reference
ms.openlocfilehash: 417c2e4635b380717662fa0762062f0228659de4
ms.sourcegitcommit: bf54b407169900bb668c85a67b31dbc0f069fe65
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92497202"
---
# <a name="how-to-create-a-classic-com-component-using-wrl"></a>Gewusst wie: Erstellen einer klassischen COM-Komponente mit WRL

Sie können die Windows-Runtime C++ Template Library (WRL) verwenden, um grundlegende klassische COM-Komponenten für die Verwendung in Desktop-Apps zu erstellen, zusätzlich zur Verwendung für universelle Windows-Plattform-Apps (UWP). Für die Erstellung von COM-Komponenten ist für die Windows-Runtime C++-Vorlagen Bibliothek möglicherweise weniger Code als für ATL erforderlich. Informationen über die Teilmenge von com, die von der Windows-Runtime C++-Vorlagen Bibliothek unterstützt wird, finden Sie unter [Windows-Runtime C++ Template Library (WRL)](windows-runtime-cpp-template-library-wrl.md).

In diesem Dokument wird gezeigt, wie Sie die Windows-Runtime C++-Vorlagen Bibliothek zum Erstellen einer grundlegenden COM-Komponente verwenden. Obwohl Sie den Bereitstellungsmechanismus, der für Ihre Anforderungen am besten geeignet ist, verwenden können, zeigt dieses Dokument auch eine einfache Möglichkeit zur Registrierung und Nutzung der COM-Komponente aus einer Desktop-App.

### <a name="to-use-the-windows-runtime-c-template-library-to-create-a-basic-classic-com-component"></a>So verwenden Sie die Windows-Runtime C++-Vorlagen Bibliothek zum Erstellen einer einfachen klassischen COM-Komponente

1. Erstellen Sie in Visual Studio ein **leeres** Projektmappenprojekt. Benennen Sie das Projekt, z `WRLClassicCOM` . b..

2. Fügen Sie der Projekt Mappe ein **Win32-Projekt** hinzu. Benennen Sie das Projekt, z `CalculatorComponent` . b.. Wählen Sie auf der Registerkarte **Anwendungseinstellungen** die Option **dll**aus.

3. Fügen Sie dem Projekt eine Datei mit **mittlerer l-Datei (. idl)** hinzu. Benennen Sie die Datei, z `CalculatorComponent.idl` . b..

4. Fügen Sie diesen Code zu CalculatorComponent.idl hinzu:

   [!code-cpp[wrl-classic-com-component#1](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_1.idl)]

5. Definieren Sie die `CalculatorComponent` Klasse in CalculatorComponent.cpp. Die `CalculatorComponent` Klasse erbt von [Microsoft:: WRL:: runtimeclass](runtimeclass-class.md). [Microsoft:: WRL:: runtimeclassflags \<ClassicCom> ](runtimeclassflags-structure.md) Gibt an, dass die Klasse von [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) und nicht von [iinspectable](/windows/win32/api/inspectable/nn-inspectable-iinspectable)abgeleitet ist. ( `IInspectable` ist nur für Windows-Runtime App-Komponenten verfügbar.) `CoCreatableClass` erstellt eine Factory für die-Klasse, die mit Funktionen wie z. b. [cokreateinstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)verwendet werden kann.

   [!code-cpp[wrl-classic-com-component#2](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_2.cpp)]

6. Verwenden Sie den folgenden Code, um den Code in zu ersetzen `dllmain.cpp` . Diese Datei definiert die DLL-Exportfunktionen. Diese Funktionen verwenden die [Microsoft:: WRL:: Module](module-class.md) -Klasse zum Verwalten der Klassenfactorys für das Modul.

   [!code-cpp[wrl-classic-com-component#3](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_3.cpp)]

7. Fügen Sie eine **Modul Definitionsdatei (. def)** zum Projekt hinzu. Benennen Sie die Datei, z `CalculatorComponent.def` . b.. Diese Datei gibt dem Linker die Namen der zu exportierenden Funktionen. Öffnen Sie das Dialogfeld **Eigenschaften Seiten** für das Projekt, und legen Sie dann unter **Konfigurations Eigenschaften**  >  **Linker**  >  **Eingabe**die Eigenschaft **Modul Definitionsdatei** auf die DEF-Datei fest.

8. Fügen Sie diesen Code zu CalculatorComponent.def hinzu:

    ```
    LIBRARY

    EXPORTS
        DllGetActivationFactory PRIVATE
        DllGetClassObject       PRIVATE
        DllCanUnloadNow         PRIVATE
    ```

9. Der Linker-Befehlszeile runtimeobject.lib hinzufügen. Weitere Informationen finden Sie unter [ `.Lib` Dateien als Eingabe](../../build/reference/dot-lib-files-as-linker-input.md)für den Linker.

### <a name="to-consume-the-com-component-from-a-desktop-app"></a>Nutzen Sie die COM-Komponente aus einer Desktop-App.

1. Registrieren Sie die COM-Komponente mit der Windows-Registrierung. Erstellen Sie zu diesem Zweck eine Registrierungseinträge-Datei, benennen Sie Sie `RegScript.reg` , und fügen Sie den folgenden Text hinzu. Ersetzen *\<dll-path>* Sie durch den Pfad der dll, z. – `C:\temp\WRLClassicCOM\Debug\CalculatorComponent.dll` ..

    ```
    Windows Registry Editor Version 5.00

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}]
    @="CalculatorComponent Class"

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}\InprocServer32]
    @="<dll-path>"
    "ThreadingModel"="Apartment"

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}\Programmable]

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}\TypeLib]
    @="{9D3E6826-CB8E-4D86-8B14-89F0D7EFCD01}"

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}\Version]
    @="1.0"
    ```

2. Führen Sie regscript. reg aus, oder fügen Sie es dem **Postbuildereignis**Ihres Projekts hinzu. Weitere Informationen finden Sie unter [Dialog Feld "Präbuildereignis/Postbuildereignis-Befehlszeile](/visualstudio/ide/reference/pre-build-event-post-build-event-command-line-dialog-box)".

3. Fügen Sie der Projekt Mappe ein **Win32-Konsolen Anwendungs** Projekt hinzu. Benennen Sie das Projekt, z `Calculator` . b..

4. Verwenden Sie diesen Code, um den Inhalt von zu ersetzen `Calculator.cpp` :

   [!code-cpp[wrl-classic-com-component#6](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_6.cpp)]

## <a name="robust-programming"></a>Stabile Programmierung

In diesem Dokument werden Standard-com-Funktionen verwendet, um zu veranschaulichen, dass Sie die Windows-Runtime C++-Vorlagen Bibliothek verwenden können, um eine COM-Komponente zu erstellen und für alle com-fähigen Technologien verfügbar zu machen. Sie können auch Windows-Runtime C++-Vorlagen Bibliothekstypen wie [Microsoft:: WRL:: comptr](comptr-class.md) in Ihrer Desktop-App verwenden, um die Lebensdauer von com und anderen Objekten zu verwalten. Im folgenden Code wird die Windows-Runtime C++-Vorlagen Bibliothek verwendet, um die Lebensdauer des `ICalculatorComponent` Zeigers zu verwalten. Die `CoInitializeWrapper` Klasse ist ein RAII-Wrapper, der sicherstellt, dass die COM-Bibliothek freigegeben wird und dass die Lebensdauer der COM-Bibliothek länger ist als die vom `ComPtr` intelligenten Zeiger-Objekt.

[!code-cpp[wrl-classic-com-component#7](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_7.cpp)]

## <a name="see-also"></a>Weitere Informationen

[Windows Runtime C++ Template Library (WRL)](windows-runtime-cpp-template-library-wrl.md)
