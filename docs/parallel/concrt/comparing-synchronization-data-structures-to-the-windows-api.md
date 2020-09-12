---
title: Vergleich der Synchronisierungsdatenstrukturen mit der Windows-API
ms.date: 11/04/2016
helpviewer_keywords:
- synchronization data structures, compared to Windows API
- event class, example
ms.assetid: 8b0b1a3a-ef80-408c-91fa-93e6af920b4e
ms.openlocfilehash: b889570935b3a94e0cb8717c8af1783e2ce31c42
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040340"
---
# <a name="comparing-synchronization-data-structures-to-the-windows-api"></a>Vergleich der Synchronisierungsdatenstrukturen mit der Windows-API

In diesem Thema wird das Verhalten der von der Concurrency Runtime bereitgestellten Synchronisierungsdatenstrukturen mit den von der Windows-API bereitgestellten Synchronisierungsdatenstrukturen verglichen.

Die von der Concurrency Runtime bereitgestellten Synchronisierungs Datenstrukturen folgen dem *kooperativen Threading Modell*. Im kooperativen Threadingmodell halten Synchronisierungsprimitiven ihre Verarbeitungsressourcen zugunsten von anderen Threads explizit zurück. Dies unterscheidet sich vom *präemptiven Threading Modell*, in dem Verarbeitungs Ressourcen durch den steuernden Planer oder das Betriebssystem an andere Threads übertragen werden.

## <a name="critical_section"></a>critical_section

Die Klasse " [parallelcurrency:: CRITICAL_SECTION](../../parallel/concrt/reference/critical-section-class.md) " ähnelt der Windows- `CRITICAL_SECTION` Struktur, da Sie nur von den Threads eines Prozesses verwendet werden kann. Weitere Informationen zu kritischen Abschnitten in der Windows-API finden Sie unter [Critical Section Objects](/windows/win32/Sync/critical-section-objects).

## <a name="reader_writer_lock"></a>reader_writer_lock

Die Klasse " [parallelcurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) " ähnelt den Sperren von Windows Slim Reader/Writer (SRW). In der folgenden Tabelle werden die Übereinstimmungen und Unterschiede aufgelistet.

| Funktion | `reader_writer_lock`-Klasse | SRW-Sperre |
|--|--|--|
| Nicht wiedereintretend | Ja | Ja |
| Kann einen Reader auf einen Writer hochstufen | Nein | Nein |
| Kann einen Writer auf einen Reader tieferstufen | Nein | Nein |
| write-preference-Sperre | Ja | Nein |
| FIFO-Zugriff auf Writer | Ja | Nein |

Weitere Informationen zu SRW-Sperren finden Sie unter [SRW-Sperren (Slim Reader/Writer)](/windows/win32/sync/slim-reader-writer--srw--locks) im Platform SDK.

## <a name="event"></a>event

Die " [parallelcurrency:: Event](../../parallel/concrt/reference/event-class.md) "-Klasse ähnelt einem unbenannten Windows-Ereignis für manuelles Zurücksetzen. Das Verhalten eines `event`-Objekts ist jedoch kooperativ, das Verhalten eines Windows-Ereignisses hingegen präemptiv. Weitere Informationen zu Windows-Ereignissen finden Sie unter [Event Objects](/windows/win32/Sync/event-objects).

## <a name="example"></a>Beispiel

### <a name="description"></a>BESCHREIBUNG

Das folgende Beispiel soll den Unterschied zwischen der `event`-Klasse und Windows-Ereignissen verdeutlichen. In diesem Beispiel wird der Planer aktiviert, um höchstens zwei gleichzeitige Aufgaben zu erstellen. Anschließend werden zwei ähnliche Funktionen aufgerufen, die die `event`-Klasse und ein Ereignis für manuelles Zurücksetzen in Windows verwenden. Beide Funktionen erstellen zunächst mehrere Aufgaben, die auf die Signalisierung eines freigegebenen Ereignisses warten. Beide Funktionen halten dann die ausgeführten Aufgaben zurück und signalisieren das Ereignis. Beide Funktionen warten dann auf das signalisierte Ereignis.

### <a name="code"></a>Code

[!code-cpp[concrt-event-comparison#1](../../parallel/concrt/codesnippet/cpp/comparing-synchronization-data-structures-to-the-windows-api_1.cpp)]

### <a name="comments"></a>Kommentare

Dieses Beispiel erzeugt die folgende Beispielausgabe:

```Output
Cooperative event:
    Context 0: waiting on an event.
    Context 1: waiting on an event.
    Context 2: waiting on an event.
    Context 3: waiting on an event.
    Context 4: waiting on an event.
    Setting the event.
    Context 5: received the event.
    Context 6: received the event.
    Context 7: received the event.
    Context 8: received the event.
    Context 9: received the event.
Windows event:
    Context 10: waiting on an event.
    Context 11: waiting on an event.
    Setting the event.
    Context 12: received the event.
    Context 14: waiting on an event.
    Context 15: received the event.
    Context 16: waiting on an event.
    Context 17: received the event.
    Context 18: waiting on an event.
    Context 19: received the event.
    Context 13: received the event.
```

Da das Verhalten der `event`-Klasse kooperativ ist, kann der Planer Verarbeitungsressourcen einem anderen Kontext zuweisen, während auf die Signalisierung eines Ereignisses gewartet wird. Aus diesem Grund bewerkstelligt die Version, die die `event`-Klasse verwendet, einen höheren Arbeitsaufwand. In der Version, die Windows-Ereignisse verwendet, muss jede wartende Aufgabe den signalisierten Zustand aufweisen, bevor die nächste Aufgabe gestartet werden kann.

Weitere Informationen zu Aufgaben finden Sie Unteraufgaben [Parallelität](../../parallel/concrt/task-parallelism-concurrency-runtime.md).

## <a name="see-also"></a>Weitere Informationen

[Synchronisierungs Datenstrukturen](../../parallel/concrt/synchronization-data-structures.md)
