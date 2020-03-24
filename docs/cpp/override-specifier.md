---
title: override-Bezeichner
ms.date: 11/04/2016
helpviewer_keywords:
- override Identifier
ms.assetid: b286fb46-9374-4ad8-b2e7-4607119b6133
ms.openlocfilehash: 82837ae34ab786e607df54038493b14350574a15
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188479"
---
# <a name="override-specifier"></a>override-Bezeichner

Sie können das **override** -Schlüsselwort verwenden, um Member-Funktionen anzugeben, die eine virtuelle Funktion in einer Basisklasse überschreiben.

## <a name="syntax"></a>Syntax

```
function-declaration override;
```

## <a name="remarks"></a>Bemerkungen

die **außer Kraft** Setzung ist kontextbezogen und hat nur dann eine besondere Bedeutung, wenn Sie nach einer Element Funktionsdeklaration verwendet wird. andernfalls handelt es sich nicht um ein reserviertes Schlüsselwort.

## <a name="example"></a>Beispiel

Verwenden Sie **override** , um unbeabsichtigtes Vererbungs Verhalten in Ihrem Code zu verhindern. Im folgenden Beispiel wird gezeigt, wo ohne **Überschreibung**das Verhalten der Funktion der abgeleiteten Klasse möglicherweise nicht beabsichtigt ist. Der Compiler gibt keinen Fehler für diesen Code aus.

```cpp
class BaseClass
{
    virtual void funcA();
    virtual void funcB() const;
    virtual void funcC(int = 0);
    void funcD();
};

class DerivedClass: public BaseClass
{
    virtual void funcA(); // ok, works as intended

    virtual void funcB(); // DerivedClass::funcB() is non-const, so it does not
                          // override BaseClass::funcB() const and it is a new member function

    virtual void funcC(double = 0.0); // DerivedClass::funcC(double) has a different
                                      // parameter type than BaseClass::funcC(int), so
                                      // DerivedClass::funcC(double) is a new member function
};
```

Wenn Sie **override**verwenden, generiert der Compiler Fehler, anstatt automatisch neue Member-Funktionen zu erstellen.

```cpp
class BaseClass
{
    virtual void funcA();
    virtual void funcB() const;
    virtual void funcC(int = 0);
    void funcD();
};

class DerivedClass: public BaseClass
{
    virtual void funcA() override; // ok

    virtual void funcB() override; // compiler error: DerivedClass::funcB() does not
                                   // override BaseClass::funcB() const

    virtual void funcC( double = 0.0 ) override; // compiler error:
                                                 // DerivedClass::funcC(double) does not
                                                 // override BaseClass::funcC(int)

    void funcD() override; // compiler error: DerivedClass::funcD() does not
                           // override the non-virtual BaseClass::funcD()
};
```

Um anzugeben, dass Funktionen nicht überschrieben werden können und Klassen nicht vererbt werden können, verwenden Sie das Schlüsselwort [Final](../cpp/final-specifier.md) .

## <a name="see-also"></a>Weitere Informationen

[final-Bezeichner](../cpp/final-specifier.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
