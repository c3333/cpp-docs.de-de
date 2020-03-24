---
title: Linkertoolwarnung LNK4049
ms.date: 04/15/2019
f1_keywords:
- LNK4049
helpviewer_keywords:
- LNK4049
ms.assetid: 5fd5fb24-c860-4149-a557-0ac26a65d97c
ms.openlocfilehash: a8e4416eafd47f584de4ab1c83aa7303cab0440a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194134"
---
# <a name="linker-tools-warning-lnk4049"></a>Linkertoolwarnung LNK4049

> das Symbol "*Symbol*", das in "*filename. obj*" definiert ist, wird importiert.

[__declspec (dllimport)](../../cpp/dllexport-dllimport.md) wurde für das *Symbol* angegeben, obwohl das Symbol in der Objektdatei *Dateiname. obj* im gleichen Bild definiert ist. Entfernen Sie den `__declspec(dllimport)` Modifizierer, um diese Warnung zu beheben.

## <a name="remarks"></a>Bemerkungen

Diese Warnung wird vom Linker generiert, wenn Sie ein Symbol in einer Objektdatei definieren und darauf verweisen, indem Sie den Modifizierer `__declspec(dllimport)` Deklaration in einem anderen verwenden.

Warnung Linkertoolwarnung LNK4049 ist eine allgemeinere Version der [Linker-Tool Warnung Linkertoolwarnung LNK4217](linker-tools-warning-lnk4217.md). Der Linker generiert eine Warnung Linkertoolwarnung LNK4049, wenn er nicht ermitteln kann, auf welche Funktion oder Objektdatei das importierte Symbol verwiesen hat.

Häufige Fälle, in denen Linkertoolwarnung LNK4049 anstelle von Linkertoolwarnung LNK4217 generiert wird, sind:

- Bei Verwendung der [/Incremental](../../build/reference/incremental-link-incrementally.md) -Option.

- Bei Verwendung der [/LTCG](../../build/reference/ltcg-link-time-code-generation.md) -Option.

Um Linkertoolwarnung LNK4049 aufzulösen, versuchen Sie es mit einem der folgenden Verfahren:

- Entfernen Sie den `__declspec(dllimport)`-Modifizierer aus der vorwärts Deklaration des Symbols, das Linkertoolwarnung LNK4049 ausgelöst hat. Sie können mit dem Dienstprogramm **DUMPBIN** nach Symbolen innerhalb eines Binär Bilds suchen. Der Schalter **DUMPBIN/Symbols** zeigt die COFF-Symboltabelle des Bilds an. Weitere Informationen zum **DUMPBIN** -Hilfsprogramm finden Sie unter [DUMPBIN Reference](../../build/reference/dumpbin-reference.md).

- Inkrementelles Verknüpfen und die Optimierung des gesamten Programms temporär deaktivieren. Bei der erneuten Kompilierung generiert die Anwendung eine Warnung Linkertoolwarnung LNK4217, die den Namen der Funktion enthält, die auf das importierte Symbol verweist. Entfernen Sie den `__declspec(dllimport)` deklarationsmodifizierer aus dem importierten Symbol, und aktivieren Sie ggf. die inkrementelle Verknüpfung oder das gesamte Programm.

Obwohl sich der endgültige generierte Code ordnungsgemäß verhält, ist der Code, der zum Aufrufen der importierten Funktion generiert wurde, weniger effizient, als die Funktion direkt aufzurufen. Diese Warnung wird nicht angezeigt, wenn Sie mit der [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) -Option kompilieren.

Weitere Informationen zum Importieren und Exportieren von Datendeklarationen finden Sie unter [dllexport, dllimport](../../cpp/dllexport-dllimport.md).

## <a name="example"></a>Beispiel

Durch das Verknüpfen der folgenden beiden Module wird Linkertoolwarnung LNK4049 generiert. Das erste Modul generiert eine Objektdatei, die eine einzelne exportierte Funktion enthält.

```cpp
// LNK4049a.cpp
// compile with: /c

__declspec(dllexport) int func()
{
   return 3;
}
```

Das zweite Modul generiert eine Objektdatei, die eine vorwärts Deklaration für die im ersten Modul exportierte Funktion enthält, zusammen mit einem Aufrufe dieser Funktion innerhalb der `main` Funktion. Wenn Sie dieses Modul mit dem ersten Modul verknüpfen, wird Linkertoolwarnung LNK4049 generiert. Entfernen Sie den `__declspec(dllimport)` Modifizierer aus der Deklaration, um die Warnung zu beheben.

```cpp
// LNK4049b.cpp
// compile with: /link /WX /LTCG LNK4049a.obj
// LNK4049 expected

__declspec(dllimport) int func();
// try the following line instead
// int func();

int main()
{
   return func();
}
```

## <a name="see-also"></a>Weitere Informationen

[Warnmeldungen für Linker-Tools Linkertoolwarnung LNK4217](linker-tools-warning-lnk4217.md) \
[Warnmeldungen für Linker-Tools LNK4286](linker-tools-warning-lnk4286.md) \
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)
