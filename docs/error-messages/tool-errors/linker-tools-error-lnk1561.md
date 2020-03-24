---
title: Linkertoolfehler LNK1561
ms.date: 11/04/2016
f1_keywords:
- LNK1561
helpviewer_keywords:
- LNK1561
ms.assetid: cb0b709b-7c9c-4496-8a4e-9e1e4aefe447
ms.openlocfilehash: 706cf6c90dc187b6c343edc82cebb93bb8660452
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194849"
---
# <a name="linker-tools-error-lnk1561"></a>Linkertoolfehler LNK1561

der Einstiegspunkt muss definiert werden.

Der Linker hat keinen *Einstiegspunkt*gefunden, die anfängliche Funktion, die in der ausführbaren Datei aufgerufen werden soll. Standardmäßig sucht der Linker nach einer `main`-oder `wmain` Funktion für eine Konsolen-APP, eine `WinMain` oder `wWinMain` Funktion für eine Windows-APP oder `DllMain` für eine DLL, die Initialisierung erfordert. Mithilfe der Option [/Entry](../../build/reference/entry-entry-point-symbol.md) Linker können Sie eine andere Funktion angeben.

Dieser Fehler kann mehrere Gründe haben:
- Möglicherweise haben Sie die Datei, die den Einstiegspunkt definiert, nicht in die Liste der zu verknüpfenden Dateien eingeschlossen. Vergewissern Sie sich, dass die Datei, die die Einstiegspunkt Funktion enthält, mit Ihrer APP verknüpft ist.
- Möglicherweise haben Sie den Einstiegspunkt mit der falschen Funktions Signatur definiert. Beispielsweise können Sie falsch geschriebene oder falsch geschriebene Fälle für den Funktionsnamen verwenden oder den Rückgabetyp oder die Parametertypen falsch angegeben haben.
- Bei der Erstellung einer DLL haben Sie möglicherweise nicht die Option [/dll](../../build/reference/dll-build-a-dll.md) angegeben.
- Wenn Sie die Option [/Entry](../../build/reference/entry-entry-point-symbol.md) Linker verwendet haben, haben Sie möglicherweise den Namen der Einstiegspunkt Funktion falsch angegeben.
- Wenn Sie das [lib](../../build/reference/lib-reference.md) -Tool verwenden, um eine DLL zu erstellen, haben Sie möglicherweise eine DEF-Datei angegeben. Wenn dies der Fall ist, entfernen Sie die DEF-Datei aus dem Build.

Beim Entwickeln einer App sucht der Linker nach einer Einstiegspunkt Funktion, um aufzurufen, um den Code zu starten. Dies ist die Funktion, die aufgerufen wird, nachdem die App geladen und die Laufzeit initialisiert wurde. Sie müssen eine Einstiegspunkt Funktion für eine APP bereitstellen, oder Ihre APP kann nicht ausgeführt werden. Ein Einstiegspunkt ist für eine DLL optional. Standardmäßig sucht der Linker nach einer Einstiegspunkt Funktion mit einem von mehreren bestimmten Namen und Signaturen, z. b. `int main(int, char**)`. Sie können einen anderen Funktionsnamen als Einstiegspunkt angeben, indem Sie die/ENTRY-Linkeroption verwenden.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird Linkertoolfehler LNK1561 generiert:

```cpp
// LNK1561.cpp
// LNK1561 expected
int i;
// add a main function to resolve this error
```
