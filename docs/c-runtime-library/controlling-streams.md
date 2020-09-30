---
title: Steuern von Streams
description: Eine Übersicht über das Arbeiten mit Streams in der Microsoft C-Lauf Zeit Bibliothek.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Controlling Streams
helpviewer_keywords:
- streams, controlling
- controlling streams
- streams
ms.assetid: 267e9013-9afc-45f6-91e3-ca093230d9d9
ms.openlocfilehash: 0caa9eca7c960acbb581358c1a92afcc6a8af066
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "91589717"
---
# <a name="controlling-streams"></a>Steuern von Streams

[fopen](../c-runtime-library/reference/fopen-wfopen.md) gibt die Adresse eines Objekts vom Typ `FILE` zurück. Sie verwenden diese Adresse als `stream`-Argument für mehrere Bibliotheksfunktionen, um verschiedene Operationen für eine geöffnete Datei durchzuführen. Bei einem Bytestream erfolgen sämtliche Eingaben, als ob jedes Zeichen durch Aufrufen von [fgetc](../c-runtime-library/reference/fgetc-fgetwc.md) gelesen wird, während dies bei allen Ausgaben durch den Aufruf von [fputc](../c-runtime-library/reference/fputc-fputwc.md) erfolgt. Bei einem weiten Stream erfolgen sämtliche Eingaben, als ob jedes Zeichen durch Aufrufen von [fgetwc](../c-runtime-library/reference/fgetc-fgetwc.md) gelesen wird, während dies bei allen Ausgaben durch den Aufruf von [fputwc](../c-runtime-library/reference/fputc-fputwc.md) erfolgt.

Sie können eine Datei durch Aufrufen von [fclose](../c-runtime-library/reference/fclose-fcloseall.md) schließen. Danach ist die Adresse des `FILE`-Objekts ungültig.

Ein `FILE`-Objekt speichert den Status eines Streams wie Folgendes:

- Ein Fehlerindikator, der von einer Funktion auf ungleich Null festgelegt ist und einen Lese- oder Schreibfehler findet.

- Ein Indikator für das Dateiende, der von einer Funktion auf ungleich Null festgelegt ist und beim Lesen das Ende der Datei erreicht hat.

- Ein Dateipositionszeiger, der das nächste Byte in dem zu lesenden oder schreibenden Stream angibt, sofern die Datei Positionierungsanforderungen unterstützt.

- Ein [Streamstatus](../c-runtime-library/stream-states.md) gibt an, ob der Stream Lese- und/oder Schreibvorgänge akzeptiert und ob der Stream ungebunden, byteorientiert oder weit ausgerichtet ist.

- Ein Konvertierungsstatus speichert den Status von teilweise assemblierten oder generierten Multibytezeichen sowie den Umschaltzuständen für die Bytesequenz in der Datei.

- Ein Dateipuffer gibt die Adresse und die Größe eines Arrayobjekts an, die Bibliotheksfunktionen zur Verbesserung der Leistung von Lese- und Schreibvorgängen in den Stream nutzen können.

Ändern Sie keine in einem `FILE`-Objekt oder in einem Dateipuffer gespeicherten Werte, das bzw. den Sie für die Verwendung mit diesem Objekt angeben. Sie können ein `FILE`-Objekt nicht kopieren und die Adresse der Kopie nicht als `stream`-Argument in eine Bibliotheksfunktion kopieren.

## <a name="see-also"></a>Weitere Informationen

[Dateien und Streams](../c-runtime-library/files-and-streams.md)
