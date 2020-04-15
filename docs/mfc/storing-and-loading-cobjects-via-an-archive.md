---
title: Speichern und Laden eines CObject per Archiv
ms.date: 11/04/2016
helpviewer_keywords:
- CObjects [MFC], loading through archives
- CArchive class [MFC], storing and loading objects
- Serialize method, vs. CArchive operators
- CObject class [MFC], CArchive objects
- CObjects [MFC]
ms.assetid: a829b6dd-bc31-47e0-8108-fbb946722db9
ms.openlocfilehash: f1b59516d5bba13b6f5e006f91d8ebd560543b05
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372145"
---
# <a name="storing-and-loading-cobjects-via-an-archive"></a>Speichern und Laden eines CObject per Archiv

Das Speichern `CObject`und Laden von s über ein Archiv erfordert zusätzliche Berücksichtigung. In bestimmten Fällen sollten `Serialize` Sie die Funktion des `CArchive` Objekts aufrufen, `Serialize` wobei das Objekt ** < ** ein **>>** Parameter `CArchive`des Aufrufs ist, im Gegensatz zur Verwendung des oder-Operators des . Wichtig zu beachten ist, dass `CArchive` **>>** der Operator `CObject` den Speicher `CRuntimeClass` auf der Grundlage von Informationen erstellt, die zuvor vom Speicherndes Archiv in die Datei geschrieben wurden.

Daher hängt die `CArchive` ** < ** Frage ab, `Serialize`ob Sie die und-Operatoren **>>** im Vergleich zum Aufrufen `CRuntimeClass` verwenden, ob Sie das Ladearchiv *benötigen,* um das Objekt dynamisch basierend auf zuvor gespeicherten Informationen zu rekonstruieren. Verwenden `Serialize` Sie die Funktion in den folgenden Fällen:

- Wenn Sie das Objekt deserialisieren, kennen Sie die genaue Klasse des Objekts im Voraus.

- Beim Deserialisieren des Objekts ist ihnen bereits Arbeitsspeicher zugewiesen.

> [!CAUTION]
> Wenn Sie das Objekt `Serialize` mit der Funktion laden, `Serialize` müssen Sie das Objekt auch mit der Funktion speichern. Speichern Sie nicht `CArchive` **<<** mit dem Operator `Serialize` und laden Sie `Serialize` dann mit der `CArchive >>` Funktion, oder speichern Sie mit der Funktion und dann mit Operator laden.

Das folgende Beispiel veranschaulicht die Fälle:

[!code-cpp[NVC_MFCSerialization#36](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_1.h)]

[!code-cpp[NVC_MFCSerialization#37](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_2.cpp)]

Zusammenfassend lässt sich sagen, dass Sie, `CObject` wenn Ihre serialisierbare Klasse eine eingebettete Klasse als Member definiert, die `CArchive` ** < ** und **>>** Operatoren nicht für dieses Objekt *verwenden* sollten, sondern stattdessen die `Serialize` Funktion aufrufen sollten. Wenn ihre serialisierbare Klasse einen Zeiger `CObject` auf ein (oder `CObject`ein von ) abgeleitetes Objekt als Member definiert, dieses `Serialize`andere Objekt jedoch in einem eigenen Konstruktor erstellt, sollten Sie auch aufrufen .

## <a name="see-also"></a>Siehe auch

[Serialisierung: Serialisieren eines Objekts](../mfc/serialization-serializing-an-object.md)
