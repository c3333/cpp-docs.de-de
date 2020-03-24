---
title: selectany
ms.date: 11/04/2016
f1_keywords:
- selectany_cpp
helpviewer_keywords:
- __declspec keyword [C++], selectany
- selectany __declspec keyword
ms.assetid: 9c353017-5a42-4f50-b741-bd13da1ce84d
ms.openlocfilehash: 38346e41c1e943e9bfda70668a163c630a0b9599
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178872"
---
# <a name="selectany"></a>selectany

**Microsoft-spezifisch**

Weist den Compiler an, dass das deklarierte, globale Datenelement (Variable oder Objekt) ein beliebig auswählbares COMDAT (eine Paketfunktion) ist.

## <a name="syntax"></a>Syntax

```
__declspec( selectany ) declarator
```

## <a name="remarks"></a>Bemerkungen

Wenn zum Zeitpunkt der Verknüpfung mehrere Definitionen einer COMDAT angezeigt werden, wählt der Linker eine aus und verwirft den Rest. Wenn die Linkeroption [/OPT: Ref](../build/reference/opt-optimizations.md) (Optimierungen) ausgewählt ist, wird die COMDAT-Löschung ausgelöst, um alle nicht referenzierten Datenelemente in der Linkerausgabe zu entfernen.

Konstruktoren und Zuweisung durch globale Funktion oder statische Methoden in der Deklaration erstellen keine Verweise und verhindern die /OPT: REF-Eliminierung nicht. Nebeneffekte von derartigem Code sollten nicht davon abhängen, ob keine weiteren Verweise auf die Daten vorhanden sind.

Für dynamisch initialisierte globale Objekte verwirft **Selectany** auch den Initialisierungs Code eines Objekts, auf das nicht verwiesen wird.

Ein globales Datenelement kann normalerweise nur einmal in einem EXE- bzw. DLL-Projekt initialisiert werden. **Selectany** kann zum Initialisieren von globalen Daten verwendet werden, die durch Header definiert werden, wenn derselbe Header in mehr als einer Quelldatei angezeigt wird. **Selectany** ist sowohl im C-als auch C++ im Compiler verfügbar.

> [!NOTE]
>  " **Selectany** " kann nur auf die tatsächliche Initialisierung globaler Datenelemente angewendet werden, die extern sichtbar sind.

## <a name="example"></a>Beispiel

Dieser Code zeigt, wie das **Selectany** -Attribut verwendet wird:

```cpp
//Correct - x1 is initialized and externally visible
__declspec(selectany) int x1=1;

//Incorrect - const is by default static in C++, so
//x2 is not visible externally (This is OK in C, since
//const is not by default static in C)
const __declspec(selectany) int x2 =2;

//Correct - x3 is extern const, so externally visible
extern const __declspec(selectany) int x3=3;

//Correct - x4 is extern const, so it is externally visible
extern const int x4;
const __declspec(selectany) int x4=4;

//Incorrect - __declspec(selectany) is applied to the uninitialized
//declaration of x5
extern __declspec(selectany) int x5;

// OK: dynamic initialization of global object
class X {
public:
X(int i){i++;};
int i;
};

__declspec(selectany) X x(1);
```

## <a name="example"></a>Beispiel

Dieser Code zeigt, wie das **Selectany** -Attribut verwendet wird, um die Faltung von Daten zu gewährleisten, wenn Sie auch die Linkeroption [/OPT: ICF](../build/reference/opt-optimizations.md) verwenden. Beachten Sie, dass Daten mit **Selectany** gekennzeichnet und in einem **Konstanten** Abschnitt (Schreib geschützter Bereich) abgelegt werden müssen. Sie müssen den schreibgeschützten Abschnitt explizit angeben.

```cpp
// selectany2.cpp
// in the following lines, const marks the variables as read only
__declspec(selectany) extern const int ix = 5;
__declspec(selectany) extern const int jx = 5;
int main() {
   int ij;
   ij = ix + jx;
}
```

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[__declspec](../cpp/declspec.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
