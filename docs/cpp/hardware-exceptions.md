---
title: Hardwareausnahmen
ms.date: 11/04/2016
helpviewer_keywords:
- exceptions [C++], hardware
- errors [C++], low-level
- errors [C++], hardware
- hardware exceptions [C++]
- low level errors
ms.assetid: 06ac6f01-a8cf-4426-bb12-1688315ae1cd
ms.openlocfilehash: 8adfd59eab0960ab14b2becb8d9864c77196c909
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188675"
---
# <a name="hardware-exceptions"></a>Hardwareausnahmen

Die meisten Standardausnahmen, die vom Betriebssystem erkannt werden, sind Hardware-definierte Ausnahmen. Windows erkennt einige Softwareausnahmen auf niedriger Ebene, doch diese werden normalerweise am besten vom Betriebssystem selbst behandelt.

Windows ordnet die Hardwarefehler der verschiedenen Prozessoren den Ausnahmecodes in diesem Abschnitt zu. In manchen Fällen generiert ein Prozessor möglicherweise nur eine Teilmenge dieser Ausnahmen. Windows verarbeitet Informationen zur Ausnahme vor und gibt den entsprechenden Ausnahmecode aus.

Die Hardwareausnahmen, die von Windows erkannt werden, werden in der folgenden Tabelle zusammengefasst:

|Ausnahmecode|Ursache der Ausnahme|
|--------------------|------------------------|
|STATUS_ACCESS_VIOLATION|Lesen oder Schreiben in einer Speicheradresse, auf die nicht zugegriffen werden kann.|
|STATUS_BREAKPOINT|Auftreten eines Hardware-definierten Haltepunkts. Nur von Debuggern verwendet.|
|STATUS_DATATYPE_MISALIGNMENT|Lesen oder Schreiben in Daten unter einer Adresse, die nicht ordnungsgemäß ausgerichtet ist. Beispielsweise müssen 16-Bit-Entitäten auf 2-Byte-Begrenzungen ausgerichtet sein. (Gilt nicht für Intel 80*x*86-Prozessoren.)|
|STATUS_FLOAT_DIVIDE_BY_ZERO|Teilen des Gleitkommatyps durch 0,0.|
|STATUS_FLOAT_OVERFLOW|Überschreiten des maximalen positiven Exponenten eines Gleitkommatyps.|
|STATUS_FLOAT_UNDERFLOW|Überschreiten der Größe des niedrigsten negativen Exponenten eines Gleitkommatyps.|
|STATUS_FLOATING_RESEVERED_OPERAND|Verwenden eines reservierten Gleitkommaformats (ungültige Verwendung von Format).|
|STATUS_ILLEGAL_INSTRUCTION|Versuch, einen Anweisungscode auszuführen, der nicht vom Prozessor definiert ist.|
|STATUS_PRIVILEGED_INSTRUCTION|Ausführen einer Anweisung, die nicht im aktuellen Computermodus zulässig ist.|
|STATUS_INTEGER_DIVIDE_BY_ZERO|Teilen eines ganzzahligen Typs durch 0.|
|STATUS_INTEGER_OVERFLOW|Versuch, einen Vorgang auszuführen, der den Ganzzahlbereich übersteigt.|
|STATUS_SINGLE_STEP|Ausführen einer Anweisung im einschrittigen Modus. Nur von Debuggern verwendet.|

Viele der Ausnahmen, die in der vorherigen Tabelle aufgelistet sind, sollen von Debuggern, dem Betriebssystem oder einem anderen Code auf niedriger Ebene behandelt werden. Mit Ausnahme von Ganzzahl- und Gleitkommafehlern sollte der Code diese Fehler nicht verarbeiten. Daher sollten Sie normalerweise den Ausnahmebehandlungsfilter verwenden, um Ausnahmen zu ignorieren (ergibt 0). Andernfalls hindern Sie Mechanismen auf niedrigerer Ebene möglicherweise daran, entsprechend zu reagieren. Sie können jedoch angemessene Vorkehrungen gegen die potenziellen Auswirkungen dieser Low-Level-Fehler durch Schreiben von Beendigungs [Handlern](../cpp/writing-a-termination-handler.md)treffen.

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Ausnahme Handlers](../cpp/writing-an-exception-handler.md)<br/>
[Strukturierte Ausnahmebehandlung (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
