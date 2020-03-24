---
title: final-Bezeichner
ms.date: 11/04/2016
f1_keywords:
- final_CPP
helpviewer_keywords:
- final Identifier
ms.assetid: 649866d0-79d4-449f-ab74-f84b911b79a3
ms.openlocfilehash: 93e8d9b0b445d1120ec15911eb763ae1d7d2d359
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188655"
---
# <a name="final-specifier"></a>final-Bezeichner

Sie können das Schlüsselwort **Final** verwenden, um virtuelle Funktionen festzulegen, die in einer abgeleiteten Klasse nicht überschrieben werden können. Sie können es auch verwenden, um Klassen festzulegen, die nicht vererbbar sind.

## <a name="syntax"></a>Syntax

```
function-declaration final;
class class-name final base-classes
```

## <a name="remarks"></a>Bemerkungen

**Final** ist kontextbezogen und hat nur dann eine besondere Bedeutung, wenn es nach einer Funktionsdeklaration oder einem Klassennamen verwendet wird. andernfalls handelt es sich nicht um ein reserviertes Schlüsselwort.

Wenn **Final** in Klassen Deklarationen verwendet wird, ist `base-classes` ein optionaler Teil der Deklaration.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird das Schlüsselwort **Final** verwendet, um anzugeben, dass eine virtuelle Funktion nicht überschrieben werden kann.

```cpp
class BaseClass
{
    virtual void func() final;
};

class DerivedClass: public BaseClass
{
    virtual void func(); // compiler error: attempting to
                         // override a final function
};
```

Informationen dazu, wie Sie angeben können, dass Element Funktionen überschrieben werden können, finden Sie unter [Überschreibungsspezifizierer](../cpp/override-specifier.md).

Im nächsten Beispiel wird das Schlüsselwort **Final** verwendet, um anzugeben, dass eine Klasse nicht vererbt werden kann.

```cpp
class BaseClass final
{
};

class DerivedClass: public BaseClass // compiler error: BaseClass is
                                     // marked as non-inheritable
{
};
```

## <a name="see-also"></a>Weitere Informationen

[Schlüsselwörter](../cpp/keywords-cpp.md)<br/>
[override-Bezeichner](../cpp/override-specifier.md)
