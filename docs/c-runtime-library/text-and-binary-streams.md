---
title: Text- und binäre Streams
description: Eine Beschreibung von Text-und Binärdaten strömen in der Microsoft C-Lauf Zeit Bibliothek.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- binary streams
- text streams
ms.assetid: 57035e4a-955d-4e04-a560-fcf67ce68b4e
ms.openlocfilehash: 522e4d5f119e4415694b59b2b08141a45f06fe5a
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "91589613"
---
# <a name="text-and-binary-streams"></a>Text- und binäre Streams

Ein Textstream besteht aus einer oder mehreren Textzeilen, die in eine textorientierte Anzeige geschrieben werden können, sodass sie gelesen werden können. Beim Lesen aus einem Textstream liest das Programm einen `NL` (Zeilenvorschub) am Ende jeder Zeile. Beim Schreiben in einen Textstream schreibt das Programm ein `NL`, um das Ende einer Zeile anzugeben. Um unterschiedliche Konventionen in Zielumgebungen für die Darstellung von Text in Dateien einander zuzuordnen, können die Bibliotheksfunktionen die Anzahl und Darstellungen der Zeichen ändern, die zwischen dem Programm und einem Textstream übertragen werden.

Die Positionierung innerhalb eines Textstreams ist begrenzt. Durch Aufrufen von [fgetpos](../c-runtime-library/reference/fgetpos.md) oder [ftell](../c-runtime-library/reference/ftell-ftelli64.md) können Sie den aktuellen Dateipositionszeiger abrufen. Sie können einen Textstream an einer auf diese Weise abgerufenen Position positionieren, oder am Anfang bzw. am Ende des Streams, indem Sie [fsetpos](../c-runtime-library/reference/fsetpos.md) oder [fseek](../c-runtime-library/reference/fseek-fseeki64.md) aufrufen. Alle anderen Positionsänderungen werden möglicherweise nicht unterstützt.

Zur maximalen Portabilität sollte das Programm nicht schreiben:

- Leere Dateien
- Leerzeichen am Ende einer Zeile
- Partielle Zeilen (durch Weglassen von `NL` am Ende einer Datei)
- Andere Zeichen als die druckbaren Zeichen, NL und `HT` (horizontaler Tabulator)

Wenn Sie diese Regeln befolgen, entspricht die Sequenz der Zeichen, die Sie (entweder als Byte- oder Multibytezeichen) aus einem Textstream lesen, der Sequenz der Zeichen, die Sie bei der Erstellung der Datei in den Textstream geschrieben haben. Anderenfalls können die Bibliotheksfunktionen eine von Ihnen erstellte Datei entfernen, wenn die Datei beim Schließen leer ist. Sie können auch Zeichen ändern oder löschen, die Sie in die Datei schreiben.

Ein binärer Stream besteht aus einem oder mehreren Bytes willkürlicher Informationen. Sie können den in einem beliebigen Objekt gespeicherten Wert in einen (byteorientierten) binären Stream schreiben und genau lesen, was in dem Objekt beim Schreibvorgang gespeichert wurde. Die Bibliotheksfunktionen ändern nicht die Bytes, die zwischen dem Programm und einem binären Stream übertragen werden. Sie können jedoch eine beliebige Anzahl von `NULL` Bytes an die Datei anfügen, die Sie mit einem binären Stream schreiben. Das Programm muss diese zusätzlichen `NULL` Bytes am Ende des binären Streams behandeln.

Die Positionierung innerhalb eines binären Streams ist klar definiert, außer der Positionierung relativ zum Ende des Streams. Sie können denselben aktuellen Dateipositionszeiger wie bei einem Textstream abrufen und ändern. Die von " [f](../c-runtime-library/reference/ftell-ftelli64.md) " und " [f Seek](../c-runtime-library/reference/fseek-fseeki64.md) " verwendeten Offsets zählen Bytes vom Anfang des Streams (Byte 0 (null)), sodass die ganzzahlige Arithmetik für diese Offsets vorhersagbare Ergebnisse liefert.

Ein Bytestream verarbeitet eine Datei als Bytesequenz. Im Programm ähnelt der Stream dieser Bytesequenz, ausgenommen der möglichen oben beschriebenen Änderungen.

## <a name="see-also"></a>Weitere Informationen

[Dateien und Streams](../c-runtime-library/files-and-streams.md)
