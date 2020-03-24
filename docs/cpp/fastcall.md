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
ms.openlocfilehash: d4b650542a3a85c8f0008374abef02686c5491a3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188921"
---
# <a name="__fastcall"></a>__fastcall

**Microsoft-spezifisch**

Die **__fastcall** -Aufruf Konvention gibt an, dass Argumente für Funktionen, sofern möglich, in Registern übermittelt werden sollen. Diese Aufrufkonvention gilt nur für die x86-Architektur. Die folgende Liste zeigt die Implementierung dieser Aufrufkonvention.

|Element|Implementierung|
|-------------|--------------------|
|Reihenfolge der Argumentübergabe|Die ersten beiden in der Argumentliste von links nach rechts gefundenen DWORD oder kleineren Argumente werden in ECX- und EDX-Registern übergeben. Alle anderen Argumente werden von rechts nach links an den Stapel übergeben.|
|Stapelwartungszuständigkeit|Aufgerufene Funktion ruft die Argumente vom Stapel auf.|
|Namensergänzungskonvention|Das at-Zeichen (\@) hat Namen als Präfix. ein @-Zeichen, gefolgt von der Anzahl von Bytes (in dezimal) in der Parameterliste, wird für Namen angehängt.|
|Konvention zur Umwandlung von Groß- in Kleinbuchstaben und umgekehrt|Groß-/Kleinbuchstaben werden nicht umgewandelt.|

> [!NOTE]
> In zukünftigen Versionen werden von Compilern möglicherweise andere Register zum Speichern von Parametern verwendet werden.

Die Verwendung der [/gr](../build/reference/gd-gr-gv-gz-calling-convention.md) -Compileroption bewirkt, dass jede Funktion im Modul als **__fastcall** kompiliert wird, es sei denn, die Funktion wird mit einem in Konflikt stehenden Attribut deklariert, oder der Name der Funktion ist `main`.

Das **__fastcall** -Schlüsselwort wird von den Compiler, die auf Arm-und x64-Architekturen abzielen, akzeptiert und ignoriert. auf einem x64-Chip werden die ersten vier Argumente nach Möglichkeit in Registern weitergegeben, und zusätzliche Argumente werden im Stapel weitergegeben. Weitere Informationen finden Sie unter [x64-Aufruf Konvention](../build/x64-calling-convention.md). Auf einem ARM-Chip werden bis zu vier Ganzzahl- und acht Gleitkommaargumente in Registern übergeben, und zusätzliche Argumente werden auf den Stapel übergeben.

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

Aus Gründen der Kompatibilität mit früheren Versionen ist **_fastcall** ein Synonym für **__fastcall** , es sei denn, die Compileroption [/Za \(Deaktivieren von Spracherweiterungen)](../build/reference/za-ze-disable-language-extensions.md) ist angegeben.

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

## <a name="see-also"></a>Weitere Informationen

[Argumentübergabe und Benennungskonventionen](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
