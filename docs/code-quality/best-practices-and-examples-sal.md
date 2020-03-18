---
title: Empfohlene Vorgehensweisen und Beispiele (SAL)
ms.date: 11/04/2016
ms.topic: conceptual
ms.openlocfilehash: 304ba98ae5118f2ca8fb425c8dd7065bd19c8287
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/17/2020
ms.locfileid: "79467035"
---
# <a name="best-practices-and-examples-sal"></a>Empfohlene Vorgehensweisen und Beispiele (SAL)

Im folgenden finden Sie einige Möglichkeiten, die Quell Code Anmerkung (Source Code Annotation Language, SAL) optimal zu nutzen und einige häufige Probleme zu vermeiden.

## <a name="_in_"></a>\_In\_

Wenn die Funktion in das-Element schreiben soll, verwenden Sie `_Inout_` anstelle von `_In_`. Dies ist insbesondere bei der automatisierten Konvertierung von älteren Makros in SAL von Bedeutung. Vor SAL haben viele Programmierer Makros als Kommentare verwendet – Makros, die `IN`, `OUT`, `IN_OUT`oder Varianten dieser Namen benannt wurden. Es wird empfohlen, dass Sie diese Makros in SAL konvertieren, aber wir sollten auch darauf achten, dass Sie bei der Konvertierung sorgfältig vorgehen, da der Code möglicherweise geändert wurde, seit der ursprüngliche Prototyp geschrieben wurde, und das alte Makro nicht mehr die Funktionsweise des Codes widerspiegelt. Achten Sie besonders auf das `OPTIONAL` Comment-Makro, weil es häufig falsch platziert wird – z. b. auf der falschen Seite eines Kommas.

```cpp

// Incorrect
void Func1(_In_ int *p1)
{
    if (p1 == NULL)
        return;

    *p1 = 1;
}

// Correct
void Func2(_Inout_ PCHAR p1)
{
    if (p1 == NULL)
        return;

    *p1 = 1;
}
```

## <a name="_opt_"></a>\_opt\_

Wenn der Aufrufer nicht in der Übergabe eines NULL-Zeigers zulässig ist, verwenden Sie `_In_` oder `_Out_` anstelle von `_In_opt_` oder `_Out_opt_`. Dies gilt auch für eine Funktion, die ihre Parameter überprüft und einen Fehler zurückgibt, wenn Sie NULL ist, wenn Sie nicht sein sollte. Obwohl eine Funktion den Parameter auf unerwartete NULL überprüft und ordnungsgemäß zurückgegeben wird, ist dies eine gute defensive Codierungs Praxis. Dies bedeutet nicht, dass die Parameter Anmerkung einen optionalen Typ (`_*Xxx*_opt_`) aufweisen kann.

```cpp

// Incorrect
void Func1(_Out_opt_ int *p1)
{
    *p = 1;
}

// Correct
void Func2(_Out_ int *p1)
{
    *p = 1;
}
```

## <a name="_pre_defensive_-and-_post_defensive_"></a>\_Pre\_Defensive\_ und \_Post\_Defensive\_

Wenn eine Funktion an einer Vertrauens Grenze angezeigt wird, empfiehlt es sich, die `_Pre_defensive_` Anmerkung zu verwenden.  Durch den "defensive"-Modifizierer werden bestimmte Anmerkungen geändert, um anzugeben, dass die Schnittstelle zum Zeitpunkt des Aufrufes strikt geprüft werden soll. im Implementierungs Text sollte jedoch davon ausgegangen werden, dass falsche Parameter passieren können. In diesem Fall wird `_In_ _Pre_defensive_` an einer Vertrauensstellungs Grenze bevorzugt, um anzugeben, dass ein Aufrufer zwar einen Fehler erhält, wenn er versucht, NULL zu übergeben, der Funktions Rumpf wird jedoch so analysiert, als ob der Parameter NULL sein kann, und alle Versuche, auf den Zeiger aufzuheben, ohne ihn zuerst auf NULL zu überprüfen, werden gekennzeichnet.  Eine `_Post_defensive_` Anmerkung ist auch zur Verwendung in Rückrufe verfügbar, bei denen die vertrauenswürdige Partei als Aufrufer angenommen wird und der nicht vertrauenswürdige Code der aufgerufene Code ist.

## <a name="_out_writes_"></a>\_Schreibvorgänge \_\_

Das folgende Beispiel veranschaulicht einen allgemeinen Missbrauch von `_Out_writes_`.

```cpp

// Incorrect
void Func1(_Out_writes_(size) CHAR *pb,
    DWORD size
);
```

Die Anmerkung `_Out_writes_` gibt an, dass ein Puffer vorhanden ist. `cb` zugeordneten Bytes, wobei das erste Byte beim Beenden initialisiert wird. Diese Anmerkung ist nicht streng falsch, und es ist hilfreich, die zugeordnete Größe auszudrücken. Sie gibt jedoch nicht an, wie viele Elemente von der Funktion initialisiert werden.

Das nächste Beispiel zeigt drei richtige Möglichkeiten, um die genaue Größe des initialisierten Teils des Puffers vollständig anzugeben.

```cpp

// Correct
void Func1(_Out_writes_to_(size, *pCount) CHAR *pb,
    DWORD size,
    PDWORD pCount
);

void Func2(_Out_writes_all_(size) CHAR *pb,
    DWORD size
);

void Func3(_Out_writes_(size) PSTR pb,
    DWORD size
);
```

## <a name="_out_-pstr"></a>\_ Pstr \_

Die Verwendung von `_Out_ PSTR` ist fast immer falsch. Dies wird als vorhanden sein eines Output-Parameters interpretiert, der auf einen Zeichen Puffer zeigt und NULL-terminiert ist.

```cpp

// Incorrect
void Func1(_Out_ PSTR pFileName, size_t n);

// Correct
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);
```

Eine Anmerkung wie `_In_ PCSTR` ist häufig und hilfreich. Er verweist auf eine Eingabe Zeichenfolge, die NULL-Beendigung hat, da die Vorbedingung von `_In_` das Erkennen einer null-terminierten Zeichenfolge zulässt.

## <a name="_in_-wchar-p"></a>\_in\_ WCHAR * p

`_In_ WCHAR* p` gibt an, dass ein Eingabe Zeiger `p` vorhanden ist, der auf ein Zeichen zeigt. In den meisten Fällen ist dies jedoch wahrscheinlich nicht die Spezifikation, die vorgesehen ist. Stattdessen ist die Angabe eines null-terminierten Arrays wahrscheinlich beabsichtigt. Verwenden Sie dazu `_In_ PWSTR`.

```cpp

// Incorrect
void Func1(_In_ WCHAR* wszFileName);

// Correct
void Func2(_In_ PWSTR wszFileName);
```

Die richtige Angabe der NULL-Beendigung fehlt häufig. Verwenden Sie die entsprechende `STR` Version, um den Typ zu ersetzen, wie im folgenden Beispiel gezeigt.

```cpp

// Incorrect
BOOL StrEquals1(_In_ PCHAR p1, _In_ PCHAR p2)
{
    return strcmp(p1, p2) == 0;
}

// Correct
BOOL StrEquals2(_In_ PSTR p1, _In_ PSTR p2)
{
    return strcmp(p1, p2) == 0;
}
```

## <a name="_out_range_"></a>\_Bereich \_\_

Wenn der-Parameter ein-Zeiger ist und Sie den Bereich des Werts des Elements, auf das der Zeiger verweist, ausdrücken möchten, verwenden Sie `_Deref_out_range_` anstelle von `_Out_range_`. Im folgenden Beispiel wird der Bereich von * pcbfill ausgedrückt, nicht pcbfill.

```cpp

// Incorrect
void Func1(
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,
    DWORD cbSize,
    _Out_range_(0, cbSize) DWORD *pcbFilled
);

// Correct
void Func2(
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,
    DWORD cbSize,
    _Deref_out_range_(0, cbSize) _Out_ DWORD *pcbFilled
);
```

`_Deref_out_range_(0, cbSize)` ist für einige Tools nicht unbedingt erforderlich, da Sie von `_Out_writes_to_(cbSize,*pcbFilled)`abgeleitet werden kann, Sie wird jedoch aus Gründen der Vollständigkeit hier angezeigt.

## <a name="wrong-context-in-_when_"></a>Falscher Kontext in \_, wenn\_

Ein weiterer häufiger Fehler ist die Verwendung der Post-State-Auswertung für Vorbedingungen. Im folgenden Beispiel ist `_Requires_lock_held_` eine Vorbedingung.

```cpp

// Incorrect
_When_(return == 0, _Requires_lock_held_(p->cs))
int Func1(_In_ MyData *p, int flag);

// Correct
_When_(flag == 0, _Requires_lock_held_(p->cs))
int Func2(_In_ MyData *p, int flag);
```

Der Ausdruck `result` verweist auf einen Wert nach dem Zustand, der im Zustand vor dem Zustand nicht verfügbar ist.

## <a name="true-in-_success_"></a>TRUE in \_Erfolg\_

Wenn die Funktion erfolgreich ist, wenn der Rückgabewert ungleich 0 (null) ist, verwenden Sie `return != 0` als Erfolgs Bedingung anstelle von `return == TRUE`. Ungleich NULL bedeutet nicht notwendigerweise, dass die Äquivalenz zum tatsächlichen Wert, den der Compiler für `TRUE`bereitstellt. Der zu `_Success_` Ende Parameter ist ein Ausdruck, und die folgenden Ausdrücke werden als Äquivalent ausgewertet: `return != 0`, `return != false`, `return != FALSE`und `return` ohne Parameter oder Vergleiche.

```cpp
// Incorrect
_Success_(return == TRUE) _Acquires_lock_(*lpCriticalSection)
BOOL WINAPI TryEnterCriticalSection(
  _Inout_ LPCRITICAL_SECTION lpCriticalSection
);

// Correct
_Success_(return != 0) _Acquires_lock_(*lpCriticalSection)
BOOL WINAPI TryEnterCriticalSection(
  _Inout_ LPCRITICAL_SECTION lpCriticalSection
);
```

## <a name="reference-variable"></a>Verweis Variable

Bei einer Verweis Variablen wurde in der vorherigen Version von Sal der implizite Zeiger als Anmerkung verwendet, und das Hinzufügen einer `__deref` zu Anmerkungen, die an eine Verweis Variable angefügt wurden, ist erforderlich. Diese Version verwendet das-Objekt selbst und erfordert nicht die zusätzlichen `_Deref_`.

```cpp

// Incorrect
void Func1(
    _Out_writes_bytes_all_(cbSize) BYTE *pb,
    _Deref_ _Out_range_(0, 2) _Out_ DWORD &cbSize
);

// Correct
void Func2(
    _Out_writes_bytes_all_(cbSize) BYTE *pb,
    _Out_range_(0, 2) _Out_ DWORD &cbSize
);
```

## <a name="annotations-on-return-values"></a>Anmerkungen zu Rückgabe Werten

Das folgende Beispiel zeigt ein häufiges Problem in den Anmerkungen zu Rückgabe Werten.

```cpp

// Incorrect
_Out_opt_ void *MightReturnNullPtr1();

// Correct
_Ret_maybenull_ void *MightReturnNullPtr2();
```

In diesem Beispiel gibt `_Out_opt_` an, dass der Zeiger im Rahmen der Vorbedingung Null sein kann. Vorbedingungen können jedoch nicht auf den Rückgabewert angewendet werden. In diesem Fall wird die korrekte Anmerkung `_Ret_maybenull_`.

## <a name="see-also"></a>Weitere Informationen

[Verwenden von SAL-Anmerkungen zum Reduzieren von C/C++-Codefehlern](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)  
[Einführung in SAL](../code-quality/understanding-sal.md)  
[Hinzufügen einer Anmerkung zu Funktionsparametern und Rückgabewerten](../code-quality/annotating-function-parameters-and-return-values.md)  
[Hinzufügen einer Anmerkung zum Funktionsverhalten](../code-quality/annotating-function-behavior.md)  
[Hinzufügen einer Anmerkung zu Strukturen und Klassen](../code-quality/annotating-structs-and-classes.md)  
[Hinzufügen einer Anmerkung zum Sperrverhalten](../code-quality/annotating-locking-behavior.md)  
[Angeben, wann und wo eine Anmerkung gültig ist](../code-quality/specifying-when-and-where-an-annotation-applies.md)  
[Systeminterne Funktionen](../code-quality/intrinsic-functions.md)
