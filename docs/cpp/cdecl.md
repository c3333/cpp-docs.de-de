---
title: __cdecl
ms.date: 10/09/2018
f1_keywords:
- __cdecl_cpp
- __cdecl
- _cdecl
- cdecl
helpviewer_keywords:
- __cdecl keyword [C++]
ms.assetid: 1ff1d03e-fb4e-4562-8be1-74f1ad6427f1
ms.openlocfilehash: b4a86c49880b0c40d402c7cec863f79e24bc4dc1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371570"
---
# <a name="__cdecl"></a>__cdecl

**__cdecl** ist die Standardaufrufkonvention für C- und C++-Programme. Da der Stapel vom Aufrufer bereinigt wird, kann er Funktionen übernehmen. `vararg` Die **__cdecl** Aufrufkonvention erstellt größere ausführbare Dateien als [__stdcall](../cpp/stdcall.md), da jeder Funktionsaufruf erfordert, um Stapelbereinigungscode einzuschließen. Die folgende Liste zeigt die Implementierung dieser Aufrufkonvention. Der **__cdecl** Modifikator ist Microsoft-spezifisch.

|Element|Implementierung|
|-------------|--------------------|
|Reihenfolge der Argumentübergabe|Von rechts nach links.|
|Stapelwartungszuständigkeit|Aufgerufene Funktion ruft die Argumente vom Stapel auf.|
|Namensergänzungskonvention|Unterstrichzeichen (_) werden Namen vorangestellt, es sei denn, \__cdecl Funktionen, die C-Verknüpfung verwenden, werden exportiert.|
|Konvention zur Umwandlung von Groß- in Kleinbuchstaben und umgekehrt|Groß-/Kleinbuchstaben werden nicht umgewandelt.|

> [!NOTE]
> Weitere Informationen finden Sie unter [Dekorierte Namen](../build/reference/decorated-names.md).

Platzieren Sie den **__cdecl** Modifikator vor einer Variablen oder einem Funktionsnamen. Da die C-Namens- und Aufrufkonventionen die Standardeinstellung sind, müssen Sie **__cdecl** in `/Gv` x86-Code nur verwenden, wenn Sie die Compileroption (vectorcall), `/Gz` (stdcall) oder `/Gr` (fastcall) angegeben haben. Die Compileroption [/Gd](../build/reference/gd-gr-gv-gz-calling-convention.md) erzwingt die **__cdecl** Aufrufkonvention.

Bei ARM- und x64-Prozessoren **wird __cdecl** akzeptiert, aber in der Regel vom Compiler ignoriert. Gemäß der Konvention zu ARM und x64 werden Argumente in Register übergeben, wenn dies möglich ist, und darauf folgende Argumente werden auf den Stapel übergeben. Verwenden Sie im x64-Code **__cdecl,** um die **Compileroption /Gv** zu überschreiben und die standardmäßige x64-Aufrufkonvention zu verwenden.

Wenn die Funktion bei nicht statischen Klassenfunktionen abweichend definiert ist, muss der Aufrufkonventionsmodifizierer nicht in der abweichenden Definition angegeben werden. Das bedeutet, dass für nicht statische Membermethoden der Klasse zum Zeitpunkt der Definition die während der Deklaration angegebene Aufrufkonvention angenommen wird. Bei dieser Klassendefinition:

```cpp
struct CMyClass {
   void __cdecl mymethod();
};
```

entspricht:

```cpp
void CMyClass::mymethod() { return; }
```

entspricht:

```cpp
void __cdecl CMyClass::mymethod() { return; }
```

Aus Kompatibilitätmit früheren Versionen sind **cdecl** und **_cdecl** ein Synonym für **__cdecl** es sei denn, die Compileroption [ \(/Za Disable language extensions)](../build/reference/za-ze-disable-language-extensions.md) wird angegeben.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird der Compiler angewiesen, C-Namenskonventionen und C-Aufrufkonventionen für die `system`-Funktion zu verwenden.

```cpp
// Example of the __cdecl keyword on function
int __cdecl system(const char *);
// Example of the __cdecl keyword on function pointer
typedef BOOL (__cdecl *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

## <a name="see-also"></a>Siehe auch

[Argumentübergabe und Benennungskonventionen](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Keywords](../cpp/keywords-cpp.md)
