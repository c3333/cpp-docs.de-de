---
title: private (C++)
ms.date: 11/04/2016
f1_keywords:
- private_cpp
helpviewer_keywords:
- private keyword [C++]
ms.assetid: 94e99983-46a5-4e21-800c-28f8a7c6a8ff
ms.openlocfilehash: d6dc1ca309c096a4f5e857ade3d7550749991f3f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366208"
---
# <a name="private-c"></a>private (C++)

## <a name="syntax"></a>Syntax

```
private:
   [member-list]
private base-class
```

## <a name="remarks"></a>Bemerkungen

Wenn Sie einer Liste von Klassenmitgliedern vorangehen, gibt das **private** Schlüsselwort an, dass auf diese Member nur über Memberfunktionen und Freunde der Klasse zugegriffen werden kann. Dies gilt für alle Member, die bis zum nächsten Zugriffsspezifizierer oder am Ende der Klasse deklariert werden.

Wenn sie dem Namen einer Basisklasse voranstellt, gibt das **private** Schlüsselwort an, dass die öffentlichen und geschützten Member der Basisklasse private Member der abgeleiteten Klasse sind.

Der Standardzugriff von Membern einer Klasse ist privat. Der Standardzugriff der Member in einer Struktur oder Union ist öffentlich.

Der Standardzugriff einer Basisklasse ist bei Klassen privat und bei Strukturen öffentlich. Unions können keine Basisklassen aufweisen.

Weitere Informationen finden Sie unter [friend](../cpp/friend-cpp.md), [public](../cpp/public-cpp.md), [protected](../cpp/protected-cpp.md)und die Memberzugriffstabelle unter Steuern des Zugriffs [auf Klassenmitglieder](member-access-control-cpp.md).

## <a name="clr-specific"></a>"/clr"-spezifisch

In CLR-Typen können die C++-Zugriffsbezeichnerschlüsselwörter (**public**, **private**und **protected**) die Sichtbarkeit von Typen und Methoden in Bezug auf Assemblys beeinträchtigen. Weitere Informationen finden Sie unter [Member Zugriffssteuerung](member-access-control-cpp.md).

> [!NOTE]
> Dateien, die mit [/LN](../build/reference/ln-create-msil-module.md) kompiliert wurden, sind von diesem Verhalten nicht betroffen. In diesem Fall werden alle verwalteten Klassen (entweder "public" oder "private") angezeigt.

## <a name="end-clr-specific"></a>"/clr"-spezifisch – Ende

## <a name="example"></a>Beispiel

```cpp
// keyword_private.cpp
class BaseClass {
public:
   // privMem accessible from member function
   int pubFunc() { return privMem; }
private:
   void privMem;
};

class DerivedClass : public BaseClass {
public:
   void usePrivate( int i )
      { privMem = i; }   // C2248: privMem not accessible
                         // from derived class
};

class DerivedClass2 : private BaseClass {
public:
   // pubFunc() accessible from derived class
   int usePublic() { return pubFunc(); }
};

int main() {
   BaseClass aBase;
   DerivedClass aDerived;
   DerivedClass2 aDerived2;
   aBase.privMem = 1;     // C2248: privMem not accessible
   aDerived.privMem = 1;  // C2248: privMem not accessible
                          //    in derived class
   aDerived2.pubFunc();   // C2247: pubFunc() is private in
                          //    derived class
}
```

## <a name="see-also"></a>Siehe auch

[Steuern des Zugriffs auf Klassenmember](member-access-control-cpp.md)<br/>
[Keywords](../cpp/keywords-cpp.md)
