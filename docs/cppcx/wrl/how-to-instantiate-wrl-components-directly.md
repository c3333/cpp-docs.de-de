---
title: 'Gewusst wie: Direktes Instanziieren von WRL-Komponenten'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1a9fa011-0cee-4abf-bf83-49adf53ff906
ms.openlocfilehash: f291e982d7f77c63821e5943a5867662ccd1b4fa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213901"
---
# <a name="how-to-instantiate-wrl-components-directly"></a>Gewusst wie: Direktes Instanziieren von WRL-Komponenten

Erfahren Sie, wie Sie mithilfe C++ der Funktionen der Windows-Runtime Template Library (WRL)[Microsoft:: WRL:: Make](make-function.md) und [Microsoft:: WRL::D etails:: makeandinitialize](makeandinitialize-function.md) eine Komponente aus dem Modul instanziieren, das Sie definiert.

Durch die direkte Instanziierung von Komponenten können Sie den Mehraufwand reduzieren, wenn Klassenfactorys oder andere Mechanismen nicht benötigt werden. Sie können eine Komponente direkt in universelle Windows-Plattform-apps und in Desktop-Apps instanziieren.

Informationen zur Verwendung Windows-Runtime C++ Vorlagen Bibliothek zum Erstellen einer klassischen COM-Komponente und zum Instanziieren dieser Komponente über eine externe Desktop-App finden Sie unter Gewusst [wie: Erstellen einer klassischen COM-Komponente](how-to-create-a-classic-com-component-using-wrl.md).

Dieses Dokument enthält zwei Beispiele. Im ersten Beispiel wird eine Komponente mit der `Make`-Funktion instanziiert. Im zweiten Beispiel wird eine Komponente mit der `MakeAndInitialize`-Funktion instanziiert, die bei der Erstellung einen Fehler verursachen kann. (Da com in der Regel HRESULT-Werte verwendet, anstatt Ausnahmen anzugeben, löst ein com-Typ in der Regel nicht den Konstruktor aus. `MakeAndInitialize` ermöglicht einer Komponente, die Konstruktions Argumente mithilfe der `RuntimeClassInitialize`-Methode zu überprüfen.) In beiden Beispielen wird eine grundlegende Protokollierungs Schnittstelle definiert und diese Schnittstelle implementiert, indem eine Klasse definiert wird, die Meldungen in die Konsole schreibt.

> [!IMPORTANT]
> Sie können den `new`-Operator nicht verwenden, um Windows-Runtime C++ Vorlagen Bibliotheks Komponenten zu instanziieren. Daher wird empfohlen, die direkte Instanziierung von Komponenten stets mit `Make` oder `MakeAndInitialize` vorzunehmen.

### <a name="to-create-and-instantiate-a-basic-logger-component"></a>So erstellen und instanziieren Sie eine einfache Protokollierungskomponente

1. Erstellen Sie in Visual Studio ein **Win32-Konsolen Anwendungs** Projekt. Geben Sie dem Projekt einen Namen, z. b. *wrllogger*.

2. Fügen Sie dem Projekt eine Datei mit **mittlerer l-Datei (. idl)** hinzu, benennen Sie die Datei `ILogger.idl`, und fügen Sie dann den folgenden Code hinzu:

   [!code-cpp[wrl-logger-make#1](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_1.idl)]

3. Verwenden Sie den folgenden Code, um die Inhalte `WRLLogger.cpp`zu ersetzen.

   [!code-cpp[wrl-logger-make#2](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_2.cpp)]

### <a name="to-handle-construction-failure-for-the-basic-logger-component"></a>So behandeln Sie Konstruktionsfehler für die grundlegende Protokollierungskomponente

1. Ersetzen Sie die Definition der `CConsoleWriter`-Klasse durch folgenden Code. Diese Version enthält eine private Zeichenfolgenmembervariable und überschreibt die `RuntimeClass::RuntimeClassInitialize`-Methode. `RuntimeClassInitialize` schlägt fehl, wenn der `SHStrDup` Fehler auftritt.

   [!code-cpp[wrl-logger-makeandinitialize#1](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_3.cpp)]

2. Ersetzen Sie die Definition von `wmain` durch folgenden Code. Diese Version verwendet `MakeAndInitialize`, um das `CConsoleWriter` Objekt zu instanziieren und das HRESULT-Ergebnis zu überprüfen.

   [!code-cpp[wrl-logger-makeandinitialize#2](../codesnippet/CPP/how-to-instantiate-wrl-components-directly_4.cpp)]

## <a name="see-also"></a>Weitere Informationen

[C++-Vorlagenbibliothek für Windows-Runtime (WRL)](windows-runtime-cpp-template-library-wrl.md)<br/>
[Microsoft:: WRL:: Make](make-function.md)<br/>
[Microsoft:: WRL::D etails:: makeandinitialize](makeandinitialize-function.md)
