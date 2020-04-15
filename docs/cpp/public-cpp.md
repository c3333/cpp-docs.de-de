---
title: public (C++)
ms.date: 11/04/2016
f1_keywords:
- public_cpp
helpviewer_keywords:
- public keyword [C++]
ms.assetid: f3e10a59-39f6-4bcd-827e-3e99f8f89497
ms.openlocfilehash: bf8293c6a6cf12154b02979de08035807991052c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376050"
---
# <a name="public-c"></a>public (C++)

## <a name="syntax"></a>Syntax

```
public:
   [member-list]
public base-class
```

## <a name="remarks"></a>Bemerkungen

Wenn Sie einer Liste von **public** Klassenmitgliedern vorangehen, gibt das public-Schlüsselwort an, dass auf diese Member von jeder Funktion aus zugegriffen werden kann. Dies gilt für alle Member, die bis zum nächsten Zugriffsspezifizierer oder am Ende der Klasse deklariert werden.

Wenn sie dem Namen einer **public** Basisklasse voranstellt, gibt das public-Schlüsselwort an, dass die öffentlichen und geschützten Member der Basisklasse öffentliche bzw. geschützte Member der abgeleiteten Klasse sind.

Der Standardzugriff von Membern einer Klasse ist privat. Der Standardzugriff der Member in einer Struktur oder Union ist öffentlich.

Der Standardzugriff einer Basisklasse ist bei Klassen privat und bei Strukturen öffentlich. Unions können keine Basisklassen aufweisen.

Weitere Informationen finden Sie unter [privat](../cpp/private-cpp.md), [geschützt](../cpp/protected-cpp.md), [friend](../cpp/friend-cpp.md)und die Memberzugriffstabelle unter Steuern des Zugriffs [auf Klassenmitglieder](member-access-control-cpp.md).

## <a name="clr-specific"></a>"/clr"-spezifisch

In CLR-Typen können die C++-Zugriffsbezeichnerschlüsselwörter (**public**, **private**und **protected**) die Sichtbarkeit von Typen und Methoden in Bezug auf Assemblys beeinträchtigen. Weitere Informationen finden Sie unter [Member Zugriffssteuerung](member-access-control-cpp.md).

> [!NOTE]
> Dateien, die mit [/LN](../build/reference/ln-create-msil-module.md) kompiliert wurden, sind von diesem Verhalten nicht betroffen. In diesem Fall werden alle verwalteten Klassen (entweder "public" oder "private") angezeigt.

## <a name="end-clr-specific"></a>"/clr"-spezifisch – Ende

## <a name="example"></a>Beispiel

```cpp
// keyword_public.cpp
class BaseClass {
public:
   int pubFunc() { return 0; }
};

class DerivedClass : public BaseClass {};

int main() {
   BaseClass aBase;
   DerivedClass aDerived;
   aBase.pubFunc();       // pubFunc() is accessible
                          //    from any function
   aDerived.pubFunc();    // pubFunc() is still public in
                          //    derived class
}
```

## <a name="see-also"></a>Siehe auch

[Steuern des Zugriffs auf Klassenmember](member-access-control-cpp.md)<br/>
[Keywords](../cpp/keywords-cpp.md)
