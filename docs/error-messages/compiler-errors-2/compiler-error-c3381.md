---
title: Compilerfehler C3381
description: Microsoft C++-Compilerfehler C3381, seine Ursache und deren Behebung.
ms.date: 09/28/2020
f1_keywords:
- C3381
helpviewer_keywords:
- C3381
ms.assetid: d276c89f-8377-4cb6-a8d4-7770885f06c4
ms.openlocfilehash: 48a6c81f9506c532333b5353b8b194d17c91043f
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91510148"
---
# <a name="compiler-error-c3381"></a>Compilerfehler C3381

> "*Bezeichner*": Assemblyzugriffsspezifizierer sind nur in Code verfügbar, der mit der Option/CLR

Ein Typ wurde mit einem Zugriffsspezifizierer deklariert oder definiert, der nur im mit kompilierten Code zulässig ist **`/clr`** .

## <a name="remarks"></a>Bemerkungen

Dieser Fehler kann durch ein falsch verwendeter- **`public`** ,- **`protected`** oder- **`private`** Schlüsselwort oder einen fehlenden Doppelpunkt ( **`:`** ) nach einem Zugriffsspezifizierer innerhalb von oder verursacht werden **`class`** **`struct`** .

In C++/CLI können systemeigene Typen außerhalb einer Assembly sichtbar sein. Sie können jedoch nur den Assemblyzugriff für systemeigene Typen in einer **`/clr`** Kompilierung angeben. Weitere Informationen finden Sie unter [Typsichtbarkeit](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) und [ `/clr` (Common Language Runtime-Kompilierung)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3381 generiert. Um dieses Problem zu beheben, entfernen Sie zuerst den **`public`** Spezifizierer aus der `class A` Definition, oder kompilieren Sie mit der **`/clr`** Option. Fügen Sie dann einen Doppelpunkt nach ein **`private`** , um den Zugriff für anzugeben `class B {} b;` . Der Grund hierfür ist, dass eine in einer Klasse vorgebaufgefügte Klasse keinen Assemblyzugriffsspezifizierer als Teil

```cpp
// C3381.cpp
// compile with: /c
public class A {   // C3381
    private class B {} b;   // C3381
};
```
