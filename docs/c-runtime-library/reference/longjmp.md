---
title: longjmp
ms.date: 08/14/2018
api_name:
- longjmp
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
- longjmp
helpviewer_keywords:
- restoring stack environment and execution locale
- longjmp function
ms.assetid: 0e13670a-5130-45c1-ad69-6862505b7a2f
ms.openlocfilehash: 4f737818afe7136262362e4fe996745064568758
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218558"
---
# <a name="longjmp"></a>longjmp

Stellt die von einem-Befehl festgelegte Stapel Umgebung und das Ausführungs Gebiets Schema wieder her `setjmp` .

## <a name="syntax"></a>Syntax

```C
void longjmp(
   jmp_buf env,
   int value
);
```

### <a name="parameters"></a>Parameter

*ENV*<br/>
Variable, in die die Umgebung gespeichert wird

*value*<br/>
Der Wert, der dem Aufruf `setjmp` zurückgegeben wird.

## <a name="remarks"></a>Bemerkungen

Die **longjmp** -Funktion stellt eine Stapel Umgebung und ein Ausführungs Gebiets Schema wieder her, die zuvor in *env* von gespeichert wurden `setjmp` . `setjmp`und **longjmp** bieten eine Möglichkeit, eine nicht lokale auszuführen **`goto`** . Sie werden in der Regel verwendet, um die Ausführungs Steuerung an den Fehler Behandlungs-oder Wiederherstellungscode in einer vorher aufgerufenen Routine zu übergeben, ohne die normalen Aufruf-und Rückgabe Konventionen zu verwenden.

Ein-Befehl `setjmp` bewirkt, dass die aktuelle Stapel Umgebung in der *env*-Datei gespeichert wird. Ein nachfolgender Befehl von **longjmp** stellt die gespeicherte Umgebung wieder her und gibt die Steuerung an den Punkt zurück, der direkt auf den entsprechenden-Befehl folgt `setjmp` . Die Ausführung wird fortgesetzt, als ob der *Wert* gerade vom `setjmp`-Aufruf zurückgegeben worden wäre. Die Werte aller Variablen (außer Register Variablen), die für die Routine empfangende Steuerelemente zugänglich sind, enthalten die Werte, die Sie beim Aufrufen von " **longjmp** " hatten. Die Werte der Registervariablen sind unvorhersehbar. Der Wert, der von `setjmp` zurückgegeben wird, muss ungleich null sein. Wenn der *Wert* als 0 übergeben wird, wird der Wert 1 in der tatsächlichen Rückgabe ersetzt.

**Microsoft-spezifisch**

In Microsoft C++-Code unter Windows verwendet **longjmp** die gleiche Semantik für die Stapel Auflösung wie den Code zur Ausnahmebehandlung. Es ist sicher, an denselben Stellen zu verwenden, in denen C++-Ausnahmen ausgelöst werden können. Diese Verwendung ist jedoch nicht portabel und enthält einige wichtige Einschränkungen.

Ruft nur **longjmp** auf, bevor die Funktion, die aufgerufen hat, `setjmp` zurückgibt. andernfalls sind die Ergebnisse unvorhersehbar.

Beachten Sie die folgenden Einschränkungen bei der Verwendung von **longjmp**:

- Gehen Sie nicht davon aus, dass die Werte der Registervariablen unverändert bleiben. Die Werte der Register Variablen in der Routine, die aufrufen `setjmp` , können nach der Ausführung von **longjmp** nicht in den richtigen Werten wieder hergestellt werden.

- Verwenden Sie **longjmp** nicht, um die Steuerung aus einer Unterbrechungs Behandlungs Routine zu übertragen, es sei denn, die Unterbrechung wird durch eine Gleit Komma Ausnahme verursacht. In diesem Fall kann ein Programm über **longjmp** von einem Interrupt-Handler zurückkehren, wenn er das mathematische Gleit Komma Paket zum ersten Mal erneut initialisiert, indem [_fpreset](fpreset.md)aufgerufen wird.

- Verwenden Sie **longjmp** nicht, um die Steuerung aus einer Rückruf Routine zu übertragen, die direkt oder indirekt durch Windows-Code aufgerufen wird.

- Wenn der Code mit **/EHS** oder **/EHsc** kompiliert wird und die Funktion, die den **longjmp** -aufrufsvorgang enthält, verwendet wird **`noexcept`** , können lokale Objekte in dieser Funktion während der Stapel Entladung nicht zerstört werden.

**Ende Microsoft-spezifisch**

> [!NOTE]
> In portablen C++-Code können Sie `setjmp` keine `longjmp` C++-Objekt Semantik annehmen und unterstützen. Ein `setjmp` / `longjmp` Aufruf Paar hat insbesondere ein nicht definiertes Verhalten, `setjmp` Wenn und durch ersetzt werden `longjmp` **`catch`** und **`throw`** alle nicht trivialen debugtoren für alle automatischen Objekte aufrufen würden. In C++-Programmen wird empfohlen, dass Sie den C++-Mechanismus zur Ausnahmebehandlung verwenden.

Weitere Informationen finden Sie unter [Verwenden von „setjmp/longjmp“](../../cpp/using-setjmp-longjmp.md).

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**longjmp**|\<setjmp.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Siehe das Beispiel für [_fpreset](fpreset.md).

## <a name="see-also"></a>Weitere Informationen

[Prozess-und Umgebungs Steuerung](../../c-runtime-library/process-and-environment-control.md)<br/>
[setjmp](setjmp.md)
