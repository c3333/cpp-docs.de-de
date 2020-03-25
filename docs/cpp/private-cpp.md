---
title: private (C++)
ms.date: 11/04/2016
f1_keywords:
- private_cpp
helpviewer_keywords:
- private keyword [C++]
ms.assetid: 94e99983-46a5-4e21-800c-28f8a7c6a8ff
ms.openlocfilehash: 002a8ad2887bd711bc3654d8e8910e2bede889d4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177559"
---
# <a name="private-c"></a>private (C++)

## <a name="syntax"></a>Syntax

```
private:
   [member-list]
private base-class
```

## <a name="remarks"></a>Bemerkungen

Wenn eine Liste der Klassenmember vorangestellt ist, gibt das **private** -Schlüsselwort an, dass auf diese Member nur von Element Funktionen und Freunden der-Klasse zugegriffen werden kann. Dies gilt für alle Member, die bis zum nächsten Zugriffsspezifizierer oder am Ende der Klasse deklariert werden.

Wenn das **private** -Schlüsselwort dem Namen einer Basisklasse vorangestellt ist, gibt es an, dass die öffentlichen und geschützten Member der Basisklasse private Member der abgeleiteten Klasse sind.

Der Standardzugriff von Membern einer Klasse ist privat. Der Standardzugriff der Member in einer Struktur oder Union ist öffentlich.

Der Standardzugriff einer Basisklasse ist bei Klassen privat und bei Strukturen öffentlich. Unions können keine Basisklassen aufweisen.

Weitere Informationen finden Sie unter [Friend](../cpp/friend-cpp.md), [Public](../cpp/public-cpp.md), [Protected](../cpp/protected-cpp.md)und die Element Zugriffs Tabelle Untersteuern des [Zugriffs auf Klassenmember](member-access-control-cpp.md).

## <a name="clr-specific"></a>"/clr"-spezifisch

In CLR-Typen können C++ die Schlüsselwörter der Zugriffsspezifizierer (**Public**, **private**und **Protected**) die Sichtbarkeit von Typen und Methoden in Bezug auf Assemblys beeinflussen. Weitere Informationen finden Sie unter [Member Access Control](member-access-control-cpp.md).

> [!NOTE]
>  Mit [/ln](../build/reference/ln-create-msil-module.md) kompilierte Dateien sind von diesem Verhalten nicht betroffen. In diesem Fall werden alle verwalteten Klassen (entweder "public" oder "private") angezeigt.

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

## <a name="see-also"></a>Weitere Informationen

[Steuern des Zugriffs auf Klassenmember](member-access-control-cpp.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
