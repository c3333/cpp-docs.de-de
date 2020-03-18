---
title: Was ist ein CArchive-Objekt?
ms.date: 11/04/2016
helpviewer_keywords:
- archive objects [MFC]
- archives [MFC], for serialization
- buffers, serializable objects
- CArchive class [MFC], about CArchive class [MFC]
- buffering, serializable objects
ms.assetid: 843f1825-288d-4d89-a1fa-70e1f92d9b8b
ms.openlocfilehash: 0a78385c81c43a4b0c925bbe89ccd3937873ee8b
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446017"
---
# <a name="what-is-a-carchive-object"></a>Was ist ein CArchive-Objekt?

Ein `CArchive`-Objekt stellt einen typsicheren Puffer Mechanismus zum Schreiben oder Lesen von serialisierbaren Objekten in ein oder aus einem `CFile` Objekt bereit. Das `CFile`-Objekt stellt normalerweise eine Datenträger Datei dar. Es kann sich jedoch auch um eine Speicherdatei (`CSharedFile` Objekt) handeln, die möglicherweise die Zwischenablage darstellt.

Ein angegebenes `CArchive` Objekt speichert (schreibt, serialisiert) Daten oder lädt Sie (liest, deserialisiert), aber nicht beides. Die Lebensdauer eines `CArchive` Objekts ist auf einen Pass-Through-Vorgang zum Schreiben von Objekten in eine Datei oder zum Lesen von Objekten aus einer Datei beschränkt. Folglich sind zwei nacheinander erstellte `CArchive`-Objekte erforderlich, um Daten in eine Datei zu serialisieren und Sie dann wieder aus der Datei zu deserialisieren.

Wenn in einem Archiv Objekte in einer Datei gespeichert werden, fügt das Archiv den `CRuntimeClass` Namen an die-Objekte an. Wenn dann Objekte in einem anderen Archiv aus einer Datei in den Arbeitsspeicher geladen werden, werden die `CObject`von abgeleiteten Objekten basierend auf den `CRuntimeClass` der Objekte dynamisch rekonstruiert. Auf ein bestimmtes Objekt kann mehrmals verwiesen werden, da es durch das speichernde Archiv in die Datei geschrieben wird. Das Lade Archiv rekonstruiert das Objekt jedoch nur einmal. Die Details zur Vorgehensweise beim Anordnen von `CRuntimeClass` Informationen an Objekte und zum erneuten Konstruieren von Objekten, wobei möglicherweise mehrere Verweise berücksichtigt werden, werden in [Technical Note 2](../mfc/tn002-persistent-object-data-format.md)beschrieben.

Wenn Daten in ein Archiv serialisiert werden, akkumuliert das Archiv die Daten, bis der Puffer voll ist. Dann schreibt das Archiv seinen Puffer in das `CFile` Objekt, auf das das `CArchive` Objekt zeigt. Ebenso werden beim Lesen von Daten aus einem Archivdaten aus der Datei in den Puffer und dann aus dem Puffer in das deserialisierte Objekt gelesen. Diese Pufferung reduziert die Anzahl der physischen Lesevorgänge einer Festplatte und verbessert so die Leistung Ihrer Anwendung.

## <a name="see-also"></a>Weitere Informationen

[Serialisierung: Serialisieren eines Objekts](../mfc/serialization-serializing-an-object.md)
