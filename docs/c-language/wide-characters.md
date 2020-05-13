---
title: Breitzeichen
ms.date: 11/04/2016
helpviewer_keywords:
- wide characters
ms.assetid: 165c4a12-8ab9-45fb-9964-c55e9956194c
ms.openlocfilehash: 868acf0abd26a1f4b5533bb997fb9ea09a27954b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291001"
---
# <a name="wide-characters"></a>Breitzeichen

**ANSI 3.1.3.4** Der Wert einer ganzzahligen Zeichenkonstante, die mehr als ein Zeichen enthält, oder der Breitzeichenkonstante, die mehr als ein Multibytezeichen enthält

Die reguläre Zeichenkonstante "ab" verfügt über den Ganzzahlwert (int)0x6162. Wenn es mehr als ein Byte gibt, werden die zuvor gelesenen Bytes durch den Wert von **CHAR_BIT** nach links verschoben, und das nächste Byte wird unter Verwendung des bitweisen OR-Operators mit den niedrigsten **CHAR_BIT**-Bits verglichen. Die Anzahl von Bytes in der Mehrbytezeichenkonstante kann "sizeof(int)" nicht überschreiten, was für den 32-Bit-Zielcode 4 bedeutet.

Die Mehrbytezeichenkonstante wird wie oben gelesen und mithilfe der `mbtowc`-Laufzeitfunktion zu einer Breitzeichenkonstante konvertiert. Wenn sich daraus keine gültige Mehrbytezeichenkonstante ergibt, wird ein Fehler ausgegeben. In jeden Fall wird die von der `mbtowc`-Funktion überprüfte Anzahl von Bytes auf den Wert von `MB_CUR_MAX` beschränkt.

## <a name="see-also"></a>Siehe auch

[Zeichen](../c-language/characters.md)
