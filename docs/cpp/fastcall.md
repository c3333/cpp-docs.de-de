---
title: __fastcall
ms.date: 12/17/2018
f1_keywords:
- __fastcall_cpp
- __fastcall
- _fastcall
helpviewer_keywords:
- __fastcall keyword [C++]
ms.assetid: bb5b9c8a-dfad-450c-9119-0ac2bc59544f
ms.openlocfilehash: 420552dd62c46ab5c2fa7e201387f258617f8453
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227477"
---
# <a name="__fastcall"></a>__fastcall

**Microsoft-spezifisch**

Die- **`__fastcall`** Aufruf Konvention gibt an, dass Argumente für Funktionen, sofern möglich, in Registern übermittelt werden sollen. Diese Aufrufkonvention gilt nur für die x86-Architektur. Die folgende Liste zeigt die Implementierung dieser Aufrufkonvention.

|Element|Implementierung|
|-------------|--------------------|
|Reihenfolge der Argumentübergabe|Die ersten beiden in der Argumentliste von links nach rechts gefundenen DWORD oder kleineren Argumente werden in ECX- und EDX-Registern übergeben. Alle anderen Argumente werden von rechts nach links an den Stapel übergeben.|
|Stapelwartungszuständigkeit|Aufgerufene Funktion ruft die Argumente vom Stapel auf.|
|Namensergänzungskonvention|Mit \@ dem Präfix () werden Namen vorangestellt. ein @-Zeichen, gefolgt von der Anzahl der Bytes (in dezimal) in der Parameterliste, wird für die Namen angehängt.|
|Konvention zur Umwandlung von Groß- in Kleinbuchstaben und umgekehrt|Groß-/Kleinbuchstaben werden nicht umgewandelt.|

> [!NOTE]
> In zukünftigen Versionen werden von Compilern möglicherweise andere Register zum Speichern von Parametern verwendet werden.

Die Verwendung der [/gr](../build/reference/gd-gr-gv-gz-calling-convention.md) -Compileroption bewirkt, dass jede Funktion im Modul als kompiliert **`__fastcall`** wird, es sei denn, die Funktion wird mit einem in Konflikt stehenden Attribut deklariert, oder der Name der Funktion ist `main` .

Das **`__fastcall`** Schlüsselwort wird von den Compilern, die auf Arm-und x64-Architekturen abzielen, akzeptiert und ignoriert. auf einem x64-Chip werden die ersten vier Argumente nach Möglichkeit in Registern weitergegeben, und zusätzliche Argumente werden im Stapel weitergegeben. Weitere Informationen finden Sie unter [x64-Aufruf Konvention](../build/x64-calling-convention.md). Auf einem ARM-Chip werden bis zu vier Ganzzahl- und acht Gleitkommaargumente in Registern übergeben, und zusätzliche Argumente werden auf den Stapel übergeben.

Wenn die Funktion bei nicht statischen Klassenfunktionen abweichend definiert ist, muss der Aufrufkonventionsmodifizierer nicht in der abweichenden Definition angegeben werden. Das bedeutet, dass für nicht statische Membermethoden der Klasse zum Zeitpunkt der Definition die während der Deklaration angegebene Aufrufkonvention angenommen wird. Bei dieser Klassendefinition:

```cpp
struct CMyClass {
   void __fastcall mymethod();
};
```

entspricht:

```cpp
void CMyClass::mymethod() { return; }
```

entspricht:

```cpp
void __fastcall CMyClass::mymethod() { return; }
```

Aus Gründen der Kompatibilität mit früheren Versionen ist **_fastcall** ein Synonym für, **`__fastcall`** es sei denn, die Compileroption [/Za \( Spracherweiterungen deaktivieren)](../build/reference/za-ze-disable-language-extensions.md) ist angegeben.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird die Funktion `DeleteAggrWrapper` an Argumente in Registern übergeben:

```cpp
// Example of the __fastcall keyword
#define FASTCALL    __fastcall

void FASTCALL DeleteAggrWrapper(void* pWrapper);
// Example of the __ fastcall keyword on function pointer
typedef BOOL (__fastcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Argument Übergabe und Benennungs Konventionen](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
