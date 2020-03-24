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
ms.openlocfilehash: 8f2b2b0cea8ff30cc450aae534fbff0d7b77f457
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190094"
---
# <a name="__cdecl"></a>__cdecl

**__cdecl** ist die Standard Aufruf Konvention für C- C++ und-Programme. Da der Stapel vom Aufrufer bereinigt wird, kann er `vararg` Funktionen ausführen. Die **__cdecl** -Aufruf Konvention erstellt größere ausführbare Dateien als [__stdcall](../cpp/stdcall.md), da jeder Funktionsaufruf einen Stapel Bereinigungs Code einschließen muss. Die folgende Liste zeigt die Implementierung dieser Aufrufkonvention. Der **__cdecl** Modifizierer ist Microsoft-spezifisch.

|Element|Implementierung|
|-------------|--------------------|
|Reihenfolge der Argumentübergabe|Von rechts nach links.|
|Stapelwartungszuständigkeit|Aufgerufene Funktion ruft die Argumente vom Stapel auf.|
|Namensergänzungskonvention|Ein Unterstrich (_) wird Namen vorangestellt, es sei denn, \__cdecl Funktionen, die die C-Verknüpfung verwenden, werden exportiert.|
|Konvention zur Umwandlung von Groß- in Kleinbuchstaben und umgekehrt|Groß-/Kleinbuchstaben werden nicht umgewandelt.|

> [!NOTE]
>  Weitere Informationen finden Sie unter ergänzte [Namen](../build/reference/decorated-names.md).

Platzieren Sie den **__cdecl** -Modifizierer vor einer Variablen oder einem Funktionsnamen. Da die C-Benennungs-und-Aufruf Konventionen die Standardeinstellung sind, müssen Sie **__cdecl** in x86-Code nur verwenden, wenn Sie die Compileroption `/Gv` (vectorcall), `/Gz` (STDCALL) oder `/Gr` (fastcall) angegeben haben. Die [/GD](../build/reference/gd-gr-gv-gz-calling-convention.md) -Compileroption erzwingt die **__cdecl** -Aufruf Konvention.

Auf Arm-und x64-Prozessoren wird **__cdecl** akzeptiert, aber in der Regel vom Compiler ignoriert. Gemäß der Konvention zu ARM und x64 werden Argumente in Register übergeben, wenn dies möglich ist, und darauf folgende Argumente werden auf den Stapel übergeben. Verwenden Sie in x64-Code **__cdecl** , um die **/GV** -Compileroption zu überschreiben und die x64-Standard Aufruf Konvention zu verwenden.

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

Aus Kompatibilitätsgründen mit früheren Versionen sind **cdecl** und **_cdecl** ein Synonym für **__cdecl** , es sei denn, die Compileroption [/Za \(Deaktivieren von Spracherweiterungen)](../build/reference/za-ze-disable-language-extensions.md) ist angegeben.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird der Compiler angewiesen, C-Namenskonventionen und C-Aufrufkonventionen für die `system`-Funktion zu verwenden.

```cpp
// Example of the __cdecl keyword on function
int __cdecl system(const char *);
// Example of the __cdecl keyword on function pointer
typedef BOOL (__cdecl *funcname_ptr)(void * arg1, const char * arg2, DWORD flags, ...);
```

## <a name="see-also"></a>Weitere Informationen

[Argumentübergabe und Benennungskonventionen](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
