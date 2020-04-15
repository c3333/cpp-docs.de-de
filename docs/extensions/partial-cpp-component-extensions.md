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
ms.openlocfilehash: 42e8cc9a20c96e65ed3ddf73d562fe014bd9fa28
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349998"
---
# <a name="partial--ccli-and-ccx"></a>partial (C++/CLI und C++/CX)

Das Schlüsselwort **partial** ermöglicht es, verschiedene Teile derselben Verweisklasse unabhängig voneinander und in verschiedenen Dateien zu erstellen.

## <a name="all-runtimes"></a>Alle Laufzeiten

(Dieses Sprachfeature gilt nur für die Windows-Runtime.)

## <a name="windows-runtime"></a>Windows-Runtime

Bei einer Ref-Klasse mit zwei partiellen Definitionen wird das **partielle** Schlüsselwort auf das erste Vorkommen der Definition angewendet, und dies geschieht in der Regel durch automatisch generierten Code, sodass ein menschlicher Coder das Schlüsselwort nicht sehr häufig verwendet. Lassen Sie bei allen nachfolgenden partiellen Definitionen der Klasse den Modifizierer **partial** im Schlüsselwort *class-key* und im Klassenbezeichner weg. Wenn der Compiler eine zuvor definierte Verweisklasse und einen Klassenbezeichner findet, aber kein **partial**-Schlüsselwort, kombiniert er intern alle Teile der Verweisklassendefinition in eine einzige Definition.

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

*Bezeichner*<br/>
Der Name des definierten Typs.

### <a name="remarks"></a>Bemerkungen

Eine partielle Klasse unterstützt Szenarien, in denen Sie einen Teil einer Klassendefinition in einer Datei ändern und Software für die automatische Codegenerierung – beispielsweise der XAML Designer – den Code in der gleichen Klasse in einer anderen Datei ändert. Durch Verwendung einer partiellen Klasse können Sie verhindern, dass der automatische Codegenerator Ihren Code überschreibt. In einem Visual Studio-Projekt wird der Modifizierer **partial** automatisch auf die generierte Datei angewendet.

Inhalt: Mit zwei Ausnahmen kann eine partielle Klassendefinition alles enthalten, was die vollständige Klassendefinition enthalten könnte, wenn das **partielle** Schlüsselwort weggelassen wurde. Sie können jedoch keinen Klassenzugriff (z.B. `public partial class X { ... };`) oder **declspec** angeben.

Zugriffsspezifizierer, die in einer partiellen Klassendefinition für *identifier* verwendet werden, wirken sich nicht auf den Standardzugriff in einer nachfolgenden partiellen oder vollständigen Klassendefinition für *identifier* aus. Inlinedefinitionen statischer Datenmember sind zulässig.

Deklaration: Eine partielle Definition eines *Klassenbezeichners* führt nur den *Namensbezeichner*ein, aber *der Bezeichner* kann nicht in einer Weise verwendet werden, die eine Klassendefinition erfordert. Der *identifier* für den Namen kann nicht zur Größenbestimmung von *identifier* oder zur Verwendung einer Basisklasse oder eines Members von *identifier* verwendet werden, bis der Compiler die vollständige Definition von *identifier* findet.

Zahl und Reihenfolge: Es können null oder mehr partielle Klassendefinitionen für *Bezeichner*vorhanden sein. Jede partielle Klassendefinition von *identifier* muss lexikalisch einer vollständigen Definition von *identifier* vorangehen (sofern eine vollständige Definition vorhanden ist; andernfalls kann die Klasse außer bei Verwendung von „forward-declared“ nicht verwendet werden). Vorwärtsdeklarationen von *identifier* muss sie jedoch nicht vorangehen. Alle Klassenschlüssel müssen übereinstimmen.

Vollständige Definition: An der Stelle der vollständigen Definition des *Klassenbezeichners*ist das Verhalten das gleiche, als ob die Definition des *Bezeichners* alle Basisklassen, Member usw. in der Reihenfolge deklariert hätte, in der sie in den Teilklassen angetroffen und definiert wurden.

Vorlagen: Eine partielle Klasse kann keine Vorlage sein.

Generics: Eine partielle Klasse kann eine generische klasse sein, wenn die vollständige Definition generisch sein könnte. Allerdings muss jede partielle und vollständige Klasse exakt die gleichen generischen Parameter enthalten, einschließlich formaler Parameternamen.

Weitere Informationen zur Verwendung des Schlüsselworts **partial** finden Sie unter [Partielle Klassen (C++/CX)](https://go.microsoft.com/fwlink/p/?LinkId=249023).

### <a name="requirements"></a>Anforderungen

Compileroption: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

(Dieses Sprachfeature gilt nicht für die Common Language Runtime.)

## <a name="see-also"></a>Siehe auch

[Teilklassen (C++/CX)](https://go.microsoft.com/fwlink/p/?LinkId=249023)
