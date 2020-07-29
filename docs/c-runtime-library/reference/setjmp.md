---
title: setjmp
ms.date: 08/14/2018
api_name:
- setjmp
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- setjmp
helpviewer_keywords:
- programs [C++], saving states
- current state
- setjmp function
ms.assetid: 684a8b27-e8eb-455b-b4a8-733ca1cbd7d2
ms.openlocfilehash: beaf56a03c1bd157257d604bfd0ebefb219d0225
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226150"
---
# <a name="setjmp"></a>setjmp

Speichert den aktuellen Zustand des Programms.

## <a name="syntax"></a>Syntax

```C
int setjmp(
   jmp_buf env
);
```

### <a name="parameters"></a>Parameter

*ENV*<br/>
Variable, in die die Umgebung gespeichert wird

## <a name="return-value"></a>Rückgabewert

Gibt 0 zurück, wenn die Stapelumgebung gespeichert wurde. Wenn **setjmp** als Ergebnis eines- `longjmp` Aufrufes zurückgibt, gibt es das *Wert* Argument von zurück `longjmp` , oder wenn das *Wert* Argument von `longjmp` 0 ist, gibt **setjmp** den Wert 1 zurück. Es gibt keine Fehlerrückgabe.

## <a name="remarks"></a>Bemerkungen

Die **setjmp** -Funktion speichert eine Stapel Umgebung, die Sie anschließend mithilfe von wiederherstellen können `longjmp` . Bei Verwendung von **setjmp** und `longjmp` bietet eine Möglichkeit, eine nicht lokale auszuführen **`goto`** . Sie werden in der Regel verwendet, um die Ausführungssteuerung an den Fehlerbehandlungs- oder Wiederherstellungscode in einer vorher aufgerufenen Routine zu übergeben, ohne die normalen Aufruf- oder Rückgabekonventionen zu verwenden.

Ein Aufrufen von **setjmp** speichert die aktuelle Stapel *Umgebung in der*-Umgebung. Ein nachfolgendes Aufrufen von `longjmp` stellt die gespeicherte Umgebung wieder her und gibt die Steuerung an den Punkt direkt nach dem entsprechenden **setjmp** -Befehl zurück. Alle Variablen (mit Ausnahme der Variablen „register“), die für die für das Steuerelement zur Routineerfassung zugänglich sind, erhalten die ursprünglichen Werte des `longjmp`-Aufrufs.

Es ist nicht möglich, **setjmp** zu verwenden, um von nativem zu verwaltetem Code zu springen.

**Microsoft-spezifisch**

In Microsoft C++-Code unter Windows verwendet **longjmp** die gleiche Semantik für die Stapel Auflösung wie den Code zur Ausnahmebehandlung. Es ist sicher, an denselben Stellen zu verwenden, in denen C++-Ausnahmen ausgelöst werden können. Diese Verwendung ist jedoch nicht portabel und enthält einige wichtige Einschränkungen. Weitere Informationen finden Sie unter [longjmp](longjmp.md).

**Ende Microsoft-spezifisch**

> [!NOTE]
> In portablen C++-Code können Sie `setjmp` keine `longjmp` C++-Objekt Semantik annehmen und unterstützen. Ein `setjmp` / `longjmp` Aufruf Paar hat insbesondere ein nicht definiertes Verhalten, `setjmp` Wenn und durch ersetzt werden `longjmp` **`catch`** und **`throw`** alle nicht trivialen debugtoren für alle automatischen Objekte aufrufen würden. In C++-Programmen wird empfohlen, dass Sie den C++-Mechanismus zur Ausnahmebehandlung verwenden.

Weitere Informationen finden Sie unter [Verwenden von „setjmp/longjmp“](../../cpp/using-setjmp-longjmp.md).

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**setjmp**|\<setjmp.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Siehe das Beispiel für [_fpreset](fpreset.md).

## <a name="see-also"></a>Siehe auch

[Prozess-und Umgebungs Steuerung](../../c-runtime-library/process-and-environment-control.md)<br/>
[longjmp](longjmp.md)
