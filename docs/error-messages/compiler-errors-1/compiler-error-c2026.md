---
title: Compilerfehler C2026
description: Beschreibt den Microsoft C/C++-Compilerfehler C2026, seine Ursache und deren Behebung.
ms.date: 09/25/2020
f1_keywords:
- C2026
helpviewer_keywords:
- C2026
ms.assetid: 8e64b6e1-b967-479b-be97-d12dc4a8e389
ms.openlocfilehash: 39195568f964f07c6131fa43ef4a0f06121795da
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414047"
---
# <a name="compiler-error-c2026"></a>Compilerfehler C2026

> Zeichenfolge zu groß, nachfolgende Zeichen abgeschnitten

Die Zeichenfolge ist länger als der Grenzwert von 16380 Einzel Byte Zeichen.

## <a name="remarks"></a>Bemerkungen

Bevor angrenzende Zeichen folgen verkettet werden, darf eine Zeichenfolge nicht länger als 16380 Einzel Byte Zeichen sein.

Eine Unicode-Zeichenfolge mit ungefähr einer Hälfte dieser Länge würde ebenfalls diesen Fehler generieren.

## <a name="example"></a>Beispiel

Wenn Sie eine Zeichenfolge wie folgt definiert haben, generiert Sie C2026:

```C
char sz[] =
"\
imagine a really, really \
long string here\
";
```

Sie können Sie wie folgt unterbrechen:

```C
char sz[] =
"\
imagine a really, really "
"long string here\
";
```

Möglicherweise möchten Sie in einer benutzerdefinierten Ressource oder einer externen Datei besonders große Zeichenfolgenliterale (32 KB oder mehr) speichern. Weitere Informationen finden [Sie unter So erstellen Sie eine neue benutzerdefinierte oder Daten Ressource](../../windows/binary-editor.md#to-create-a-new-custom-or-data-resource).
