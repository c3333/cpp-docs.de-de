---
title: Zugreifen auf Laufzeit-Klasseninformationen
ms.date: 11/04/2016
helpviewer_keywords:
- CObject class [MFC], and RTTI
- CObject class [MFC], using IsKindOf method [MFC]
- run time [MFC], class information
- RUNTIME_CLASS macro [MFC]
- CObject class [MFC], using RUNTIME_CLASS macro [MFC]
- RTTI compiler option [MFC]
- CObject class [MFC], accessing run-time class information
- run time [MFC]
- IsKindOf method method [MFC]
- run-time class [MFC], accessing information
- classes [MFC], run-time class information
- run-time class [MFC]
- RUNTIME_CLASS macro, using
ms.assetid: 3445a9af-0bd6-4496-95c3-aa59b964570b
ms.openlocfilehash: 4a836bb7bd03bd6654e5c940442fecf541042fd1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354225"
---
# <a name="accessing-run-time-class-information"></a>Zugreifen auf Laufzeit-Klasseninformationen

In diesem Artikel wird erläutert, wie Sie zur Laufzeit auf Informationen über die Klasse eines Objekts zugreifen.

> [!NOTE]
> MFC verwendet nicht die [RTTI-Unterstützung (Run-Time Type Information),](../cpp/run-time-type-information.md) die in Visual C++ 4.0 eingeführt wurde.

Wenn Sie Ihre Klasse von [CObject](../mfc/reference/cobject-class.md) abgeleitet haben `IMPLEMENT_DYNAMIC`und `DECLARE_DYNCREATE` `IMPLEMENT_DYNCREATE`die DECLARE `DECLARE_SERIAL` `IMPLEMENT_SERIAL` _**DYNAMIC** und , die und oder die `CObject` und-Makros verwendet haben, die im Artikel [Derivieren einer Klasse von CObject](../mfc/deriving-a-class-from-cobject.md)erläutert werden, hat die Klasse die Möglichkeit, die genaue Klasse eines Objekts zur Laufzeit zu bestimmen. **DECLARE**

Diese Funktion ist besonders nützlich, wenn eine zusätzliche Typprüfung von Funktionsargumenten erforderlich ist und wenn Sie zweckgebundenen Code basierend auf der Klasse eines Objekts schreiben müssen. Diese Vorgehensweise wird jedoch in der Regel nicht empfohlen, da sie die Funktionalität virtueller Funktionen dupliziert.

Die `CObject` Memberfunktion `IsKindOf` kann verwendet werden, um zu bestimmen, ob ein bestimmtes Objekt zu einer angegebenen Klasse gehört oder ob es von einer bestimmten Klasse abgeleitet wird. Das Argument `IsKindOf` für `CRuntimeClass` ist ein Objekt, `RUNTIME_CLASS` das Sie mit dem Makro mit dem Namen der Klasse erhalten können.

### <a name="to-use-the-runtime_class-macro"></a>So verwenden Sie das RUNTIME_CLASS-Makro

1. Verwenden `RUNTIME_CLASS` Sie den Namen der Klasse, wie `CObject`hier für die Klasse gezeigt:

   [!code-cpp[NVC_MFCCObjectSample#4](../mfc/codesnippet/cpp/accessing-run-time-class-information_1.cpp)]

Sie müssen selten direkt auf das Laufzeitklassenobjekt zugreifen. Eine häufigere Verwendung besteht darin, das Laufzeitklassenobjekt an die `IsKindOf` Funktion zu übergeben, wie in der nächsten Prozedur gezeigt. Die `IsKindOf` Funktion testet ein Objekt, um festzustellen, ob es zu einer bestimmten Klasse gehört.

#### <a name="to-use-the-iskindof-function"></a>So verwenden Sie die IsKindOf-Funktion

1. Stellen Sie sicher, dass die Klasse über Die Unterstützung der Laufzeitklasse verfügt. Das heißt, die Klasse muss direkt oder `CObject` indirekt von **DECLARE**_ `DECLARE_DYNCREATE` `IMPLEMENT_DYNCREATE`**DYNAMIC** `IMPLEMENT_DYNAMIC`und `DECLARE_SERIAL` `IMPLEMENT_SERIAL` , die und oder die und-Makros abgeleitet und verwendet worden sein, die im Artikel [Ableiten einer Klasse von CObject](../mfc/deriving-a-class-from-cobject.md)erläutert werden.

1. Rufen `IsKindOf` Sie die Memberfunktion für Objekte `RUNTIME_CLASS` dieser Klasse `CRuntimeClass` auf, indem Sie das Makro verwenden, um das Argument zu generieren, wie hier gezeigt:

   [!code-cpp[NVC_MFCCObjectSample#2](../mfc/codesnippet/cpp/accessing-run-time-class-information_2.h)]

   [!code-cpp[NVC_MFCCObjectSample#5](../mfc/codesnippet/cpp/accessing-run-time-class-information_3.cpp)]

    > [!NOTE]
    >  IsKindOf gibt **TRUE** zurück, wenn das Objekt ein Member der angegebenen Klasse oder einer von der angegebenen Klasse abgeleiteten Klasse ist. `IsKindOf`unterstützt keine mehreren Vererbungs- oder virtuellen Basisklassen, obwohl Sie bei Bedarf mehrere Vererbungen für Ihre abgeleiteten Microsoft Foundation-Klassen verwenden können.

Eine Verwendung von Laufzeitklasseninformationen ist die dynamische Erstellung von Objekten. Dieser Prozess wird im Artikel [Dynamische Objekterstellung](../mfc/dynamic-object-creation.md)erläutert.

Ausführlichere Informationen zu Serialisierungundlaufzeitklasseninformationen finden Sie in den Artikeln [Dateien in MFC](../mfc/files-in-mfc.md) und [Serialisierung](../mfc/serialization-in-mfc.md).

## <a name="see-also"></a>Siehe auch

[Verwenden von CObject](../mfc/using-cobject.md)
