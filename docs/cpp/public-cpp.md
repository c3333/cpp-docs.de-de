---
title: public (C++)
ms.date: 11/04/2016
f1_keywords:
- public_cpp
helpviewer_keywords:
- public keyword [C++]
ms.assetid: f3e10a59-39f6-4bcd-827e-3e99f8f89497
ms.openlocfilehash: dd45430543ead7258096be8f3d8cef0141f27b4e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179191"
---
# <a name="public-c"></a>public (C++)

## <a name="syntax"></a>Syntax

```
public:
   [member-list]
public base-class
```

## <a name="remarks"></a>Bemerkungen

Wenn eine Liste von Klassenmembern vorangestellt ist, gibt das **Public** -Schlüsselwort an, dass auf diese Member von jeder beliebigen Funktion aus Dies gilt für alle Member, die bis zum nächsten Zugriffsspezifizierer oder am Ende der Klasse deklariert werden.

Wenn das **Public** -Schlüsselwort dem Namen einer Basisklasse vorangestellt ist, gibt es an, dass die öffentlichen und geschützten Member der Basisklasse öffentliche bzw. geschützte Member der abgeleiteten Klasse sind.

Der Standardzugriff von Membern einer Klasse ist privat. Der Standardzugriff der Member in einer Struktur oder Union ist öffentlich.

Der Standardzugriff einer Basisklasse ist bei Klassen privat und bei Strukturen öffentlich. Unions können keine Basisklassen aufweisen.

Weitere Informationen finden Sie unter " [private](../cpp/private-cpp.md)", " [Protected](../cpp/protected-cpp.md)", " [Friend](../cpp/friend-cpp.md)" und die Tabelle "Member-Access" unter [Steuern des Zugriffs auf Klassenmember](member-access-control-cpp.md).

## <a name="clr-specific"></a>"/clr"-spezifisch

In CLR-Typen können C++ die Schlüsselwörter der Zugriffsspezifizierer (**Public**, **private**und **Protected**) die Sichtbarkeit von Typen und Methoden in Bezug auf Assemblys beeinflussen. Weitere Informationen finden Sie unter [Member Access Control](member-access-control-cpp.md).

> [!NOTE]
>  Mit [/ln](../build/reference/ln-create-msil-module.md) kompilierte Dateien sind von diesem Verhalten nicht betroffen. In diesem Fall werden alle verwalteten Klassen (entweder "public" oder "private") angezeigt.

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

## <a name="see-also"></a>Weitere Informationen

[Steuern des Zugriffs auf Klassenmember](member-access-control-cpp.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
