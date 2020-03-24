---
title: __sptr, __uptr
ms.date: 10/10/2018
f1_keywords:
- __uptr_cpp
- __sptr_cpp
- __uptr
- __sptr
- _uptr
- _sptr
helpviewer_keywords:
- __sptr modifier
- __uptr modifier
ms.assetid: c7f5f3b2-9106-4a0b-a6de-d1588ab153ed
ms.openlocfilehash: bfa468c96196c417415801239925707c43a49c4e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178677"
---
# <a name="__sptr-__uptr"></a>__sptr, __uptr

**Microsoft-spezifisch**

Verwenden Sie den **__sptr** oder **__uptr** Modifizierer in einer 32-Bit-Zeiger Deklaration, um anzugeben, wie der Compiler einen 32-Bit-Zeiger in einen 64-Bit-Zeiger konvertiert. Ein 32-Bit-Zeiger wird beispielsweise konvertiert, wenn er einer 64-Bit-Zeigervariablen zugewiesen oder auf einer 64-Bit-Plattform dereferenziert wird.

In der Microsoft-Dokumentation zur Unterstützung von 64-Bit-Plattformen wird das wichtigste Bit eines 32-Bit-Zeigers gelegentlich als signiertes Bit bezeichnet. Standardmäßig verwendet der Compiler eine Vorzeichenerweiterung, um einen 32-Bit-Zeiger in einen 64-Bit-Zeiger zu konvertieren. Das heißt, die unwichtigsten 32 Bits des 64-Bit-Zeigers werden auf den Wert des 32-Bit-Zeigers festgelegt, und die wichtigsten 32 Bits werden auf den Wert des signierten Bits des 32-Bit-Zeigers festgelegt. Diese Konvertierung ergibt korrekte Ergebnisse, wenn das signierte Bit 0 ist. Wenn das signierte Bit 1 ist, sind die Ergebnisse nicht korrekt. Beispielsweise ergibt die 32-Bit-Adresse "0x7FFFFFFF" die entsprechende 64-Bit-Adresse "0x000000007FFFFFFF", die 32-Bit-Adresse "0x80000000" wurde jedoch inkorrekt auf "0xFFFFFFFF80000000" geändert.

Der Modifizierer **__sptr**oder signierter Zeiger gibt an, dass eine Zeiger Konvertierung die signifikantesten Bits eines 64-Bit-Zeigers auf das Signier Bit des 32-Bit-Zeigers festlegt. Der Modifizierer " **__uptr**" oder "Ganzzahl ohne Vorzeichen Pointer" gibt an, dass bei einer Konvertierung die signifikantesten Bits auf NULL gesetzt werden. Die folgenden Deklarationen zeigen die **__sptr** und **__uptr** Modifizierer, die mit zwei nicht qualifizierten Zeigern verwendet werden, zwei mit dem [__ptr32](../cpp/ptr32-ptr64.md) Typ qualifizierte Zeiger und einen Funktionsparameter.

```cpp
int * __sptr psp;
int * __uptr pup;
int * __ptr32 __sptr psp32;
int * __ptr32 __uptr pup32;
void MyFunction(char * __uptr __ptr32 myValue);
```

Verwenden Sie die **__sptr** -und **__uptr** Modifizierer mit Zeiger Deklarationen. Verwenden Sie die Modifizierer an der Position eines [Zeigertyp Qualifizierers](../c-language/pointer-declarations.md). Dies bedeutet, dass der Modifizierer dem Sternchen folgen muss. Die Modifizierer können nicht mit [Zeigern auf](../cpp/pointers-to-members.md)Member verwendet werden. Die Modifizierer beeinflussen nicht die Nichtzeigerdeklarationen.

Aus Kompatibilitätsgründen mit früheren Versionen sind **_sptr** und **_uptr** Synonyme für **__sptr** und **__uptr** , es sei denn, die Compileroption [/Za \(Deaktivieren von Spracherweiterungen)](../build/reference/za-ze-disable-language-extensions.md) ist angegeben.

## <a name="example"></a>Beispiel

Im folgenden Beispiel werden 32-Bit-Zeiger deklariert, die die **__sptr** -und **__uptr** -Modifizierer verwenden, jeder 32-Bit-Zeiger einer 64-Bit-Zeiger Variablen zugewiesen und dann der hexadezimale Wert jedes 64-Bit-Zeigers angezeigt. Das Beispiel wird mit dem systemeigenen 64-Bit-Compiler kompiliert und auf einer 64-Bit-Plattform ausgeführt.

```cpp
// sptr_uptr.cpp
// processor: x64
#include "stdio.h"

int main()
{
    void *        __ptr64 p64;
    void *        __ptr32 p32d; //default signed pointer
    void * __sptr __ptr32 p32s; //explicit signed pointer
    void * __uptr __ptr32 p32u; //explicit unsigned pointer

// Set the 32-bit pointers to a value whose sign bit is 1.
    p32d = reinterpret_cast<void *>(0x87654321);
    p32s = p32d;
    p32u = p32d;

// The printf() function automatically displays leading zeroes with each 32-bit pointer. These are unrelated
// to the __sptr and __uptr modifiers.
    printf("Display each 32-bit pointer (as an unsigned 64-bit pointer):\n");
    printf("p32d:       %p\n", p32d);
    printf("p32s:       %p\n", p32s);
    printf("p32u:       %p\n", p32u);

    printf("\nDisplay the 64-bit pointer created from each 32-bit pointer:\n");
    p64 = p32d;
    printf("p32d: p64 = %p\n", p64);
    p64 = p32s;
    printf("p32s: p64 = %p\n", p64);
    p64 = p32u;
    printf("p32u: p64 = %p\n", p64);
    return 0;
}
```

```Output
Display each 32-bit pointer (as an unsigned 64-bit pointer):
p32d:       0000000087654321
p32s:       0000000087654321
p32u:       0000000087654321

Display the 64-bit pointer created from each 32-bit pointer:
p32d: p64 = FFFFFFFF87654321
p32s: p64 = FFFFFFFF87654321
p32u: p64 = 0000000087654321
```

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[Microsoft-spezifische Modifizierer](../cpp/microsoft-specific-modifiers.md)
