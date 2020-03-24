---
title: Auslösen von Softwareausnahmen
ms.date: 11/04/2016
helpviewer_keywords:
- run-time errors, treating as exceptions
- exception handling [C++], errors as exceptions
- exceptions [C++], flagging errors as exceptions
- errors [C++], treating as exceptions
- exception handling [C++], detecting errors
- structured exception handling [C++], errors as exceptions
- exceptions [C++], software
- RaiseException function
- software exceptions [C++]
- formats [C++], exception codes
ms.assetid: be1376c3-c46a-4f52-ad1d-c2362840746a
ms.openlocfilehash: f50d84bd034cc6eeb00dc17cb3b7272a988b6731
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179132"
---
# <a name="raising-software-exceptions"></a>Auslösen von Softwareausnahmen

Einige der häufigsten Programmfehlerquellen werden vom System nicht als Ausnahmen gekennzeichnet. Wenn Sie beispielsweise versuchen, einen Speicherblock zu belegen, jedoch unzureichend Arbeitsspeicher vorhanden ist, löst die Laufzeit oder API-Funktion keine Ausnahme aus, sondern gibt einen Fehlercode zurück.

Allerdings können Sie jede Bedingung als Ausnahme behandeln, indem Sie diese Bedingung in Ihrem Code erkennen und diese dann durch Aufrufen der [RaiseException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raiseexception) -Funktion melden. Indem Sie Fehler auf diese Weise kennzeichnen, können Sie die Vorteile der strukturierten Ausnahmebehandlung für jede Art von Laufzeitfehler nutzen.

So verwenden Sie die strukturierte Ausnahmebehandlung bei Fehlern

- Definieren Sie einen eigenen Ausnahmecode für das Ereignis.

- Ruft `RaiseException` auf, wenn ein Problem erkannt wird.

- Verwenden Sie Ausnahmebehandlungsfilter, um den von Ihnen definierten Ausnahmecode zu testen.

Die > Datei \<Winerror. h zeigt das Format für Ausnahme Codes an. Um sicherzustellen, dass Sie keinen Code definieren, der in Konflikt mit einem vorhandenen Ausnahmecode steht, legen Sie das dritte höchstwertige Bit auf 1 fest. Die vier höchstwertigen Bits sollten so festgelegt werden, wie in der folgenden Tabelle gezeigt.

|Bits|Empfohlene Binäreinstellung|BESCHREIBUNG|
|----------|--------------------------------|-----------------|
|31-30|11|Diese zwei Bits beschreiben den grundlegenden Status des Codes: 11 = Fehler, 00 = Erfolg, 01 = Information, 10 = Warnung.|
|29|1|Clientbit. Wird für benutzerdefinierten Code auf 1 festgelegt.|
|28|0|Reservierte Bitzahl. (Festlegung auf 0 beibehalten.)|

Sie können die ersten zwei Bits optional auf eine andere Einstellung als binär 11 festlegen, obwohl die Einstellung "Fehler" für die meisten Ausnahmen angemessen ist. Es ist wichtig, daran zu denken, Bits 29 und 28 so festzulegen, wie es in der vorherigen Tabelle gezeigt wurde.

Der resultierende Fehlercode sollte daher die höchsten vier Bits aufweisen, die auf Hexadezimal E festgelegt sind. Die folgenden Definitionen definieren z. b. Ausnahme Codes, die nicht mit Windows-Ausnahme Codes in Konflikt stehen. (Sie müssen jedoch prüfen, welche Codes von Drittanbieter-DLLs verwendet werden).

```cpp
#define STATUS_INSUFFICIENT_MEM       0xE0000001
#define STATUS_FILE_BAD_FORMAT        0xE0000002
```

Nachdem Sie einen Ausnahmecode definiert haben, können Sie ihn verwenden, um eine Ausnahme auszulösen. Beispielsweise löst der folgende Code die `STATUS_INSUFFICIENT_MEM` Ausnahme als Reaktion auf ein Problem mit der Speicher Belegung aus:

```cpp
lpstr = _malloc( nBufferSize );
if (lpstr == NULL)
    RaiseException( STATUS_INSUFFICIENT_MEM, 0, 0, 0);
```

Wenn Sie einfach eine Ausnahme auslösen möchten, können Sie die letzten drei Parameter auf 0 festlegen. Die drei letzten Parameter übergeben zusätzliche Informationen und legen Flags fest, die Handler beim Fortsetzen der Ausführung hindern. Weitere Informationen finden Sie unter der [raiserexception](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raiseexception) -Funktion in der Windows SDK.

In den Ausnahmebehandlungsfiltern können Sie dann die Codes testen, die Sie definiert haben. Beispiel:

```cpp
__try {
    ...
}
__except (GetExceptionCode() == STATUS_INSUFFICIENT_MEM ||
        GetExceptionCode() == STATUS_FILE_BAD_FORMAT )
```

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Ausnahme Handlers](../cpp/writing-an-exception-handler.md)<br/>
[Strukturierte Ausnahmebehandlung (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
