---
title: partial (C++/CLI und C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- partial_CPP
helpviewer_keywords:
- partial
- C++/CX, partial
ms.assetid: 43adf1f5-10c5-44aa-a66f-7507e2bdabf8
ms.openlocfilehash: 37406060c3569c417c14bcc98561f8f52a7c6201
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2019
ms.locfileid: "79544399"
---
# <a name="partial--ccli-and-ccx"></a>partial (C++/CLI und C++/CX)

Das Schlüsselwort **partial** ermöglicht es, verschiedene Teile derselben Verweisklasse unabhängig voneinander und in verschiedenen Dateien zu erstellen.

## <a name="all-runtimes"></a>Alle Laufzeiten

(Dieses Sprachfeature gilt nur für die Windows-Runtime.)

## <a name="windows-runtime"></a>Windows-Runtime

Bei einer Verweisklasse mit zwei partielle Definitionen wird das Schlüsselwort **partial** auf das erste Vorkommen der Definition angewendet. Dies erfolgt in der Regel über automatisch generierten Code, daher wird ein menschlicher Programmierer dieses Schlüsselwort nicht sehr häufig verwenden. Lassen Sie bei allen nachfolgenden partiellen Definitionen der Klasse den Modifizierer **partial** im Schlüsselwort *class-key* und im Klassenbezeichner weg. Wenn der Compiler eine zuvor definierte Verweisklasse und einen Klassenbezeichner findet, aber kein **partial**-Schlüsselwort, kombiniert er intern alle Teile der Verweisklassendefinition in eine einzige Definition.

### <a name="syntax"></a>Syntax

```cpp
partial class-key identifier {
   /* The first part of the partial class definition.
      This is typically auto-generated */
}
// ...
class-key identifier {
   /* The subsequent part(s) of the class definition. The same
      identifier is specified, but the "partial" keyword is omitted. */
}
```

### <a name="parameters"></a>Parameter

*class-key*<br/>
Ein Schlüsselwort, das eine Klasse oder Struktur deklariert, die durch die Windows-Runtime unterstützt wird. **ref class**, **value class**, **ref struct** oder **value struct**.

*identifier*<br/>
Der Name des definierten Typs.

### <a name="remarks"></a>Hinweise

Eine partielle Klasse unterstützt Szenarien, in denen Sie einen Teil einer Klassendefinition in einer Datei ändern und Software für die automatische Codegenerierung – beispielsweise der XAML Designer – den Code in der gleichen Klasse in einer anderen Datei ändert. Durch Verwendung einer partiellen Klasse können Sie verhindern, dass der automatische Codegenerator Ihren Code überschreibt. In einem Visual Studio-Projekt wird der Modifizierer **partial** automatisch auf die generierte Datei angewendet.

Inhalt: mit zwei Ausnahmen kann eine partielle Klassendefinition alles enthalten, was die vollständige Klassendefinition enthalten kann, wenn das **partielle** Schlüsselwort ausgelassen wird. Sie können jedoch keinen Klassenzugriff (z.B. `public partial class X { ... };`) oder **declspec** angeben.

Zugriffsspezifizierer, die in einer partiellen Klassendefinition für *identifier* verwendet werden, wirken sich nicht auf den Standardzugriff in einer nachfolgenden partiellen oder vollständigen Klassendefinition für *identifier* aus. Inlinedefinitionen statischer Datenmember sind zulässig.

Deklaration: eine partielle Definition eines Klassen *Bezeichners* führt nur den namens *Bezeichner*ein, aber der *Bezeichner* kann nicht auf eine Weise verwendet werden, für die eine Klassendefinition erforderlich ist. Der *identifier* für den Namen kann nicht zur Größenbestimmung von *identifier* oder zur Verwendung einer Basisklasse oder eines Members von *identifier* verwendet werden, bis der Compiler die vollständige Definition von *identifier* findet.

Anzahl und Reihenfolge: Es können NULL oder mehr partielle Klassendefinitionen für den *Bezeichner*vorhanden sein. Jede partielle Klassendefinition von *identifier* muss lexikalisch einer vollständigen Definition von *identifier* vorangehen (sofern eine vollständige Definition vorhanden ist; andernfalls kann die Klasse außer bei Verwendung von „forward-declared“ nicht verwendet werden). Vorwärtsdeklarationen von *identifier* muss sie jedoch nicht vorangehen. Alle Klassenschlüssel müssen übereinstimmen.

Vollständige Definition: zum Zeitpunkt der vollständigen Definition des Klassen *Bezeichners*ist das Verhalten das gleiche wie, wenn die Definition des *Bezeichners* alle Basisklassen, Member usw. in der Reihenfolge deklariert hätte, in der Sie in der partiellen Klasse gefunden und definiert wurden.

Vorlagen: eine partielle Klasse kann keine Vorlage sein.

Generika: eine partielle Klasse kann eine generische Klasse sein, wenn die vollständige Definition generisch sein könnte. Allerdings muss jede partielle und vollständige Klasse exakt die gleichen generischen Parameter enthalten, einschließlich formaler Parameternamen.

Weitere Informationen zur Verwendung des Schlüsselworts **partial** finden Sie unter [Partielle Klassen (C++/CX)](https://go.microsoft.com/fwlink/p/?LinkId=249023).

### <a name="requirements"></a>Voraussetzungen

Compileroption: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

(Dieses Sprachfeature gilt nicht für die Common Language Runtime.)

## <a name="see-also"></a>Siehe auch

[Partielle Klassen (C++-CX)](https://go.microsoft.com/fwlink/p/?LinkId=249023)