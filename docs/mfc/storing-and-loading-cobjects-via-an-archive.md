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
ms.openlocfilehash: 368421a86d6ff6fc70455edd0ea9a32e05645007
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446361"
---
# <a name="storing-and-loading-cobjects-via-an-archive"></a>Speichern und Laden eines CObject per Archiv

Das Speichern und Laden von `CObject`s über ein Archiv erfordert zusätzliche Überlegungen. In bestimmten Fällen sollten Sie die `Serialize`-Funktion des-Objekts aufrufen, wobei das `CArchive`-Objekt ein Parameter des `Serialize`-Aufrufes ist, im Gegensatz zur Verwendung des **<\<** oder **>>** Operators des `CArchive`. Wichtig zu beachten ist, dass der `CArchive` **>>** -Operator die `CObject` im Arbeitsspeicher erstellt, basierend auf `CRuntimeClass` Informationen, die zuvor vom speichernden Archiv in die Datei geschrieben wurden.

Unabhängig davon, ob Sie die `CArchive` **<\<** und **>>** -Operatoren verwenden, und das Aufrufen von `Serialize`, hängt davon ab, ob Sie das Lade Archiv *benötigen* , um das Objekt auf der Grundlage zuvor gespeicherter `CRuntimeClass` Informationen dynamisch zu rekonstruieren. Verwenden Sie die `Serialize`-Funktion in den folgenden Fällen:

- Wenn Sie das Objekt deserialisieren, kennen Sie die exakte Klasse des Objekts.

- Beim Deserialisieren des Objekts ist bereits Arbeitsspeicher zugeordnet.

> [!CAUTION]
>  Wenn Sie das Objekt mit der `Serialize`-Funktion laden, müssen Sie das Objekt auch mit der `Serialize`-Funktion speichern. Speichern Sie den `CArchive` **<<** -Operator nicht, und laden Sie dann mithilfe der `Serialize`-Funktion, oder speichern Sie mithilfe der `Serialize` Funktion, und laden Sie dann mithilfe `CArchive >>`-Operators.

Im folgenden Beispiel werden die Fälle veranschaulicht:

[!code-cpp[NVC_MFCSerialization#36](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_1.h)]

[!code-cpp[NVC_MFCSerialization#37](../mfc/codesnippet/cpp/storing-and-loading-cobjects-via-an-archive_2.cpp)]

Wenn die serialisierbare Klasse eine eingebettete `CObject` als Member definiert, sollten Sie die `CArchive`- **<\<** -und **>>** -Operatoren für dieses Objekt *nicht* verwenden, sondern stattdessen die `Serialize`-Funktion verwenden. Wenn die serialisierbare Klasse außerdem einen Zeiger auf eine `CObject` (oder ein Objekt, das von `CObject`abgeleitet ist) als Member definiert, aber dieses andere Objekt in einem eigenen Konstruktor erstellt, sollten Sie auch `Serialize`aufruft.

## <a name="see-also"></a>Weitere Informationen

[Serialisierung: Serialisieren eines Objekts](../mfc/serialization-serializing-an-object.md)
