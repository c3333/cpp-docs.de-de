---
title: Compilerfehler C2026
ms.date: 11/04/2016
f1_keywords:
- C2026
helpviewer_keywords:
- C2026
ms.assetid: 8e64b6e1-b967-479b-be97-d12dc4a8e389
ms.openlocfilehash: 9747b1edadc76ceeb502b2c6fd03496b91769f5a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80208064"
---
# <a name="compiler-error-c2026"></a>Compilerfehler C2026

Zeichenfolge zu groß, nachfolgende Zeichen abgeschnitten

Die Zeichenfolge ist länger als der Grenzwert von 16380 Einzel Byte Zeichen.

Bevor angrenzende Zeichen folgen verkettet werden, darf eine Zeichenfolge nicht länger als 16380 Einzel Byte Zeichen sein.

Eine Unicode-Zeichenfolge mit ungefähr einer Hälfte dieser Länge würde ebenfalls diesen Fehler generieren.

Wenn Sie eine Zeichenfolge wie folgt definiert haben, generiert Sie C2026:

```
char sz[] =
"\
imagine a really, really \
long string here\
";
```

Sie können Sie wie folgt unterbrechen:

```
char sz[] =
"\
imagine a really, really "
"long string here\
";
```

Möglicherweise möchten Sie in einer benutzerdefinierten Ressource oder einer externen Datei besonders große Zeichenfolgenliterale (32 KB oder mehr) speichern. Weitere Informationen finden Sie unter [Erstellen einer neuen benutzerdefinierten Ressource oder Daten Ressource](../../windows/creating-a-new-custom-or-data-resource.md) .
