---
title: Linkertoolfehler LNK1561
ms.date: 11/04/2016
f1_keywords:
- LNK1561
helpviewer_keywords:
- LNK1561
ms.assetid: cb0b709b-7c9c-4496-8a4e-9e1e4aefe447
ms.openlocfilehash: b397ef8e551f8cd6179392541e35183a5850454f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81357748"
---
# <a name="linker-tools-error-lnk1561"></a>Linkertoolfehler LNK1561

Einstiegspunkt muss definiert werden

Der Linker hat keinen *Einstiegspunkt*gefunden, die erste Funktion, die in Ihrer ausführbaren Datei aufruft. Standardmäßig sucht der Linker `main` nach `wmain` einer oder einer `WinMain` Funktion `wWinMain` für eine Konsolen-App, eine oder eine Funktion für eine Windows-App oder `DllMain` nach einer DLL, die initialisiert werden muss. Sie können eine andere Funktion angeben, indem Sie die Linkeroption [/ENTRY](../../build/reference/entry-entry-point-symbol.md) verwenden.

Dieser Fehler kann mehrere Ursachen haben:

- Möglicherweise haben Sie die Datei, die Ihren Einstiegspunkt definiert, nicht in die Liste der zu verknüpfenden Dateien aufgenommen. Stellen Sie sicher, dass die Datei, die die Einstiegspunktfunktion enthält, mit Ihrer App verknüpft ist.
- Möglicherweise haben Sie den Einstiegspunkt mit der falschen Funktionssignatur definiert. Sie haben z. B. die falsche Groß-/Kleinschreibung oder falsche Groß-/Kleinschreibung für den Funktionsnamen oder den Rückgabetyp oder die Parametertypen falsch angegeben.
- Möglicherweise haben Sie beim Erstellen einer DLL nicht die Option [/DLL](../../build/reference/dll-build-a-dll.md) angegeben.
- Möglicherweise haben Sie den Namen der Einstiegspunktfunktion falsch angegeben, wenn Sie die Linkeroption [/ENTRY](../../build/reference/entry-entry-point-symbol.md) verwendet haben.
- Wenn Sie das [LIB-Tool](../../build/reference/lib-reference.md) zum Erstellen einer DLL verwenden, haben Sie möglicherweise eine .def-Datei angegeben. Wenn dies der Zuspruch ist, entfernen Sie die .def-Datei aus dem Build.

Beim Erstellen einer App sucht der Linker nach einer Einstiegspunktfunktion, die zum Starten des Codes aufruft. Dies ist die Funktion, die aufgerufen wird, nachdem die App geladen und die Laufzeit initialisiert wurde. Sie müssen eine Einstiegspunktfunktion für eine App bereitstellen, oder Ihre App kann nicht ausgeführt werden. Ein Einstiegspunkt ist für eine DLL optional. Standardmäßig sucht der Linker nach einer Einstiegspunktfunktion, die über einen `int main(int, char**)`von mehreren bestimmten Namen und Signaturen verfügt, z. B. . Sie können einen anderen Funktionsnamen als Einstiegspunkt angeben, indem Sie die Linkeroption /ENTRY verwenden.

## <a name="example"></a>Beispiel

Das folgende Beispiel generiert LNK1561:

```cpp
// LNK1561.cpp
// LNK1561 expected
int i;
// add a main function to resolve this error
```
