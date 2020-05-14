---
title: Konvertierungen in und aus Zeigertypen
ms.date: 11/04/2016
helpviewer_keywords:
- pointers, converting
- conversions, pointer
- type casts, involving pointers
- void pointers
ms.assetid: 3facc56f-06d3-4570-b1a2-7d4927b83086
ms.openlocfilehash: 2d907dbcf4f826d364fb68ce65f7d44c6cfe97cd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62312408"
---
# <a name="conversions-to-and-from-pointer-types"></a>Konvertierungen in und aus Zeigertypen

Ein Zeiger auf einen Werttyp kann in einen Zeiger auf einen anderen Typ konvertiert werden. Allerdings ist das Ergebnis möglicherweise aufgrund der Ausrichtungsanforderungen und Größen unterschiedlicher Typen im Speicher nicht definiert. Ein Zeiger auf ein Objekt kann in einen Zeiger auf ein Objekt konvertiert werden, dessen Typ eine weniger oder gleich strenge Speicherausrichtung erfordert, und unverändert wieder zurück konvertiert werden kann.

Ein Zeiger auf `void` kann zu oder von einem Zeiger auf einen beliebigen Typ ohne Einschränkung oder Datenverlust konvertiert werden. Wenn das Ergebnis wieder in den ursprünglichen Typ konvertiert wird, wird der ursprüngliche Zeiger wiederhergestellt.

Wenn ein Zeiger in einen anderen Zeiger desselben Typs konvertiert wird, aber über unterschiedliche oder zusätzliche Qualifizierer verfügt, ist der neue Zeiger bis auf die Einschränkungen, die vom neuen Qualifizierer auferlegt werden, derselbe wie der alte.

Ein Zeigerwert kann auch in einen ganzzahligen Wert konvertiert werden. Der Pfad für die Konvertierung hängt von der Größe des Zeigers und der Größe des ganzzahligen Typs gemäß den folgenden Regeln ab:

- Wenn die Größe des Zeigers größer oder gleich der Größe des ganzzahligen Typs ist, verhält sich der Zeiger bei der Konvertierung wie ein Wert ohne Vorzeichen, nur dass er nicht in einen Gleitkommawert konvertiert werden kann.

- Wenn der Zeiger kleiner als der ganzzahlige Typ ist, wird der Zeiger zunächst in einen Zeiger mit derselben Größe wie der ganzzahlige Typ und anschließend in einen ganzzahligen Typ konvertiert.

Umgekehrt kann ein ganzzahliger Typ gemäß den folgenden Regeln in einen Zeigertyp konvertiert werden:

- Wenn der ganzzahlige Typ dieselbe Größe hat wie der Zeigertyp, wird der Ganzzahlwert durch die Konvertierung als Zeiger (ganze Zahl ohne Vorzeichen) behandelt.

- Wenn die Größe des ganzzahligen Typs von der Größe des Zeigertyps abweicht, wird der ganzzahlige Typ zuerst auf die Größe des Zeigers konvertiert. Dies wird mithilfe der Konvertierungspfade erreicht, die in den Tabellen [Konvertierungen von ganzzahligen Typen mit Vorzeichen](../c-language/conversions-from-signed-integral-types.md) und [Konvertierungen von ganzzahligen Typen ohne Vorzeichen](../c-language/conversions-from-unsigned-integral-types.md) angegeben sind. Es wird dann als Zeigerwert behandelt.

Ein integraler konstanter Ausdruck mit dem Wert 0 oder ein solcher Ausdruck, der in den Typ **void** <strong>\*</strong> umgewandelt wird, kann durch eine Typumwandlung, eine Zuweisung oder einen Vergleich mit einem beliebigen Zeiger konvertiert werden. Dies erzeugt einen NULL-Zeiger, der gleich einem anderen NULL-Zeiger desselben Typs ist, aber dieser NULL-Zeiger ist nicht gleich einem Zeiger auf eine Funktion oder ein Objekt. Ganze Zahlen, die nicht die Konstante 0 sind, können in den Zeigertyp konvertiert werden, aber das Ergebnis ist nicht übertragbar.

## <a name="see-also"></a>Siehe auch

[Zuweisungskonvertierungen](../c-language/assignment-conversions.md)
