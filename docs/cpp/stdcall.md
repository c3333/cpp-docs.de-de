---
title: __stdcall
ms.date: 10/10/2018
f1_keywords:
- __stdcall_cpp
- __stdcall
- _stdcall
helpviewer_keywords:
- __stdcall keyword [C++]
ms.assetid: e212594b-1827-4d07-9527-7d412b300df8
ms.openlocfilehash: 3abd1d020e4181a42a7bc38319e5e17e69ef0507
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178537"
---
# <a name="__stdcall"></a>__stdcall

Die **__stdcall** -Aufruf Konvention wird zum Aufrufen von Win32-API-Funktionen verwendet. Der aufgerufene bereinigt den Stapel, sodass der Compiler `vararg` Funktionen **__cdecl**. Für Funktionen, die diese Aufrufkonvention verwenden, ist ein Funktionsprototyp erforderlich. Der **__stdcall** Modifizierer ist Microsoft-spezifisch.

## <a name="syntax"></a>Syntax

> *Rückgabetyp* **\_\_stdcallfunktionsname** *function-name*[ **(** *Argument-List* **)** ]

## <a name="remarks"></a>Bemerkungen

Die folgende Liste zeigt die Implementierung dieser Aufrufkonvention.

|Element|Implementierung|
|-------------|--------------------|
|Reihenfolge der Argumentübergabe|Von rechts nach links.|
|Argumentübergabekonvention|Nach Wert, es sei denn, ein Zeiger oder ein Referenztyp wird übergeben.|
|Stapelwartungszuständigkeit|Die aufgerufene Funktion nimmt die eigenen Argumente vom Stapel auf.|
|Namensergänzungskonvention|Ein Unterstrich (_) wird dem Namen vorangestellt. Dem Namen folgt das @-Zeichen, gefolgt von der Anzahl von Bytes (als Dezimalzahl) in der Argumentliste. Daher wird die Funktion, die als `int func( int a, double b )` deklariert ist, wie folgt ergänzt: `_func@12`|
|Konvention zur Umwandlung von Groß- in Kleinbuchstaben und umgekehrt|Keine|

Die [/gz](../build/reference/gd-gr-gv-gz-calling-convention.md) -Compileroption gibt **__stdcall** für alle Funktionen an, die nicht explizit mit einer anderen Aufruf Konvention deklariert werden.

Aus Gründen der Kompatibilität mit früheren Versionen ist **_stdcall** ein Synonym für **__stdcall** , es sei denn, die Compileroption [/Za \(Deaktivieren von Spracherweiterungen)](../build/reference/za-ze-disable-language-extensions.md) ist angegeben.

Funktionen, die mit dem **__stdcall** Modifizierer deklariert werden, geben Werte auf die gleiche Weise zurück wie Funktionen, die mit [__cdecl](../cpp/cdecl.md)

Auf Arm-und x64-Prozessoren wird **__stdcall** vom Compiler akzeptiert und ignoriert. bei Arm-und x64-Architekturen werden Argumente nach Möglichkeit in Registern weitergegeben, und nachfolgende Argumente werden im Stapel weitergegeben.

Wenn die Funktion bei nicht statischen Klassenfunktionen abweichend definiert ist, muss der Aufrufkonventionsmodifizierer nicht in der abweichenden Definition angegeben werden. Das bedeutet, dass für nicht statische Membermethoden der Klasse zum Zeitpunkt der Definition die während der Deklaration angegebene Aufrufkonvention angenommen wird. Bei der Klassendefinition

```cpp
struct CMyClass {
   void __stdcall mymethod();
};
```

diesen

```cpp
void CMyClass::mymethod() { return; }
```

entspricht

```cpp
void __stdcall CMyClass::mymethod() { return; }
```

## <a name="example"></a>Beispiel

Im folgenden Beispiel führt die Verwendung von **__stdcall** dazu, dass alle `WINAPI` Funktionstypen als Standard--Aufrufe behandelt werden:

```cpp
// Example of the __stdcall keyword
#define WINAPI __stdcall
// Example of the __stdcall keyword on function pointer
typedef BOOL (__stdcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

## <a name="see-also"></a>Weitere Informationen

[Argumentübergabe und Benennungskonventionen](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
