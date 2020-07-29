---
title: Pufferüberlauf
ms.date: 11/04/2016
helpviewer_keywords:
- buffers [C++], character sizes
- buffer overflows [C++]
- MBCS [C++], buffer overflow
ms.assetid: f2b7e40a-f02b-46d8-a449-51d26fc0c663
ms.openlocfilehash: 71877ed770384190cb7f856567d9e7e845e3da19
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217323"
---
# <a name="buffer-overflow"></a>Pufferüberlauf

Abweichende Zeichengrößen können Probleme verursachen, wenn Sie Zeichen in einem Puffer platzieren. Sehen Sie sich den folgenden Code an, der Zeichen aus einer Zeichenfolge `sz` in einen Puffer kopiert `rgch` :

```cpp
cb = 0;
while( cb < sizeof( rgch ) )
    rgch[ cb++ ] = *sz++;
```

Die Frage lautet: wurde das letzte Byte als führendes Byte kopiert? Im folgenden wird das Problem nicht gelöst, da es potenziell einen Überlauf des Puffers verursachen kann:

```cpp
cb = 0;
while( cb < sizeof( rgch ) )
{
    _mbccpy( rgch + cb, sz );
    cb += _mbclen( sz );
    sz = _mbsinc( sz );
}
```

Der-Befehl `_mbccpy` versucht, die richtige Aktion durchzuführen – kopieren Sie das vollständige Zeichen, egal ob es sich um 1 oder 2 Bytes handelt. Es wird jedoch nicht berücksichtigt, dass das letzte kopierte Zeichen möglicherweise nicht in den Puffer passt, wenn das Zeichen 2 Bytes breit ist. Die richtige Lösung ist:

```cpp
cb = 0;
while( (cb + _mbclen( sz )) <= sizeof( rgch ) )
{
    _mbccpy( rgch + cb, sz );
    cb += _mbclen( sz );
    sz = _mbsinc( sz );
}
```

Dieser Code testet auf möglichen Pufferüberlauf im Schleifen Test, wobei verwendet wird, `_mbclen` um die Größe des aktuellen Zeichens zu testen, auf das von gezeigt wird `sz` . Wenn Sie die Funktion aufzurufen `_mbsnbcpy` , können Sie den Code in der Schleife durch **`while`** eine einzelne Codezeile ersetzen. Beispiel:

```cpp
_mbsnbcpy( rgch, sz, sizeof( rgch ) );
```

## <a name="see-also"></a>Weitere Informationen

[Tipps für die MBCS-Programmierung](../text/mbcs-programming-tips.md)
