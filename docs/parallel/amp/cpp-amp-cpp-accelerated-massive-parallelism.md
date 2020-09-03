---
title: C++ AMP (C++ Accelerated Massive Parallelism)
ms.date: 11/04/2016
helpviewer_keywords:
- C++ AMP (see C++ Accelerated Massive Parallelism)
- C++ Accelerated Massive Parallelism, getting started
ms.assetid: e27824cb-3167-409b-8c3f-a0e476d8f349
ms.openlocfilehash: 243c476b6536278eb09b26b24becb65276d6e48a
ms.sourcegitcommit: 093f49b8b69daf86661adc125b1d2d7b1f0e0650
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/03/2020
ms.locfileid: "89427633"
---
# <a name="c-amp-c-accelerated-massive-parallelism"></a>C++ AMP (C++ Accelerated Massive Parallelism)

(C++ AMP Accelerated Massive Parallelism) beschleunigt die Ausführung von C++-Code, indem die Vorteile Daten parallel verarbeitender Hardware, beispielsweise ein Grafikprozessor (Graphics Processing Unit, GPU) auf einer separaten Grafikkarte, genutzt werden. Das C++ AMP-Programmiermodell enthält Unterstützung für mehrdimensionale Arrays, Indizierung, Arbeitsspeicherübertragung und Tiling. Außerdem umfasst es eine Bibliothek mathematischer Funktionen. Mithilfe von C++ AMP-Sprachenerweiterungen können Sie steuern, wie Daten von der CPU auf die GPU bzw. zurück verschoben werden.

## <a name="related-topics"></a>Verwandte Themen

|Titel|Beschreibung|
|-----------|-----------------|
|[Übersicht über C++ amp](../../parallel/amp/cpp-amp-overview.md)|Beschreibt die Hauptfunktionen von C++ AMP und der mathematischen Bibliothek.|
|[Verwenden von Lambdas, Funktions Objekten und eingeschränkten Funktionen](../../parallel/amp/using-lambdas-function-objects-and-restricted-functions.md)|Beschreibt, wie Lambda-Ausdrücke, Funktions Objekte und eingeschränkte Funktionen in Aufrufen der [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) -Methode verwendet werden.|
|[Verwenden von Kacheln](../../parallel/amp/using-tiles.md)|Beschreibt, wie Unterteilungen verwendet werden, um den C++ AMP-Code beschleunigen.|
|[Verwenden von Accelerator-und accelerator_view Objekten](../../parallel/amp/using-accelerator-and-accelerator-view-objects.md)|Beschreibt, wie die Ausführung des Codes auf der GPU mithilfe von Beschleunigern angepasst werden kann.|
|[Verwenden von C++ amp in UWP-apps](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)|Beschreibt die Verwendung von C++ amp in universelle Windows-Plattform-Apps (UWP), die Windows-Runtime-Typen verwenden.|
|[Grafiken (C++ AMP)](../../parallel/amp/graphics-cpp-amp.md)|Beschreibt, wie die C++ AMP-Grafikbibliothek verwendet wird.|
|[Exemplarische Vorgehensweise: Matrix Multiplikation](../../parallel/amp/walkthrough-matrix-multiplication.md)|Veranschaulicht die Matrixmultiplikation mithilfe von C++ AMP-Code und Unterteilung.|
|[Exemplarische Vorgehensweise: Debuggen einer C++ AMP-Anwendung](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)|Erklärt, wie eine Anwendung erstellt und gedebuggt wird, die parallele Reduzierung verwendet, um ein großes Array von ganzen Zahlen aufzusummieren.|

## <a name="reference"></a>Verweis

[Referenz (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)<br/>
[tile_static-Schlüsselwort](../../cpp/tile-static-keyword.md)<br/>
[restrict (C++ AMP)](../../cpp/restrict-cpp-amp.md)

## <a name="other-resources"></a>Weitere Ressourcen

[Parallele Programmierung in nativem Code (Blog)](/archive/blogs/nativeconcurrency/)<br/>
[C++ amp Beispiel Projekte zum herunterladen](/archive/blogs/nativeconcurrency/c-amp-sample-projects-for-download)<br/>
[Analysieren von C++ amp-Code mit der neben läufigkeits Schnellansicht](/archive/blogs/nativeconcurrency/analyzing-c-amp-code-with-the-concurrency-visualizer)
