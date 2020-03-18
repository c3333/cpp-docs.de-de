---
title: Ableiten einer Klasse von CObject
ms.date: 11/04/2016
helpviewer_keywords:
- DECLARE_DYNCREATE macro [MFC]
- DECLARE_SERIAL macro [MFC]
- macros [MFC], serialization
- serialization [MFC], macros
- DECLARE_DYNAMIC macro [MFC]
- derived classes [MFC], from CObject
- CObject class [MFC], deriving serializable classes
- CObject class [MFC], deriving from
ms.assetid: 5ea4ea41-08b5-4bd8-b247-c5de8c152a27
ms.openlocfilehash: 860af88512acb33ff3035b3a04609165953d80a8
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446978"
---
# <a name="deriving-a-class-from-cobject"></a>Ableiten einer Klasse von CObject

Dieser Artikel beschreibt die minimalen Schritte, die erforderlich sind, um eine Klasse von [CObject](../mfc/reference/cobject-class.md)abzuleiten. In anderen Artikeln der `CObject`-Klasse werden die Schritte beschrieben, die erforderlich sind, um bestimmte `CObject` Features zu nutzen, z. b. die Serialisierung und die Unterstützung

In den Erörterung von `CObject`werden die Begriffe "Schnittstellen Datei" und "Implementierungs Datei" häufig verwendet. Die Schnittstellen Datei (häufig als Header Datei bezeichnet) oder. H-Datei) enthält die Klassen Deklaration und alle anderen Informationen, die für die Verwendung der-Klasse erforderlich sind. Die Implementierungs Datei (oder. Cpp-Datei) enthält sowohl die Klassendefinition als auch den Code, der die Klassenmember-Funktionen implementiert. Beispielsweise würden Sie für eine Klasse mit dem Namen `CPerson`in der Regel eine Schnittstellen Datei namens Person erstellen. H und eine Implementierungs Datei mit dem Namen Person. CPP. Bei einigen kleinen Klassen, die nicht von Anwendungen gemeinsam genutzt werden, ist es manchmal einfacher, die Schnittstelle und die Implementierung in einem einzelnen zu kombinieren. Cpp-Datei.

Sie können zwischen vier Funktionsebenen wählen, wenn Sie eine Klasse von `CObject`ableiten:

- Grundlegende Funktionalität: keine Unterstützung für Lauf Zeit Klassen Informationen oder Serialisierung, aber auch für die Diagnose Speicherverwaltung.

- Grundlegende Funktionalität und Unterstützung von Lauf Zeit Klassen Informationen.

- Grundlegende Funktionalität Plus Unterstützung für Lauf Zeit Klassen Informationen und dynamische Erstellung.

- Grundlegende Funktionalität Plus Unterstützung für Lauf Zeit Klassen Informationen, dynamische Erstellung und Serialisierung.

Klassen, die für die Wiederverwendung vorgesehen sind (solche, die später als Basisklassen fungieren), sollten zumindest Lauf Zeit Klassen Unterstützung und Serialisierungsunterstützung einschließen, wenn eine zukünftige Serialisierungsanforderung erwartet wird.

Sie wählen den Funktionsumfang mithilfe spezifischer Deklarations-und Implementierungs Makros in der Deklaration und Implementierung der Klassen aus, die Sie von `CObject`ableiten.

Die folgende Tabelle zeigt die Beziehung zwischen den Makros, die zur Unterstützung von Serialisierungs-und Laufzeitinformationen verwendet werden.

### <a name="macros-used-for-serialization-and-run-time-information"></a>Makros, die für die Serialisierung und Laufzeitinformationen verwendet werden

|Verwendetes Makro|CObject:: IsKindOf|CRuntimeClass::<br /><br /> CreateObject|CArchive:: Operator > ><br /><br /> CArchive:: Operator < <|
|----------------|-----------------------|--------------------------------------|-------------------------------------------------------|
|Grundlegende `CObject` Funktionen|Nein|Nein|Nein|
|`DECLARE_DYNAMIC`|Ja|Nein|Nein|
|`DECLARE_DYNCREATE`|Ja|Ja|Nein|
|`DECLARE_SERIAL`|Ja|Ja|Ja|

#### <a name="to-use-basic-cobject-functionality"></a>So verwenden Sie die grundlegende CObject-Funktionalität

1. Leiten Sie die C++ Klasse mit der normalen Syntax aus `CObject` (oder aus einer von `CObject`abgeleiteten Klasse) ab.

   Das folgende Beispiel zeigt den einfachsten Fall, die Ableitung einer Klasse von `CObject`:

   [!code-cpp[NVC_MFCCObjectSample#1](../mfc/codesnippet/cpp/deriving-a-class-from-cobject_1.h)]

Normalerweise möchten Sie jedoch einige der Element Funktionen von `CObject`überschreiben, um die Besonderheiten der neuen Klasse zu behandeln. Beispielsweise können Sie die `Dump` Funktion von `CObject` überschreiben, um die Debugausgabe für den Inhalt Ihrer Klasse bereitzustellen. Ausführliche Informationen zum Überschreiben von `Dump`finden Sie im Artikel zur [Anpassung von Objekt](/previous-versions/visualstudio/visual-studio-2010/sc15kz85(v=vs.100))Abbildern. Möglicherweise möchten Sie auch die `AssertValid` Funktion von `CObject` überschreiben, um angepasste Tests zur Überprüfung der Konsistenz der Datenmember von Klassen Objekten bereitzustellen. Eine Beschreibung zum Überschreiben von `AssertValid`finden Sie unter [MFC ASSERT_VALID und CObject:: AssertValid](reference/diagnostic-services.md#assert_valid).

In diesem [Artikel wird](../mfc/specifying-levels-of-functionality.md) beschrieben, wie Sie andere Funktionsebenen angeben, einschließlich Lauf Zeit Klassen Informationen, dynamische Objekt Erstellung und Serialisierung.

## <a name="see-also"></a>Weitere Informationen

[Verwenden von CObject](../mfc/using-cobject.md)
