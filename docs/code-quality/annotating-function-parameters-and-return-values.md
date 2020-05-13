---
title: Kommentieren von Funktionsparametern und Rückgabewerten
description: Referenzhandbuch für Funktionsparameter und Rückgabewertanmerkungen.
ms.date: 10/15/2019
ms.topic: conceptual
f1_keywords:
- _Outptr_opt_result_bytebuffer_to_
- _Inout_updates_all_opt_
- _Post_equal_to_
- _Outptr_opt_result_maybenull_
- _Out_writes_bytes_all_
- _Out_writes_all_opt_
- _In_opt_
- _Outptr_
- _Outptr_result_maybenull_
- _Outref_result_bytebuffer_all_maybenull_
- _Inout_updates_opt_z_
- _Inout_updates_z_
- _Out_writes_
- _Out_writes_to_ptr_opt_z_
- _In_reads_to_ptr_opt_
- _Ret_writes_to_maybenull_
- _Outref_result_maybenull_
- _Ret_writes_bytes_
- _Outptr_result_bytebuffer_
- _Out_writes_opt_
- _Inout_updates_bytes_opt_
- _In_z_
- _Inout_updates_to_
- _Ret_maybenull_
- _Ret_writes_bytes_to_
- _Ret_z_
- _COM_Outptr_
- _Ret_maybenull_z_
- _Out_opt_
- _In_reads_opt_z_
- _Outptr_result_bytebuffer_to_
- _Ret_notnull_
- _COM_Outptr_opt_result_maybenull_
- _Inout_updates_to_opt_
- _Inout_updates_
- _Outptr_opt_result_buffer_
- _Outptr_result_buffer_to_
- _Out_writes_to_ptr_opt_
- _Out_writes_bytes_all_opt_
- _Inout_updates_all_
- _Deref_inout_range_
- _Ret_writes_
- _Out_writes_z_
- _Ret_writes_to_
- _Out_writes_to_ptr_z_
- _Out_writes_bytes_to_opt_
- _In_reads_or_z_
- _Inout_updates_bytes_to_
- _In_reads_z_
- _In_opt_z_
- _Outref_result_buffer_maybenull_
- _Ret_range_
- _COM_Outptr_opt_
- _Outptr_opt_result_maybenull_z_
- _In_reads_opt_
- _Inout_
- _Field_range_
- _Ret_writes_z_
- _Out_writes_to_
- _Out_writes_to_ptr_
- _Inout_opt_z_
- _Outref_
- _Deref_out_range_
- _Outref_result_buffer_
- _Outref_result_buffer_to_
- _Outref_result_bytebuffer_to_maybenull_
- _In_reads_bytes_
- _Outptr_opt_result_buffer_to_
- _Outref_result_buffer_all_
- _Out_writes_bytes_to_
- _Result_zeroonfailure_
- _In_reads_bytes_opt_
- _Outref_result_buffer_to_maybenull_
- _Outref_result_bytebuffer_all_
- _Outref_result_buffer_all_maybenull_
- _Ret_writes_maybenull_z_
- _In_range_
- _Inout_updates_bytes_all_opt_
- _Outref_result_bytebuffer_to_
- _Inout_updates_bytes_to_opt_
- _Pre_equal_to_
- _Ret_writes_bytes_maybenull_
- _COM_Outptr_result_maybenull_
- _Ret_writes_maybenull_
- _Out_writes_bytes_
- _Outptr_opt_
- _Out_writes_opt_z_
- _Outref_result_nullonfailure_
- _Outptr_opt_result_z_
- _Inout_opt_
- _Deref_in_range_
- _Outptr_result_z_
- _In_reads_to_ptr_opt_z_
- _Struct_size_bytes_
- _Outptr_result_nullonfailure_
- _In_
- _Inout_updates_bytes_
- _In_reads_to_ptr_z_
- _Ret_writes_bytes_to_maybenull
- _Outptr_opt_result_nullonfailure_
- _In_reads_to_ptr_
- _Outptr_result_buffer_
- _Out_
- _Outref_result_bytebuffer_maybenull_
- _Outptr_result_maybenull_z_
- _In_reads_
- _Inout_updates_opt_
- _Out_writes_to_opt_
- _Outptr_opt_result_bytebuffer_
- _Out_writes_all_
- _Out_range_
- _Inout_updates_bytes_all_
- _Inout_z_
- _Outref_result_bytebuffer_
- _Result_nullonfailure_
- _Ret_null_
- _Scanf_format_string_
- _Scanf_s_format_string_
- _Printf_format_string_
ms.assetid: 82826a3d-0c81-421c-8ffe-4072555dca3a
ms.openlocfilehash: c787dcfb252da1abe47251d66c46689db289cf15
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328010"
---
# <a name="annotating-function-parameters-and-return-values"></a>Kommentieren von Funktionsparametern und Rückgabewerten

In diesem Artikel werden typische Verwendungen von Anmerkungen für einfache Funktionsparameter – Skalar und Zeiger auf Strukturen und Klassen – und die meisten Arten von Puffern beschrieben. Dieser Artikel zeigt auch allgemeine Verwendungsmuster für Anmerkungen. Weitere Anmerkungen zu Funktionen finden Sie unter Kommentieren [des Funktionsverhaltens](../code-quality/annotating-function-behavior.md).

## <a name="pointer-parameters"></a>Zeigerparameter

Wenn bei den Anmerkungen in der folgenden Tabelle ein Zeigerparameter mit Anmerkungen angezeigt wird, meldet der Analyzer einen Fehler, wenn der Zeiger null ist. Diese Anmerkung gilt für Zeiger und alle Datenelemente, auf die verwiesen wird.

### <a name="annotations-and-descriptions"></a>Anmerkungen und Beschreibungen

- `_In_`

     Annotiert Eingabeparameter, die Skalar, Strukturen, Zeiger auf Strukturen und dergleichen sind. Explizit kann auf einfachen Skalarn verwendet werden. Der Parameter muss im Vorstatus gültig sein und wird nicht geändert.

- `_Out_`

     Annotiert Ausgabeparameter, die Skalar, Strukturen, Zeiger auf Strukturen und dergleichen sind. Wenden Sie diese Anmerkung nicht auf ein Objekt an, das keinen Wert zurückgeben kann, z. B. einen Skalar, der als Wert übergeben wird. Der Parameter muss nicht im Vorstatus gültig sein, sondern im Post-State.

- `_Inout_`

     Annotiert einen Parameter, der von der Funktion geändert wird. Sie muss sowohl im Vor- als auch im Post-State gültig sein, es wird jedoch davon ausgegangen, dass sie vor und nach dem Aufruf unterschiedliche Werte aufweisen. Muss auf einen veränderbaren Wert angewendet werden.

- `_In_z_`

     Ein Zeiger auf eine null-terminierte Zeichenfolge, die als Eingabe verwendet wird. Die Zeichenfolge muss im Vorstatus gültig sein. Varianten `PSTR`von , die bereits die richtigen Anmerkungen haben, werden bevorzugt.

- `_Inout_z_`

     Ein Zeiger auf ein null-terminiertes Zeichenarray, das geändert wird. Sie muss vor und nach dem Aufruf gültig sein, es wird jedoch davon ausgegangen, dass sich der Wert geändert hat. Der Null-Terminator kann verschoben werden, aber nur auf die Elemente bis zum ursprünglichen Null-Terminator kann zugegriffen werden.

- `_In_reads_(s)`

     `_In_reads_bytes_(s)`

     Ein Zeiger auf ein Array, das von der Funktion gelesen wird. Das Array besteht `s` aus Größenelementen, die alle gültig sein müssen.

     Die `_bytes_` Variante gibt die Größe in Bytes anstelle von Elementen an. Verwenden Sie diese Variante nur, wenn die Größe nicht als Elemente ausgedrückt werden kann. Zeichenfolgen `char` würden die `_bytes_` Variante z. B. `wchar_t` nur verwenden, wenn eine ähnliche Funktion verwendet würde.

- `_In_reads_z_(s)`

     Ein Zeiger auf ein Array, das null-terminiert ist und eine bekannte Größe hat. Die Elemente bis zum Null-Terminator – oder `s` wenn kein Null-Terminator vorhanden ist – müssen im Vorstatus gültig sein. Wenn die Größe in Bytes `s` bekannt ist, skalieren Sie nach der Elementgröße.

- `_In_reads_or_z_(s)`

     Ein Zeiger auf ein Array, das null-terminiert ist oder eine bekannte Größe hat, oder beides. Die Elemente bis zum Null-Terminator – oder `s` wenn kein Null-Terminator vorhanden ist – müssen im Vorstatus gültig sein. Wenn die Größe in Bytes `s` bekannt ist, skalieren Sie nach der Elementgröße. (Für die `strn` Familie verwendet.)

- `_Out_writes_(s)`

     `_Out_writes_bytes_(s)`

     Ein Zeiger auf ein `s` Array von Elementen (bzw. Bytes), die von der Funktion geschrieben werden. Die Arrayelemente müssen nicht im Vorstatus gültig sein, und die Anzahl der Elemente, die im Post-State gültig sind, ist nicht angegeben. Wenn anmerkungen zum Parametertyp vorhanden sind, werden diese im Post-State angewendet. Betrachten Sie hierzu den folgenden Beispielcode:

     ```cpp
     typedef _Null_terminated_ wchar_t *PWSTR;
     void MyStringCopy(_Out_writes_(size) PWSTR p1, _In_ size_t size, _In_ PWSTR p2);
     ```

     In diesem Beispiel stellt der Aufrufer einen Puffer mit `size` Elementen für `p1`bereit. `MyStringCopy`macht einige dieser Elemente gültig. Noch wichtiger `_Null_terminated_` ist, `PWSTR` dass `p1` die Anmerkung auf Mittel, die null-beendet in Post-State ist. Auf diese Weise ist die Anzahl der gültigen Elemente noch genau definiert, aber eine bestimmte Elementanzahl ist nicht erforderlich.

     Die `_bytes_` Variante gibt die Größe in Bytes anstelle von Elementen an. Verwenden Sie diese Variante nur, wenn die Größe nicht als Elemente ausgedrückt werden kann. Zeichenfolgen `char` würden die `_bytes_` Variante z. B. `wchar_t` nur verwenden, wenn eine ähnliche Funktion verwendet würde.

- `_Out_writes_z_(s)`

     Ein Zeiger auf ein `s` Array von Elementen. Die Elemente müssen nicht im Vorstatus gültig sein. Im Post-State müssen die Elemente bis zum Null-Terminator , der vorhanden sein muss, gültig sein. Wenn die Größe in Bytes `s` bekannt ist, skalieren Sie nach der Elementgröße.

- `_Inout_updates_(s)`

     `_Inout_updates_bytes_(s)`

     Ein Zeiger auf ein Array, das in der Funktion gelesen und geschrieben wird. Es ist von `s` Größenelementen und gültig im Vor- und Nachzustand.

     Die `_bytes_` Variante gibt die Größe in Bytes anstelle von Elementen an. Verwenden Sie diese Variante nur, wenn die Größe nicht als Elemente ausgedrückt werden kann. Zeichenfolgen `char` würden die `_bytes_` Variante z. B. `wchar_t` nur verwenden, wenn eine ähnliche Funktion verwendet würde.

- `_Inout_updates_z_(s)`

     Ein Zeiger auf ein Array, das null-beendet ist und eine bekannte Größe hat. Die Elemente bis zum Null-Terminator, die vorhanden sein müssen, müssen sowohl im Vor- als auch im Post-State gültig sein. Es wird davon ausgegangen, dass sich der Wert im Post-State vom Wert im Vor-Zustand unterscheidet. die die Position des Nullabschlusses enthält. Wenn die Größe in Bytes `s` bekannt ist, skalieren Sie nach der Elementgröße.

- `_Out_writes_to_(s,c)`

     `_Out_writes_bytes_to_(s,c)`

     `_Out_writes_all_(s)`

     `_Out_writes_bytes_all_(s)`

     Ein Zeiger auf ein `s` Array von Elementen. Die Elemente müssen nicht im Vorstatus gültig sein. Im Post-State müssen die `c`Elemente bis zum -th-Element gültig sein. Die `_bytes_` Variante kann verwendet werden, wenn die Größe in Bytes und nicht in der Anzahl der Elemente bekannt ist.

     Beispiel:

     ```cpp
     void *memcpy(_Out_writes_bytes_all_(s) char *p1, _In_reads_bytes_(s) char *p2, _In_ int s);
     void *wordcpy(_Out_writes_all_(s) DWORD *p1, _In_reads_(s) DWORD *p2, _In_ int s);
     ```

- `_Inout_updates_to_(s,c)`

     `_Inout_updates_bytes_to_(s,c)`

     Ein Zeiger auf ein Array, das sowohl von der Funktion gelesen als auch geschrieben wird. Es handelt sich `s` um Größenelemente, die alle im Vorstatus gültig sein müssen, und `c` Elemente müssen im Post-State gültig sein.

     Die `_bytes_` Variante gibt die Größe in Bytes anstelle von Elementen an. Verwenden Sie diese Variante nur, wenn die Größe nicht als Elemente ausgedrückt werden kann. Zeichenfolgen `char` würden die `_bytes_` Variante z. B. `wchar_t` nur verwenden, wenn eine ähnliche Funktion verwendet würde.

- `_Inout_updates_all_(s)`

     `_Inout_updates_bytes_all_(s)`

     Ein Zeiger auf ein Array, das sowohl von der `s` Funktion von Größenelementen gelesen als auch geschrieben wird. Definiert als äquivalent zu:

     `_Inout_updates_to_(_Old_(s), _Old_(s))    _Inout_updates_bytes_to_(_Old_(s), _Old_(s))`

     Mit anderen Worten, jedes Element, das `s` im Puffer bis zum Vorstatus vorhanden ist, ist im Vor- und Nachzustand gültig.

     Die `_bytes_` Variante gibt die Größe in Bytes anstelle von Elementen an. Verwenden Sie diese Variante nur, wenn die Größe nicht als Elemente ausgedrückt werden kann. Zeichenfolgen `char` würden die `_bytes_` Variante z. B. `wchar_t` nur verwenden, wenn eine ähnliche Funktion verwendet würde.

- `_In_reads_to_ptr_(p)`

     Ein Zeiger auf ein `p - _Curr_` Array, für `p` `_Curr_`das (d. h. minus ) ein gültiger Ausdruck ist. Die Elemente `p` davor müssen im Vorstatus gültig sein.

    Beispiel:

    ```cpp
    int ReadAllElements(_In_reads_to_ptr_(EndOfArray) const int *Array, const int *EndOfArray);
    ```

- `_In_reads_to_ptr_z_(p)`

     Ein Zeiger auf ein null-terminiertes `p - _Curr_` Array, `p` für `_Curr_`das Ausdruck (d. h. minus ) ein gültiger Ausdruck ist. Die Elemente `p` davor müssen im Vorstatus gültig sein.

- `_Out_writes_to_ptr_(p)`

     Ein Zeiger auf ein `p - _Curr_` Array, für `p` `_Curr_`das (d. h. minus ) ein gültiger Ausdruck ist. Die Elemente `p` davor müssen nicht im Vor-Status gültig sein und im Post-State gültig sein.

- `_Out_writes_to_ptr_z_(p)`

     Ein Zeiger auf ein null-terminiertes Array, für das `p - _Curr_` (d. h. `p` minus `_Curr_`) ein gültiger Ausdruck ist. Die Elemente `p` davor müssen nicht im Vor-Status gültig sein und im Post-State gültig sein.

## <a name="optional-pointer-parameters"></a>Optionale Zeigerparameter

Wenn eine Zeigerparameteranmerkung `_opt_`enthält, gibt dies an, dass der Parameter null sein kann. Andernfalls verhält sich die Anmerkung genauso wie die Version, die nicht enthält. `_opt_` Hier ist eine `_opt_` Liste der Varianten der Zeigerparameter-Anmerkungen:

||||
|-|-|-|
|`_In_opt_`<br /><br /> `_Out_opt_`<br /><br /> `_Inout_opt_`<br /><br /> `_In_opt_z_`<br /><br /> `_Inout_opt_z_`<br /><br /> `_In_reads_opt_`<br /><br /> `_In_reads_bytes_opt_`<br /><br /> `_In_reads_opt_z_`|`_Out_writes_opt_`<br /><br /> `_Out_writes_opt_z_`<br /><br /> `_Inout_updates_opt_`<br /><br /> `_Inout_updates_bytes_opt_`<br /><br /> `_Inout_updates_opt_z_`<br /><br /> `_Out_writes_to_opt_`<br /><br /> `_Out_writes_bytes_to_opt_`<br /><br /> `_Out_writes_all_opt_`<br /><br /> `_Out_writes_bytes_all_opt_`|`_Inout_updates_to_opt_`<br /><br /> `_Inout_updates_bytes_to_opt_`<br /><br /> `_Inout_updates_all_opt_`<br /><br /> `_Inout_updates_bytes_all_opt_`<br /><br /> `_In_reads_to_ptr_opt_`<br /><br /> `_In_reads_to_ptr_opt_z_`<br /><br /> `_Out_writes_to_ptr_opt_`<br /><br /> `_Out_writes_to_ptr_opt_z_`|

## <a name="output-pointer-parameters"></a>Ausgabezeigerparameter

Ausgabezeigerparameter erfordern eine spezielle Notation, um die Nulligkeit des Parameters und der Pointed-to-Position zu disambiguieren.

### <a name="annotations-and-descriptions"></a>Anmerkungen und Beschreibungen

- `_Outptr_`

   Parameter kann nicht NULL sein, und im Post-State kann die Pointed-to-Position nicht null sein und muss gültig sein.

- `_Outptr_opt_`

   Der Parameter kann null sein, aber im Post-State kann die Pointed-to-Position nicht null sein und muss gültig sein.

- `_Outptr_result_maybenull_`

   Parameter kann nicht null sein, und im Post-State kann die Pointed-to-Position null sein.

- `_Outptr_opt_result_maybenull_`

   Der Parameter kann null sein, und im Post-State kann die Pointed-to-Position null sein.

  In der folgenden Tabelle werden zusätzliche Teilzeichenfolgen in den Anmerkungsnamen eingefügt, um die Bedeutung der Anmerkung weiter zu qualifizieren. Die verschiedenen Teilzeichenfolgen `_buffer_` `_bytebuffer_`sind `_z`, `_COM_`, , und `_to_`.

> [!IMPORTANT]
> Wenn die Schnittstelle, die Sie mit Anmerkungen benoten, COM ist, verwenden Sie die COM-Form dieser Anmerkungen. Verwenden Sie die COM-Anmerkungen nicht mit einer anderen Typschnittstelle.

- `_Outptr_result_z_`

   `_Outptr_opt_result_z_`

   `_Outptr_result_maybenull_z_`

   `_Outptr_opt_result_maybenull_z_`

   Der zurückgegebene Zeiger `_Null_terminated_` hat die Anmerkung.

- `_COM_Outptr_`

   `_COM_Outptr_opt_`

   `_COM_Outptr_result_maybenull_`

   `_COM_Outptr_opt_result_maybenull_`

   Der zurückgegebene Zeiger verfügt über COM-Semantik und trägt daher eine `_On_failure_` Postbedingung, dass der zurückgegebene Zeiger null ist.

- `_Outptr_result_buffer_(s)`

   `_Outptr_result_bytebuffer_(s)`

   `_Outptr_opt_result_buffer_(s)`

   `_Outptr_opt_result_bytebuffer_(s)`

   Der zurückgegebene Zeiger zeigt auf `s` einen gültigen Puffer mit Größenelementen oder Bytes.

- `_Outptr_result_buffer_to_(s, c)`

   `_Outptr_result_bytebuffer_to_(s, c)`

   `_Outptr_opt_result_buffer_to_(s,c)`

   `_Outptr_opt_result_bytebuffer_to_(s,c)`

   Der zurückgegebene Zeiger zeigt auf `s` einen Puffer von Größenelementen oder Bytes, von denen der erste `c` gültig ist.

Bestimmte Schnittstellenkonventionen gehen davon aus, dass Ausgabeparameter bei einem Fehler für ungültig erklärt werden. Mit Ausnahme von explizit COM-Code werden die Formulare in der folgenden Tabelle bevorzugt. Verwenden Sie für COM-Code die entsprechenden COM-Formulare, die im vorherigen Abschnitt aufgeführt sind.

- `_Result_nullonfailure_`

   Ändert andere Anmerkungen. Das Ergebnis wird auf null gesetzt, wenn die Funktion fehlschlägt.

- `_Result_zeroonfailure_`

   Ändert andere Anmerkungen. Das Ergebnis wird auf Null gesetzt, wenn die Funktion fehlschlägt.

- `_Outptr_result_nullonfailure_`

   Der zurückgegebene Zeiger zeigt auf einen gültigen Puffer, wenn die Funktion erfolgreich ist, oder NULL, wenn die Funktion fehlschlägt. Diese Anmerkung ist für einen nicht optionalen Parameter.

- `_Outptr_opt_result_nullonfailure_`

   Der zurückgegebene Zeiger zeigt auf einen gültigen Puffer, wenn die Funktion erfolgreich ist, oder NULL, wenn die Funktion fehlschlägt. Diese Anmerkung ist für einen optionalen Parameter.

- `_Outref_result_nullonfailure_`

   Der zurückgegebene Zeiger zeigt auf einen gültigen Puffer, wenn die Funktion erfolgreich ist, oder NULL, wenn die Funktion fehlschlägt. Diese Anmerkung ist für einen Referenzparameter.

## <a name="output-reference-parameters"></a>Ausgabereferenzparameter

Eine häufige Verwendung des Referenzparameters ist für Ausgabeparameter. Für einfache Ausgabereferenzparameter `int&` `_Out_` wie , stellt die richtige Semantik zur Verfügung. Wenn der Ausgabewert jedoch ein Zeiger `int *&`wie ist, stellen die `_Outptr_ int **` entsprechenden Zeigeranmerkungen wie nicht die richtige Semantik bereit. Um die Semantik von Ausgabereferenzparametern für Zeigertypen prägnant auszudrücken, verwenden Sie diese zusammengesetzten Anmerkungen:

### <a name="annotations-and-descriptions"></a>Anmerkungen und Beschreibungen

- `_Outref_`

     Das Ergebnis muss im Post-State gültig sein und darf nicht null sein.

- `_Outref_result_maybenull_`

     Das Ergebnis muss im Post-State gültig sein, kann aber im Post-State null sein.

- `_Outref_result_buffer_(s)`

     Das Ergebnis muss im Post-State gültig sein und darf nicht null sein. Zeigt auf einen `s` gültigen Puffer von Größenelementen.

- `_Outref_result_bytebuffer_(s)`

     Das Ergebnis muss im Post-State gültig sein und darf nicht null sein. Zeigt auf einen `s` gültigen Puffer mit Größe Bytes.

- `_Outref_result_buffer_to_(s, c)`

     Das Ergebnis muss im Post-State gültig sein und darf nicht null sein. Punkte zum `s` Puffer von Elementen, `c` von denen die ersten gültig sind.

- `_Outref_result_bytebuffer_to_(s, c)`

     Das Ergebnis muss im Post-State gültig sein und darf nicht null sein. Punkte auf `s` Puffer von Bytes, von denen die ersten `c` gültig sind.

- `_Outref_result_buffer_all_(s)`

     Das Ergebnis muss im Post-State gültig sein und darf nicht null sein. Zeigt auf gültigen `s` Puffer gültiger Elemente der Größe.

- `_Outref_result_bytebuffer_all_(s)`

     Das Ergebnis muss im Post-State gültig sein und darf nicht null sein. Verweist auf den `s` gültigen Puffer von Bytes gültiger Elemente.

- `_Outref_result_buffer_maybenull_(s)`

     Das Ergebnis muss im Post-State gültig sein, kann aber im Post-State null sein. Zeigt auf einen `s` gültigen Puffer von Größenelementen.

- `_Outref_result_bytebuffer_maybenull_(s)`

     Das Ergebnis muss im Post-State gültig sein, kann aber im Post-State null sein. Zeigt auf einen `s` gültigen Puffer mit Größe Bytes.

- `_Outref_result_buffer_to_maybenull_(s, c)`

     Das Ergebnis muss im Post-State gültig sein, kann aber im Post-State null sein. Punkte zum `s` Puffer von Elementen, `c` von denen die ersten gültig sind.

- `_Outref_result_bytebuffer_to_maybenull_(s,c)`

     Das Ergebnis muss im Post-State gültig sein, kann jedoch null im Post-Status sein. Punkte auf `s` Puffer von Bytes, von denen die ersten `c` gültig sind.

- `_Outref_result_buffer_all_maybenull_(s)`

     Das Ergebnis muss im Post-State gültig sein, kann jedoch null im Post-Status sein. Zeigt auf gültigen `s` Puffer gültiger Elemente der Größe.

- `_Outref_result_bytebuffer_all_maybenull_(s)`

     Das Ergebnis muss im Post-State gültig sein, kann jedoch null im Post-Status sein. Verweist auf den `s` gültigen Puffer von Bytes gültiger Elemente.

## <a name="return-values"></a>Rückgabewerte

Der Rückgabewert einer Funktion `_Out_` ähnelt einem Parameter, befindet sich jedoch auf einer anderen Ebene der Dereferenzierung, und Sie müssen das Konzept des Zeigers auf das Ergebnis nicht berücksichtigen. Bei den folgenden Anmerkungen ist der Rückgabewert das annotierte Objekt – ein Skalar, ein Zeiger auf eine Struktur oder ein Zeiger auf einen Puffer. Diese Anmerkungen haben die gleiche Semantik wie die entsprechende `_Out_` Anmerkung.

|||
|-|-|
|`_Ret_z_`<br /><br /> `_Ret_writes_(s)`<br /><br /> `_Ret_writes_bytes_(s)`<br /><br /> `_Ret_writes_z_(s)`<br /><br /> `_Ret_writes_to_(s,c)`<br /><br /> `_Ret_writes_maybenull_(s)`<br /><br /> `_Ret_writes_to_maybenull_(s)`<br /><br /> `_Ret_writes_maybenull_z_(s)`|`_Ret_maybenull_`<br /><br /> `_Ret_maybenull_z_`<br /><br /> `_Ret_null_`<br /><br /> `_Ret_notnull_`<br /><br /> `_Ret_writes_bytes_to_`<br /><br /> `_Ret_writes_bytes_maybenull_`<br /><br /> `_Ret_writes_bytes_to_maybenull_`|

## <a name="format-string-parameters"></a>Formatieren von Zeichenfolgenparametern

- `_Printf_format_string_`Gibt an, dass es sich bei `printf` dem Parameter um eine Formatzeichenfolge für die Verwendung in einem Ausdruck handelt.

     **Beispiel**

    ```cpp
    int MyPrintF(_Printf_format_string_ const wchar_t* format, ...)
    {
           va_list args;
           va_start(args, format);
           int ret = vwprintf(format, args);
           va_end(args);
           return ret;
    }
    ```

- `_Scanf_format_string_`Gibt an, dass es sich bei `scanf` dem Parameter um eine Formatzeichenfolge für die Verwendung in einem Ausdruck handelt.

     **Beispiel**

    ```cpp
    int MyScanF(_Scanf_format_string_ const wchar_t* format, ...)
    {
           va_list args;
           va_start(args, format);
           int ret = vwscanf(format, args);
           va_end(args);
           return ret;
    }
    ```

- `_Scanf_s_format_string_`Gibt an, dass es sich bei `scanf_s` dem Parameter um eine Formatzeichenfolge für die Verwendung in einem Ausdruck handelt.

     **Beispiel**

    ```cpp
    int MyScanF_s(_Scanf_s_format_string_ const wchar_t* format, ...)
    {
           va_list args;
           va_start(args, format);
           int ret = vwscanf_s(format, args);
           va_end(args);
           return ret;
    }
    ```

## <a name="other-common-annotations"></a>Andere häufige Anmerkungen

### <a name="annotations-and-descriptions"></a>Anmerkungen und Beschreibungen

- `_In_range_(low, hi)`

     `_Out_range_(low, hi)`

     `_Ret_range_(low, hi)`

     `_Deref_in_range_(low, hi)`

     `_Deref_out_range_(low, hi)`

     `_Deref_inout_range_(low, hi)`

     `_Field_range_(low, hi)`

     Der Parameter, das Feld oder das Ergebnis `low` befindet `hi`sich im Bereich (inklusive) von . `_Satisfies_(_Curr_ >= low && _Curr_ <= hi)` Entspricht dem auf das benotete Objekt zusammen mit den entsprechenden Vor- oder Nachstatusbedingungen.

    > [!IMPORTANT]
    > Obwohl die Namen "in" und "out" enthalten, `_Out_` **gilt** die Semantik und `_In_` nicht für diese Anmerkungen.

- `_Pre_equal_to_(expr)`

     `_Post_equal_to_(expr)`

     Der annotierte Wert `expr`ist genau . `_Satisfies_(_Curr_ == expr)` Entspricht dem auf das benotete Objekt zusammen mit den entsprechenden Vor- oder Nachstatusbedingungen.

- `_Struct_size_bytes_(size)`

     Gilt für eine Struktur- oder Klassendeklaration. Gibt an, dass ein gültiges Objekt dieses Typs größer als der `size`deklarierte Typ sein kann, wobei die Anzahl der Bytes von angegeben wird. Beispiel:

     `typedef _Struct_size_bytes_(nSize) struct MyStruct {    size_t nSize;    ... };`

     Die Puffergröße in Bytes `pM` eines `MyStruct *` Typparameters wird dann wie:

     `min(pM->nSize, sizeof(MyStruct))`

## <a name="related-resources"></a>Verwandte Ressourcen

[Blog zum Codeanalyseteam](https://blogs.msdn.microsoft.com/codeanalysis/)

## <a name="see-also"></a>Siehe auch

- [Verwenden von SAL-Anmerkungen zum Reduzieren von C/C++-Codefehlern](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Einführung in SAL](../code-quality/understanding-sal.md)
- [Hinzufügen einer Anmerkung zum Funktionsverhalten](../code-quality/annotating-function-behavior.md)
- [Hinzufügen einer Anmerkung zu Strukturen und Klassen](../code-quality/annotating-structs-and-classes.md)
- [Hinzufügen einer Anmerkung zum Sperrverhalten](../code-quality/annotating-locking-behavior.md)
- [Angeben, wann und wo eine Anmerkung gültig ist](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Intrinsische Funktionen](../code-quality/intrinsic-functions.md)
- [Empfohlene Vorgehensweisen und Beispiele](../code-quality/best-practices-and-examples-sal.md)
