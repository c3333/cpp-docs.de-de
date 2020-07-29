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
ms.openlocfilehash: 85d1b29fddece741aa94364bb6edfdf3b973faaf
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213176"
---
# <a name="__stdcall"></a>__stdcall

Die Aufruf **`__stdcall`** Konvention wird zum Aufrufen von Win32-API-Funktionen verwendet. Der aufgerufene bereinigt den Stapel, sodass der Compiler Funktionen übernimmt `vararg` **`__cdecl`** . Für Funktionen, die diese Aufrufkonvention verwenden, ist ein Funktionsprototyp erforderlich. Der **`__stdcall`** -Modifizierer ist Microsoft-spezifisch.

## <a name="syntax"></a>Syntax

> *Rückgabetyp* **`__stdcall`** *Funktionsname*[ **`(`** *Argument-List* **`)`** ]

## <a name="remarks"></a>Bemerkungen

Die folgende Liste zeigt die Implementierung dieser Aufrufkonvention.

|Element|Implementierung|
|-------------|--------------------|
|Reihenfolge der Argumentübergabe|Von rechts nach links.|
|Argumentübergabekonvention|Nach Wert, es sei denn, ein Zeiger oder ein Referenztyp wird übergeben.|
|Stapelwartungszuständigkeit|Die aufgerufene Funktion nimmt die eigenen Argumente vom Stapel auf.|
|Namensergänzungskonvention|Ein Unterstrich ( `_` ) wird dem Namen vorangestellt. Auf den Namen folgt das at-Zeichen ( `@` ), gefolgt von der Anzahl der Bytes (in dezimal) in der Argumentliste. Daher wird die Funktion, die als `int func( int a, double b )` deklariert ist, wie folgt ergänzt: `_func@12`|
|Konvention zur Umwandlung von Groß- in Kleinbuchstaben und umgekehrt|Keine|

Die [/gz](../build/reference/gd-gr-gv-gz-calling-convention.md) -Compileroption gibt **`__stdcall`** für alle Funktionen an, die nicht explizit mit einer anderen Aufruf Konvention deklariert wurden.

Aus Gründen der Kompatibilität mit früheren Versionen ist **`_stdcall`** ein Synonym für, **`__stdcall`** es sei denn, die Compileroption [ `/Za` \( Spracherweiterungen deaktivieren)](../build/reference/za-ze-disable-language-extensions.md) ist angegeben.

Funktionen, die mit dem- **`__stdcall`** Modifizierer deklariert werden, geben die-Werte auf die gleiche Weise zurück wie mit [`__cdecl`](../cpp/cdecl.md)

Auf Arm-und x64-Prozessoren **`__stdcall`** wird vom Compiler akzeptiert und ignoriert. auf Arm-und x64-Architekturen werden Argumente, wenn möglich, in Registern weitergegeben, und nachfolgende Argumente werden im Stapel weitergegeben.

Wenn die Funktion bei nicht statischen Klassenfunktionen abweichend definiert ist, muss der Aufrufkonventionsmodifizierer nicht in der abweichenden Definition angegeben werden. Das bedeutet, dass für nicht statische Membermethoden der Klasse zum Zeitpunkt der Definition die während der Deklaration angegebene Aufrufkonvention angenommen wird. Bei der Klassendefinition

```cpp
struct CMyClass {
   void __stdcall mymethod();
};
```

this

```cpp
void CMyClass::mymethod() { return; }
```

entspricht

```cpp
void __stdcall CMyClass::mymethod() { return; }
```

## <a name="example"></a>Beispiel

Im folgenden Beispiel führt die Verwendung von dazu, **`__stdcall`** `WINAPI` dass alle Funktionstypen als Standard--Aufrufe behandelt werden:

```cpp
// Example of the __stdcall keyword
#define WINAPI __stdcall
// Example of the __stdcall keyword on function pointer
typedef BOOL (__stdcall *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

## <a name="see-also"></a>Weitere Informationen

[Argument Übergabe und Benennungs Konventionen](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
