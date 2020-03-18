---
title: C++Referenz zu Kern Richtlinien Prüfung
ms.date: 03/22/2018
ms.topic: reference
helpviewer_keywords:
- code analysis, C++ core check
ms.assetid: f1429463-136e-41ed-8a75-a8dbf0b4fd89
ms.openlocfilehash: 3fe8f1795416bd05ce2c8cc622664a3ff1d6c749
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/17/2020
ms.locfileid: "79467232"
---
# <a name="c-core-guidelines-checker-reference"></a>C++Referenz zu Kern Richtlinien Prüfung

Dieser Abschnitt listet die Warnungen für C++ Core Richtlinien aus. Weitere Informationen zur Code Analyse finden Sie unter [/analyze (Code Analyse)](/cpp/build/reference/analyze-code-analysis) und [Schnellstart: Code Analyse für CC++/](../code-quality/quick-start-code-analysis-for-c-cpp.md).

> [!NOTE]
> Einige Warnungen zu mehr als eine Gruppe gehören, und nicht alle Warnungen haben eine vollständige Referenz-Thema.

## <a name="owner_pointer-group"></a>OWNER_POINTER-Gruppe

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)\
Zurückgeben eines Bereichs bezogenen Objekts anstelle eines Heap zugeordneten, wenn es über einen bewegungskonstruktor verfügt. Weitere Informationen finden [ C++ Sie in den Kern Richtlinien R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26403 RESET_OR_DELETE_OWNER](C26403.md)\
Zurücksetzen oder explizites Löschen eines Besitzers\<t > Zeiger "*Variable*". Weitere Informationen finden [ C++ Sie in den Kern Richtlinien R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26404 DONT_DELETE_INVALID](C26404.md)\
Löschen Sie keinen Besitzer\<t->, der möglicherweise einen ungültigen Status aufweist. Weitere Informationen finden [ C++ Sie in den Kern Richtlinien R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26405 DONT_ASSIGN_TO_VALID](C26405.md)\
Weisen Sie keinen Besitzer\<t-> zu, die sich möglicherweise in einem gültigen Zustand befinden. Weitere Informationen finden [ C++ Sie in den Kern Richtlinien R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26406 DONT_ASSIGN_RAW_TO_OWNER](C26406.md)\
Weisen Sie einem Besitzer\<t > keinen rohzeiger zu. Weitere Informationen finden [ C++ Sie in den Kern Richtlinien R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26407 DONT_HEAP_ALLOCATE_UNNECESSARILY](C26407.md)\
Bevorzugen Sie Bereichs bezogene Objekte, nicht unnötig Heap Zuordnung. Weitere Informationen finden [ C++ Sie unter Core Guidelines R. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26429 USE_NOTNULL](C26429.md)\
Das Symbol '*Symbol*' wird nie auf NULL-Werte getestet, es kann als not_null gekennzeichnet werden. Weitere Informationen finden [ C++ Sie unter Core Guidelines F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26430 TEST_ON_ALL_PATHS](C26430.md)\
Das Symbol "*Symbol*" wird nicht auf NULL-Werte in allen Pfaden getestet. Weitere Informationen finden [ C++ Sie unter Core Guidelines F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26431 DONT_TEST_NOTNULL](C26431.md)\
Der Typ des Ausdrucks '*expr*' ist bereits "gsl:: NOT_NULL". Testen sie nicht auf nullwertigkeit. Weitere Informationen finden [ C++ Sie unter Core Guidelines F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

## <a name="raw_pointer-group"></a>RAW_POINTER-Gruppe

[C26400 NO_RAW_POINTER_ASSIGNMENT](c26400.md)\
Weisen Sie das Ergebnis einer Zuordnung oder eines Funktions Aufrufes nicht mit einem Besitzer zu,\<t > Rückgabewert an einen rohzeiger. Verwenden Sie stattdessen Owner\<t >. Weitere Informationen finden [ C++ Sie in den Kern Richtlinien I. 11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[C26401 DONT_DELETE_NON_OWNER](c26401.md)\
Löschen Sie keinen rohzeiger, der kein Besitzer\<t > ist. Weitere Informationen finden [ C++ Sie in den Kern Richtlinien I. 11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Ri-raw).

[C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT](C26402.md)\
Zurückgeben eines Bereichs bezogenen Objekts anstelle eines Heap zugeordneten, wenn es über einen bewegungskonstruktor verfügt. Weitere Informationen finden [ C++ Sie in den Kern Richtlinien R. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-ptr).

[C26408 NO_MALLOC_FREE](C26408.md)\
Vermeiden Sie malloc () und Free (), bevorzugen Sie die nothrow-Version von New with DELETE. Weitere Informationen finden [ C++ Sie in den Kern Richtlinien R. 10](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-mallocfree).

[C26409 NO_NEW_DELETE](C26409.md)\
Vermeiden Sie das Aufrufen von New und explizites löschen, verwenden Sie stattdessen Std:: make_unique\<t >. Weitere Informationen finden [ C++ Sie in den Kern Richtlinien R. 11](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-newdelete).

[C26429 USE_NOTNULL](C26429.md)\
Das Symbol '*Symbol*' wird nie auf NULL-Werte getestet, es kann als not_null gekennzeichnet werden. Weitere Informationen finden [ C++ Sie unter Core Guidelines F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26430 TEST_ON_ALL_PATHS](C26430.md)\
Das Symbol "*Symbol*" wird nicht auf NULL-Werte in allen Pfaden getestet. Weitere Informationen finden [ C++ Sie unter Core Guidelines F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26431 DONT_TEST_NOTNULL](C26431.md)\
Der Typ des Ausdrucks '*expr*' ist bereits "gsl:: NOT_NULL". Testen sie nicht auf nullwertigkeit. Weitere Informationen finden [ C++ Sie unter Core Guidelines F. 23](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f23-use-a-not_nullt-to-indicate-that-null-is-not-a-valid-value).

[C26481 NO_POINTER_ARITHMETIC](C26481.md)\
Verwenden Sie keine Zeigerarithmetik. Verwenden Sie stattdessen die Spanne. Siehe [ C++ Kern Leitlinien Begrenzungen. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md)\
Ausdruck '*expr*': kein Array zu Zeiger Verfall. Weitere Informationen finden [ C++ Sie Untergrund Legende Begrenzungen. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds).

## <a name="unique_pointer-group"></a>UNIQUE_POINTER-Gruppe

[C26410 NO_REF_TO_CONST_UNIQUE_PTR](C26410.md)\
Der Parameter "*Parameter*" ist ein Verweis auf `const` eindeutigen Zeiger, verwenden Sie stattdessen "Konstante t *" oder "&". Weitere Informationen finden [ C++ Sie in den Kern Richtlinien R. 32](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-uniqueptrparam).

[C26411 NO_REF_TO_UNIQUE_PTR](C26411.md)\
Der Parameter "*Parameter*" ist ein Verweis auf einen eindeutigen Zeiger und wird nie neu zugeordnet oder zurückgesetzt, verwenden Sie stattdessen "t *" oder "t" &. Weitere Informationen finden [ C++ Sie in den Kern Richtlinien R. 33](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-reseat).

[C26414 RESET_LOCAL_SMART_PTR](C26414.md)\
Verschieben, kopieren, Neuzuweisen oder Zurücksetzen eines lokalen intelligenten Zeigers '*Symbol*'. Weitere Informationen finden [ C++ Sie unter Core Guidelines R. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26415 SMART_PTR_NOT_NEEDED](C26415.md)\
Der intelligente Zeiger Parameter '*Symbol*' wird nur für den Zugriff auf einen enthaltenen Zeiger verwendet. Verwenden von T * "oder" T & stattdessen. Weitere Informationen finden [ C++ Sie unter Core Guidelines R. 30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

## <a name="shared_pointer-group"></a>SHARED_POINTER-Gruppe

[C26414 RESET_LOCAL_SMART_PTR](C26414.md)\
Verschieben, kopieren, Neuzuweisen oder Zurücksetzen eines lokalen intelligenten Zeigers '*Symbol*'. Weitere Informationen finden [ C++ Sie unter Core Guidelines R. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-scoped).

[C26415 SMART_PTR_NOT_NEEDED](C26415.md)\
Der intelligente Zeiger Parameter '*Symbol*' wird nur für den Zugriff auf einen enthaltenen Zeiger verwendet. Verwenden von T * "oder" T & stattdessen. Weitere Informationen finden [ C++ Sie unter Core Guidelines R. 30](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-smartptrparam).

[C26416 NO_RVALUE_REF_SHARED_PTR](C26416.md)\
Der Shared Pointer-Parameter '*Symbol*' wird durch einen rvalue-Verweis übergeben. Stattdessen als Wert übergeben. Weitere Informationen finden [ C++ Sie in den Kern Richtlinien R. 34](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-owner).

[C26417 NO_LVALUE_REF_SHARED_PTR](C26417.md)\
Der Shared Pointer-Parameter '*Symbol*' wird als Verweis übergeben und nicht zurückgesetzt oder neu zugewiesen. Verwenden von T * "oder" T & stattdessen. Weitere Informationen finden [ C++ Sie in den Kern Richtlinien R. 35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam).

[C26418 NO_VALUE_OR_CONST_REF_SHARED_PTR](C26418.md)\
Der Shared Pointer-Parameter '*Symbol*' wird nicht kopiert oder verschoben. Verwenden von T * "oder" T & stattdessen. Weitere Informationen finden [ C++ Sie in den Kern Richtlinien R. 36](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rr-sharedptrparam-const).

## <a name="declaration-group"></a>Gruppe der DEKLARATION

[C26426 NO_GLOBAL_INIT_CALLS](C26426.md)\
Der globale Initialisierer Ruft eine nicht-constexpr-Funktion '*Symbol*' auf. Weitere Informationen finden [ C++ Sie unter Core Guidelines I. 22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[C26427 NO_GLOBAL_INIT_EXTERNS](C26427.md)\
Der globale Initialisierer greift auf das externe Objekt '*Symbol*' zu. Weitere Informationen finden [ C++ Sie unter Core Guidelines I. 22](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#i22-avoid-complex-initialization-of-global-objects).

[C26444 NO_UNNAMED_RAII_OBJECTS](c26444.md)\
Vermeiden Sie unbenannte Objekte mit benutzerdefinierter Konstruktion und Zerstörung. Siehe [es. 84: nicht (versuchen Sie es), eine lokale Variable ohne Namen zu deklarieren](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="class-group"></a>Gruppe der-Klasse

[C26432 DEFINE_OR_DELETE_SPECIAL_OPS](C26432.md)\
Wenn Sie einen Standard Vorgang im Typ '*Symbol*' definieren oder löschen, definieren oder löschen Sie alle. Weitere Informationen finden [ C++ Sie in den Kern Richtlinien C. 21](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c21-if-you-define-or-delete-any-default-operation-define-or-delete-them-all).

[C26433 OVERRIDE_EXPLICITLY](c26433.md)\
Die Funktion "*Symbol*" sollte mit "override" markiert werden. Weitere Informationen finden Sie [unter C. 128: virtuelle Funktionen sollten genau eine von Virtual, override oder Final angeben](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).

[C26434 DONT_HIDE_METHODS](C26434.md)\
Die Funktion '*symbol_1*' blendet eine nicht virtuelle Funktion '*symbol_2*' aus. Weitere Informationen finden [ C++ Sie in den Kern Richtlinien C. 128](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c128-virtual-functions-should-specify-exactly-one-of-virtual-override-or-final).

[C26435 SINGLE_VIRTUAL_SPECIFICATION](c26435.md)\
Die Funktion "*Symbol*" sollte genau eine von "Virtual", "override" oder "Final" angeben. Weitere Informationen finden Sie [unter C. 128: virtuelle Funktionen sollten genau eine von Virtual, override oder Final angeben](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

[C26436 NEED_VIRTUAL_DTOR](C26436.md)\
Der Typ "*Symbol*" mit einer virtuellen Funktion benötigt entweder einen öffentlichen virtuellen oder einen geschützten nicht virtuellen debugtor. Weitere Informationen finden [ C++ Sie in den Kern Richtlinien C. 35](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#c35-a-base-class-destructor-should-be-either-public-and-virtual-or-protected-and-nonvirtual).

[C26443 NO_EXPLICIT_DTOR_OVERRIDE](c26443.md)\
Der über schreibende Dekonstruktor darf keine expliziten Überschreibungs-oder Virtual-Spezifizierer verwenden. Weitere Informationen finden Sie [unter C. 128: virtuelle Funktionen sollten genau eine von Virtual, override oder Final angeben](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md).

## <a name="style-group"></a>STYLE-Gruppe

[C26438 NO_GOTO](C26438.md)\
Vermeiden Sie `goto`. Weitere Informationen finden [ C++ Sie unter Core Guidelines es. 76](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es76-avoid-goto).

## <a name="function-group"></a>Funktionsgruppe

[C26439 SPECIAL_NOEXCEPT](C26439.md)\
Diese Art von Funktion löst möglicherweise nicht aus. Deklarieren Sie Sie `noexcept`. Weitere Informationen finden [ C++ Sie unter Core Guidelines F. 6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[C26440 DECLARE_NOEXCEPT](C26440.md)\
Die Funktion '*Symbol*' kann als `noexcept`deklariert werden. Weitere Informationen finden [ C++ Sie unter Core Guidelines F. 6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept).

[C26447 DONT_THROW_IN_NOEXCEPT](c26447.md)\
Die-Funktion ist als " **noaußer** " deklariert, aber Ruft eine Funktion auf, die Ausnahmen auslösen kann.
Weitere Informationen finden [ C++ Sie Untergrund Legende Richtlinien: F. 6: Wenn die Funktion nicht auslöst, deklarieren Sie Sie mit Ausnahme](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#f6-if-your-function-may-not-throw-declare-it-noexcept)von.

## <a name="concurrency-group"></a>CONCURRENCY-Gruppe

[C26441 NO_UNNAMED_GUARDS](C26441.md)\
Wächter Objekte müssen benannt werden. Weitere Informationen finden [ C++ Sie in den Kern Richtlinien CP. 44](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#cp44-remember-to-name-your-lock_guards-and-unique_locks).

## <a name="const-group"></a>CONST-Gruppe

[C26460 USE_CONST_REFERENCE_ARGUMENTS](c26460.md)\
Das Verweis Argument '*Argument*' für die Funktion '*Function*' kann als `const`gekennzeichnet werden. Weitere Informationen finden [ C++ Sie unter Core Guidelines con. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[C26461 USE_CONST_POINTER_ARGUMENTS](c26461.md): \
Das Zeigerargument '*Argument*' für die Funktion '*Function*' kann als Zeiger auf `const`gekennzeichnet werden. Weitere Informationen finden [ C++ Sie unter Core Guidelines con. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-ref).

[C26462 USE_CONST_POINTER_FOR_VARIABLE](c26462.md)\
Der Wert, auf den '*Variable*' zeigt, wird nur einmal zugewiesen. Markieren Sie ihn als Zeiger auf `const`. Weitere Informationen finden [ C++ Sie unter Core Guidelines con. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26463 USE_CONST_FOR_ELEMENTS](c26463.md)\
Die Elemente des Arrays '*Array*' werden nur einmal zugewiesen, markieren Elemente `const`. Weitere Informationen finden [ C++ Sie unter Core Guidelines con. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26464 USE_CONST_POINTER_FOR_ELEMENTS](c26464.md)\
Die Werte, auf die Elemente des*Array Arrays zeigen*, werden nur einmal zugewiesen. Markieren Sie Elemente als Zeiger auf `const`. Weitere Informationen finden [ C++ Sie unter Core Guidelines con. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26496 USE_CONST_FOR_VARIABLE](c26496.md)\
Die Variable '*Variable*' wird nur einmal zugewiesen, markieren Sie Sie als `const`. Weitere Informationen finden [ C++ Sie unter Core Guidelines con. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#con4-use-const-to-define-objects-with-values-that-do-not-change-after-construction).

[C26497 USE_CONSTEXPR_FOR_FUNCTION](c26497.md)\
Diese Funktions *Funktion* kann als `constexpr` gekennzeichnet werden, wenn eine Kompilierzeit Auswertung gewünscht wird. Weitere Informationen finden [ C++ Sie unter Core Guidelines F. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rf-constexpr).

[C26498 USE_CONSTEXPR_FOR_FUNCTIONCALL](c26498.md)\
Diese Funktionsaufruf *Funktion* kann `constexpr` verwenden, wenn die Auswertung der Kompilierzeit gewünscht wird. Weitere Informationen finden [ C++ Sie unter Core Guidelines con. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Rconst-constexpr).

## <a name="type-group"></a>Typ-Gruppe

[C26437 DONT_SLICE](C26437.md)\
Nicht in Slice. Weitere Informationen finden [ C++ Sie unter Core Guidelines es. 63](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es63-dont-slice).

[C26465 NO_CONST_CAST_UNNECESSARY](c26465.md)\
Verwenden Sie `const_cast` nicht zum Umwandeln `const`. `const_cast` ist nicht erforderlich. constness oder Volatilität wird nicht durch diese Konvertierung entfernt. Weitere Informationen finden [ C++ Sie unter Core Guidelines Type. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-constcast).

[C26466 NO_STATIC_DOWNCAST_POLYMORPHIC](c26466.md)\
Verwenden Sie keine `static_cast` downcasts. Eine Umwandlung in einen polymorphen Typ sollten Dynamic_cast verwenden. Weitere Informationen finden [ C++ Sie unter Core Guidelines Type. 2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-downcast).

[C26471 NO_REINTERPRET_CAST_FROM_VOID_PTR](c26471.md)\
Verwenden Sie `reinterpret_cast`nicht. Eine Umwandlung aus void * kann `static_cast`verwenden. Weitere Informationen finden [ C++ Sie unter Core Guidelines Type. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26472 NO_CASTS_FOR_ARITHMETIC_CONVERSION](C26472.md)\
Verwenden Sie keine `static_cast` für arithmetische Konvertierungen. Verwenden Sie die Initialisierung von Klammern, gsl:: narrow_cast oder gsl:: Narrow. Weitere Informationen finden [ C++ Sie unter Core Guidelines Type. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26473 NO_IDENTITY_CAST](C26473.md)\
Konvertieren Sie nicht zwischen Zeiger Typen, bei denen der Quelltyp und der Zieltyp identisch sind. Weitere Informationen finden [ C++ Sie unter Core Guidelines Type. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26474 NO_IMPLICIT_CAST](C26474.md)\
Konvertieren Sie nicht zwischen Zeiger Typen, wenn die Konvertierung implizit sein könnte. Weitere Informationen finden [ C++ Sie unter Core Guidelines Type. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#Pro-type-reinterpretcast).

[C26475 NO_FUNCTION_STYLE_CASTS](C26475.md)\
Verwenden Sie keine C-casts im Funktions Stil. Weitere Informationen finden [ C++ Sie unter Core Guidelines es. 49](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es49-if-you-must-use-a-cast-use-a-named-cast).

[C26490 NO_REINTERPRET_CAST](c26490.md)\
Verwenden Sie `reinterpret_cast`nicht. Weitere Informationen finden [ C++ Sie unter Core Guidelines Type. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26491 NO_STATIC_DOWNCAST](c26490.md)\
Verwenden Sie keine `static_cast` downcasts. Weitere Informationen finden [ C++ Sie unter Core Guidelines Type. 2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26492 NO_CONST_CAST](c26492.md)\
Verwenden Sie `const_cast` nicht zum Umwandeln `const`. Weitere Informationen finden [ C++ Sie unter Core Guidelines Type. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26493 NO_CSTYLE_CAST](c26493.md)\
Verwenden Sie keine Umwandlungen im C-Stil. Weitere Informationen finden [ C++ Sie unter Core Guidelines Type. 4](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26494 VAR_USE_BEFORE_INIT](c26494.md)\
Die Variable '*Variable*' ist nicht initialisiert. Ein Objekt immer initialisiert werden. Weitere Informationen finden [ C++ Sie unter Core Guidelines Type. 5](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

[C26495 MEMBER_UNINIT](c26495.md)\
Die Variable '*Variable*' ist nicht initialisiert. Initialisieren Sie eine Membervariable immer. Weitere Informationen finden [ C++ Sie unter Core Guidelines Type. 6](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-type).

## <a name="bounds-group"></a>Gruppe von Grenzen

[C26446 USE_GSL_AT](c26446.md)\
Bevorzugen Sie die Verwendung von `gsl::at()` anstelle des nicht überprüften Index Operators. Weitere Informationen finden [ C++ Sie Untergrund Legende Richtlinien: Bounds. 4: Verwenden Sie keine Standard Bibliotheksfunktionen und-Typen, die nicht durch Grenzen geprüft werden](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

[C26481 NO_POINTER_ARITHMETIC](C26481.md)\
Verwenden Sie keine Zeigerarithmetik. Verwenden Sie stattdessen die Spanne. Siehe [ C++ Kern Leitlinien Begrenzungen. 1](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26482 NO_DYNAMIC_ARRAY_INDEXING](c26482.md)\
Indizieren Sie in Arrays nur mithilfe konstanter Ausdrücke. Siehe [ C++ Kern Leitlinien Begrenzungen. 2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26483 STATIC_INDEX_OUT_OF_RANGE](c26483.md)\
Der *Wertwert* liegt außerhalb der Grenzen (0, *gebunden*) der Variablen "*Variable*". Index nur mithilfe konstanter Ausdrücke, die innerhalb der Grenzen des Arrays sind Arrays. Siehe [ C++ Kern Leitlinien Begrenzungen. 2](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

[C26485 NO_ARRAY_TO_POINTER_DECAY](C26485.md)\
Ausdruck '*expr*': kein Array zu Zeiger Verfall. Siehe [ C++ Kern Leitlinien Begrenzungen. 3](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-bounds)

## <a name="gsl-group"></a>GSL-Gruppe

[C26445 NO_SPAN_REF](c26445.md)\
Ein Verweis auf `gsl::span` oder `std::string_view` ist möglicherweise ein Hinweis auf ein Problem mit der Lebensdauer.
Siehe [ C++ Kern Richtlinien GSL. View: views](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views)

[C26446 USE_GSL_AT](c26446.md)\
Bevorzugen Sie die Verwendung von `gsl::at()` anstelle des nicht überprüften Index Operators. Weitere Informationen finden [ C++ Sie Untergrund Legende Richtlinien: Bounds. 4: Verwenden Sie keine Standard Bibliotheksfunktionen und-Typen, die nicht durch Grenzen geprüft werden](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#probounds-bounds-safety-profile).

[C26448 USE_GSL_FINALLY](c26448.md)\
Verwenden Sie `gsl::finally`, wenn die endgültige Aktion beabsichtigt ist. Weitere Informationen finden [ C++ Sie Untergrund Legende Richtlinien: gsl. util: Hilfsprogramme](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#SS-utilities).

[C26449 NO_SPAN_FROM_TEMPORARY](c26449.md)\
`gsl::span` oder `std::string_view`, die aus einem temporären erstellt wurden, sind ungültig, wenn die temporäre ungültig erklärt wird. Weitere Informationen finden [ C++ Sie unter Core Guidelines: gsl. View: views](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#gslview-views).

## <a name="deprecated-warnings"></a>Veraltete Warnungen

Die folgenden Warnungen in einer frühen experimentelle Regelsatz von Core Richtlinien Checker, vorhanden sind, aber sind jetzt veraltet und können ignoriert werden. Die Warnungen werden durch Warnungen aus der obigen Liste abgelöst.

- 26412 DEREF_INVALID_POINTER
- 26413 DEREF_NULLPTR
- 26420 ASSIGN_NONOWNER_TO_EXPLICIT_OWNER
- 26421 ASSIGN_VALID_OWNER
- 26422 VALID_OWNER_LEAVING_SCOPE
- 26423 ALLOCATION_NOT_ASSIGNED_TO_OWNER
- 26424 VALID_ALLOCATION_LEAVING_SCOPE
- 26425 ASSIGNING_TO_STATIC
- 26499 NO_LIFETIME_TRACKING

## <a name="see-also"></a>Weitere Informationen

[Verwenden der C++ wichtigsten Leitfäden](using-the-cpp-core-guidelines-checkers.md)
