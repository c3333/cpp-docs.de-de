---
title: Linkertoolwarnung LNK4221
ms.date: 08/19/2019
f1_keywords:
- LNK4221
helpviewer_keywords:
- LNK4221
ms.assetid: 8e2eb2de-9532-4b85-908a-8c9ff5c4cccb
ms.openlocfilehash: f18224150232384adbf8ee7cc31af7bb7678eae5
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92919201"
---
# <a name="linker-tools-warning-lnk4221"></a>Linkertoolwarnung LNK4221

Diese Objektdatei definiert keine zuvor nicht definierten öffentlichen Symbole und wird daher von keinem Link Vorgang verwendet, der diese Bibliothek verwendet.

Beachten Sie die folgenden zwei Code Ausschnitte.

```cpp
// a.cpp
#include <atlbase.h>
```

```cpp
// b.cpp
#include <atlbase.h>
int function()
{
   return 0;
}
```

Um die Dateien zu kompilieren und zwei Objektdateien zu erstellen, führen Sie **cl/c a. cpp b. cpp** an einer Eingabeaufforderung aus. Wenn Sie die Objektdateien durch Ausführen von **Link/lib/out: Test. lib a. obj b. obj** verknüpfen, wird die Linkertoolwarnung LNK4221-Warnung angezeigt. Wenn Sie die Objekte durch Ausführen von **Link/lib/out: Test. lib b. obj a. obj** verknüpfen, wird keine Warnung angezeigt.

Im zweiten Szenario wird keine Warnung ausgegeben, da der Linker in der LIFO-Weise (Last-in-First-Out) arbeitet. Im ersten Szenario wird b. obj vor einer. obj verarbeitet, und a. obj hat keine neuen Symbole, die hinzugefügt werden können. Indem Sie den Linker dazu auffordern, a. obj zuerst zu verarbeiten, können Sie die Warnung vermeiden.

::: moniker range=">=msvc-160"

Eine häufige Ursache für diesen Fehler ist, dass zwei Quelldateien die Option [/Yc (Vorkompilierte Header Datei erstellen)](../../build/reference/yc-create-precompiled-header-file.md) mit dem gleichen Header Dateinamen angeben, der im **vorkompilierten Header** Feld angegeben ist. Eine häufige Ursache für dieses Problem ist " *PCH. h* ", da " *PCH. cpp* " standardmäßig " *PCH. h* " enthält und keine neuen Symbole hinzufügt. Wenn eine andere Quelldatei " *PCH. h* " mit **/Yc** enthält und die zugehörige obj-Datei vor "PCH. obj" verarbeitet wird, löst der Linker Linkertoolwarnung LNK4221 aus.

::: moniker-end

::: moniker range="<=msvc-150"

Eine häufige Ursache für diesen Fehler ist, dass zwei Quelldateien die Option [/Yc (Vorkompilierte Header Datei erstellen)](../../build/reference/yc-create-precompiled-header-file.md) mit dem gleichen Header Dateinamen angeben, der im **vorkompilierten Header** Feld angegeben ist. Eine häufige Ursache für dieses Problem ist " *stdafx. h* ", da " *stdafx. cpp* " standardmäßig " *stdafx. h* " enthält und keine neuen Symbole hinzufügt. Wenn eine andere Quelldatei *stdafx. h* mit **/Yc** enthält und die zugehörige obj-Datei vor stdafx. obj verarbeitet wird, löst der Linker Linkertoolwarnung LNK4221 aus.

::: moniker-end

Eine Möglichkeit, dieses Problem zu beheben, besteht darin sicherzustellen, dass für jeden vorkompilierten Header nur eine Quelldatei mit **/Yc** enthalten ist. Für alle anderen Quelldateien müssen vorkompilierte Header verwendet werden. Weitere Informationen zum Ändern dieser Einstellung finden Sie unter [/Yu (Vorkompilierte Header Datei verwenden)](../../build/reference/yu-use-precompiled-header-file.md).
