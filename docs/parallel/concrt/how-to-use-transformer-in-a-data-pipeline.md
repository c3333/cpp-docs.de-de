---
title: 'Gewusst wie: Verwenden von transformer in einer Datenpipeline'
ms.date: 11/04/2016
helpviewer_keywords:
- transformer class, example
- data pipelines, using transformer [Concurrency Runtime]
- using transformer in data pipelines [Concurrency Runtime]
ms.assetid: ca49cb3f-4dab-4b09-a9c9-d3a109ae4c29
ms.openlocfilehash: 4eb490ecf51abea324f20395279bff2d74b7af77
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215854"
---
# <a name="how-to-use-transformer-in-a-data-pipeline"></a>Gewusst wie: Verwenden von transformer in einer Datenpipeline

Dieses Thema enthält ein einfaches Beispiel, in dem gezeigt wird, wie die Klasse " [parallelcurrency:: Transformer](../../parallel/concrt/reference/transformer-class.md) " in einer Daten Pipeline verwendet wird. Ein vollständigeres Beispiel, in dem eine Daten Pipeline zum Ausführen der Bildverarbeitung verwendet wird, finden Sie unter Exemplarische Vorgehensweise [: Erstellen eines Bild Verarbeitungs Netzwerks](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).

*Data Pipelining* ist ein gängiges Muster bei der gleichzeitigen Programmierung. Eine Datenpipeline besteht aus einer Reihe von Phasen, wobei in jeder einzelnen Phase Arbeiten ausführt und das jeweilige Ergebnis dann an die nächste Phase weitergeleitet wird. Die `transformer`-Klasse ist eine Hauptkomponente in Datenpipelines, da sie einen Eingabewert empfängt, Arbeiten für diesen Wert ausführt und dann ein Ergebnis erzeugt, das von einer anderen Komponente verwendet werden kann.

## <a name="example"></a>Beispiel

Bei diesem Beispiel wird zur Ausführung einer Reihe von Transformationen, denen ein ursprünglicher Eingabewert zugrunde liegt, folgende Datenpipeline verwendet:

1. In der ersten Phase wird der absolute Wert der Eingabe berechnet.

1. In der zweiten Phase wird die Quadratwurzel der Eingabe berechnet.

1. In der dritten Phase wird das Quadrat der Eingabe berechnet.

1. In der vierten Phase wird die Eingabe negiert.

1. In der fünften Phase wird das Endergebnis in einen Meldungspuffer geschrieben.

Bei diesem Beispiel wird schließlich das Ergebnis der Pipeline auf der Konsole gedruckt.

[!code-cpp[concrt-data-pipeline#1](../../parallel/concrt/codesnippet/cpp/how-to-use-transformer-in-a-data-pipeline_1.cpp)]

Dieses Beispiel erzeugt die folgende Ausgabe:

```Output
The result is -42.
```

Es kommt bei einer Datenpipeline häufig vor, dass bei einer Phase ein Wert ausgegeben wird, dessen Typ sich vom Eingabewert unterscheidet. In diesem Beispiel nimmt die zweite Phase einen Wert vom Typ **`int`** als Eingabe auf und erzeugt die Quadratwurzel dieses Werts (a **`double`** ) als Ausgabe.

> [!NOTE]
> Die Datenpipeline in diesem Beispiel dient zur Veranschaulichung. Da der Arbeitsmehraufwand jedes Transformationsvorgangs gering ist, kann der Mehraufwand zum Ausführen der Meldungsübergabe die Vorteile einer Datenpipeline zunichte machen.

## <a name="compiling-the-code"></a>Kompilieren des Codes

Kopieren Sie den Beispielcode, und fügen Sie ihn in ein Visual Studio-Projekt ein. Alternativ dazu können Sie ihn auch in eine Datei mit dem Namen einfügen `data-pipeline.cpp` und dann den folgenden Befehl in einem Visual Studio-Eingabe Aufforderungs Fenster ausführen.

> **cl.exe/EHsc Data-Pipeline. cpp**

## <a name="see-also"></a>Weitere Informationen

[Asynchronous Agents Library](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Asynchrone Nachrichten Blöcke](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Exemplarische Vorgehensweise: Erstellen eines Bild Verarbeitungs Netzwerks](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)
