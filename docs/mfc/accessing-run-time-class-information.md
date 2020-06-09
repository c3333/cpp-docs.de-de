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
ms.openlocfilehash: a9f90640007f84c854d59cc27e0c38459c76fe46
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619198"
---
# <a name="accessing-run-time-class-information"></a>Zugreifen auf Laufzeit-Klasseninformationen

In diesem Artikel wird erläutert, wie Sie zur Laufzeit auf Informationen zur Klasse eines Objekts zugreifen.

> [!NOTE]
> MFC verwendet nicht die in Visual C++ 4,0 eingeführte rtti-Unterstützung ( [Run-Time Type Information](../cpp/run-time-type-information.md) ).

Wenn Sie die Klasse von [CObject](reference/cobject-class.md) abgeleitet und die Deklaration **_****Dynamic** und verwendet haben `IMPLEMENT_DYNAMIC` , und die Makros und, die `DECLARE_DYNCREATE` `IMPLEMENT_DYNCREATE` `DECLARE_SERIAL` `IMPLEMENT_SERIAL` im Artikel zum [Ableiten einer Klasse von CObject](deriving-a-class-from-cobject.md)erläutert wurden, kann die-Klasse die `CObject` exakte Klasse eines Objekts zur Laufzeit bestimmen.

Diese Funktion ist besonders nützlich, wenn eine zusätzliche Typüberprüfung von Funktions Argumenten erforderlich ist und wenn Sie speziellen Code basierend auf der Klasse eines Objekts schreiben müssen. Diese Vorgehensweise wird jedoch in der Regel nicht empfohlen, da Sie die Funktionalität von virtuellen Funktionen dupliziert.

Mithilfe der `CObject` Member-Funktion `IsKindOf` kann ermittelt werden, ob ein bestimmtes Objekt zu einer bestimmten Klasse gehört oder ob es von einer bestimmten Klasse abgeleitet ist. Das-Argument für `IsKindOf` ist ein- `CRuntimeClass` Objekt, das Sie mit dem- `RUNTIME_CLASS` Makro mit dem Namen der Klasse erhalten können.

### <a name="to-use-the-runtime_class-macro"></a>So verwenden Sie das RUNTIME_CLASS-Makro

1. Verwenden Sie `RUNTIME_CLASS` mit dem Namen der Klasse, wie hier für die-Klasse dargestellt `CObject` :

   [!code-cpp[NVC_MFCCObjectSample#4](codesnippet/cpp/accessing-run-time-class-information_1.cpp)]

Sie müssen selten direkt auf das Lauf Zeit Klassenobjekt zugreifen. Eine allgemeinere Verwendung besteht darin, das Lauf Zeit Klassenobjekt an die- `IsKindOf` Funktion zu übergeben, wie im folgenden Verfahren gezeigt. Die- `IsKindOf` Funktion testet ein Objekt, um festzustellen, ob es zu einer bestimmten Klasse gehört.

#### <a name="to-use-the-iskindof-function"></a>So verwenden Sie die IsKindOf-Funktion

1. Stellen Sie sicher, dass die Klasse über Lauf Zeit Klassen Unterstützung verfügt. Das heißt, die Klasse muss direkt oder indirekt von abgeleitet `CObject` werden und die Deklaration _**Dynamic** und, die-und **DECLARE** `IMPLEMENT_DYNAMIC` `DECLARE_DYNCREATE` `IMPLEMENT_DYNCREATE` `DECLARE_SERIAL` -Makros sowie die-und-Makros, die `IMPLEMENT_SERIAL` im Artikel [Ableiten einer Klasse von CObject](deriving-a-class-from-cobject.md)erläutert werden, verwenden.

1. Rufen `IsKindOf` Sie die Member-Funktion für Objekte dieser Klasse mithilfe des- `RUNTIME_CLASS` Makros auf, um das Argument zu generieren `CRuntimeClass` , wie hier gezeigt:

   [!code-cpp[NVC_MFCCObjectSample#2](codesnippet/cpp/accessing-run-time-class-information_2.h)]

   [!code-cpp[NVC_MFCCObjectSample#5](codesnippet/cpp/accessing-run-time-class-information_3.cpp)]

    > [!NOTE]
    >  IsKindOf gibt **true** zurück, wenn das Objekt ein Member der angegebenen Klasse oder einer von der angegebenen Klasse abgeleiteten Klasse ist. `IsKindOf`unterstützt nicht mehrere Vererbungs-oder virtuelle Basisklassen, obwohl Sie ggf. die mehrfache Vererbung für die abgeleiteten Microsoft Foundation-Klassen verwenden können.

Eine Verwendung von Lauf Zeit Klassen Informationen ist die dynamische Erstellung von Objekten. Dieser Prozess wird im Artikel [dynamische Objekt Erstellung](dynamic-object-creation.md)erläutert.

Ausführlichere Informationen zu Serialisierungs-und Lauf Zeit Klassen Informationen finden Sie in den Artikeln [Dateien in MFC](files-in-mfc.md) und [Serialisierung](serialization-in-mfc.md).

## <a name="see-also"></a>Siehe auch

[Verwenden von CObject](using-cobject.md)
