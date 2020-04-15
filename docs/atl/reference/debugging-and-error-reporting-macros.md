---
title: Debuggen und Fehlerberichterstattungsmakros
ms.date: 05/06/2019
f1_keywords:
- atldef/ATL::_ATL_DEBUG_INTERFACES
- atldef/ATL::_ATL_DEBUG_QI
- atldef/ATL::ATLASSERT
- afx/ATL::ATLENSURE
- atltrace/ATL::ATLTRACENOTIMPL
- atltrace/ATL::ATLTRACE
helpviewer_keywords:
- macros, error reporting
ms.assetid: 4da9b87f-ec5c-4a32-ab93-637780909b9d
ms.openlocfilehash: 69ab6e17bfb1ec85ddb5b8c19c18010a9b4f3df6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330188"
---
# <a name="debugging-and-error-reporting-macros"></a>Debuggen und Fehlerberichterstattungsmakros

Diese Makros bieten nützliche Debugging- und Ablaufverfolgungsfunktionen.

|||
|-|-|
|[_ATL_DEBUG_INTERFACES](#_atl_debug_interfaces)|Schreibt in das Ausgabefenster alle Schnittstellenlecks, `_Module.Term` die beim Aufruf erkannt werden.|
|[_ATL_DEBUG_QI](#_atl_debug_qi)|Schreibt alle `QueryInterface` Aufrufe in das Ausgabefenster.|
|[ATLASSERT](#atlassert)|Führt die gleiche Funktionalität aus wie das [_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) Makros, das in der C-Laufzeitbibliothek gefunden wurde.|
|[ATLENSURE](#atlensure)|Führt die Parameterüberprüfung durch. Anruf `AtlThrow` bei Bedarf|
|[ATLTRACENOTIMPL](#atltracenotimpl)|Sendet eine Meldung an das Dumpgerät, dass die angegebene Funktion nicht implementiert ist.|
|[ATLTRACE](#atltrace)|Meldet Warnungen an ein Ausgabegerät, z. B. das Debuggerfenster, entsprechend den angegebenen Flags und Ebenen. Für Abwärtskompatibilität enthalten.|
|[ATLTRACE2](#atltrace2)|Meldet Warnungen an ein Ausgabegerät, z. B. das Debuggerfenster, entsprechend den angegebenen Flags und Ebenen.|

## <a name="_atl_debug_interfaces"></a><a name="_atl_debug_interfaces"></a>_ATL_DEBUG_INTERFACES

Definieren Sie dieses Makro, bevor Sie `AddRef` ATL-Headerdateien einschließen, um alle Schnittstellen Ihrer `Release` Komponenten und Aufrufe zum Ausgabefenster nachzuverfolgen.

```
#define _ATL_DEBUG_INTERFACES
```

### <a name="remarks"></a>Bemerkungen

Die Ablaufverfolgungsausgabe wird wie unten gezeigt angezeigt:

`ATL: QIThunk - 2008         AddRef  :   Object = 0x00d81ba0   Refcount = 1   CBug - IBug`

Der erste Teil jeder Ablaufverfolgung ist `ATL: QIThunk`immer . Als Nächstes ist ein Wert, der den verwendeten *Schnittstellen-Thunk* identifiziert. Ein Schnittstellen-Thunk ist ein Objekt, das verwendet wird, um eine Verweisanzahl beizubehalten und die hier verwendete Ablaufverfolgungsfunktion bereitzustellen. Bei jedem Aufruf wird ein neuer `QueryInterface` Schnittstellen-Thunk `IUnknown` erstellt, mit Ausnahme von Anforderungen für die Schnittstelle (in diesem Fall wird derselbe Thunk jedes Mal zurückgegeben, um die Identitätsregeln von COM einzuhalten).

Als Nächstes sehen `AddRef` `Release` oder geben Sie an, welche Methode aufgerufen wurde. Anschließend wird ein Wert angezeigt, der das Objekt identifiziert, dessen Schnittstellenverweisanzahl geändert wurde. Der nachverfolgte Wert ist der **Zeiger** des Objekts.

Die Referenzanzahl, die verfolgt wird, ist die `AddRef` `Release` Referenzanzahl für diesen Thunk nach oder wurde aufgerufen. Beachten Sie, dass diese Verweisanzahl möglicherweise nicht mit der Referenzanzahl für das Objekt übereinstimmt. Jeder Thunk behält seine eigene Referenzanzahl bei, damit Sie die Referenzzählregeln von COM vollständig einhalten können.

Die letzte zurückverfolgte Information ist der Name des Objekts `AddRef` `Release` und die Schnittstelle, die von dem oder Aufruf betroffen ist.

Alle Schnittstellenlecks, die beim Herunterfahren `_Module.Term` des Servers erkannt werden und aufgerufen werden, werden wie folgt protokolliert:

`ATL: QIThunk - 2005         LEAK    :   Object = 0x00d81ca0   Refcount = 1   MaxRefCount = 1   CBug - IBug`

Die hier bereitgestellten Informationen werden direkt den Informationen in den vorherigen Ablaufverfolgungsanweisungen zugeordnet, sodass Sie die Referenzanzahl über die gesamte Lebensdauer eines Schnittstellen-Thunks untersuchen können. Darüber hinaus erhalten Sie eine Angabe der maximalen Referenzanzahl auf diesem Schnittstellen-Thunk.

> [!NOTE]
> _ATL_DEBUG_INTERFACES kann in Einzelhandelsbuilds verwendet werden.

## <a name="_atl_debug_qi"></a><a name="_atl_debug_qi"></a>_ATL_DEBUG_QI

Schreibt alle `QueryInterface` Aufrufe in das Ausgabefenster.

```
#define _ATL_DEBUG_QI
```

### <a name="remarks"></a>Bemerkungen

Wenn ein `QueryInterface` Aufruf zum Fehler auftritt, wird im Ausgabefenster folgende Anzeigen angezeigt:

*Schnittstellenname* - `failed`

## <a name="atlassert"></a><a name="atlassert"></a>ATLASSERT

Das ATLASSERT-Makro führt die gleiche Funktionalität aus wie das [_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) Makroin der C-Laufzeitbibliothek.

```
ATLASSERT(booleanExpression);
```

### <a name="parameters"></a>Parameter

*booleanExpression*<br/>
Ausdruck (einschließlich Zeiger), der auf Uneinlauter oder 0 ausgewertet wird.

### <a name="remarks"></a>Bemerkungen

In Debugbuilds wertet ATLASSERT *booleanExpression* aus und generiert einen Debugbericht, wenn das Ergebnis false ist.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atldef.h

## <a name="atlensure"></a><a name="atlensure"></a>ATLENSURE

Dieses Makro wird verwendet, um Parameter zu überprüfen, die an eine Funktion übergeben werden.

```
ATLENSURE(booleanExpression);
ATLENSURE_THROW(booleanExpression, hr);
```

### <a name="parameters"></a>Parameter

*booleanExpression*<br/>
Gibt einen booleschen Ausdruck an, der getestet werden soll.

*Hr*<br/>
Gibt einen zurückzugebenden Fehlercode an.

### <a name="remarks"></a>Bemerkungen

Diese Makros bieten einen Mechanismus, um den Benutzer über eine falsche Parameterverwendung zu erkennen und zu benachrichtigen.

Das Makro ruft ATLASSERT auf `AtlThrow`und ruft, wenn die Bedingung fehlschlägt, auf .

Im Fall ATLENSURE `AtlThrow` wird mit E_FAIL aufgerufen.

Im ATLENSURE_THROW Fall `AtlThrow` wird mit dem angegebenen HRESULT aufgerufen.

Der Unterschied zwischen ATLENSURE und ATLASSERT besteht darin, dass ATLENSURE sowohl in Release-Builds als auch in Debug-Builds eine Ausnahme auslöst.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#108](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_1.cpp)]

## <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="atltracenotimpl"></a><a name="atltracenotimpl"></a>ATLTRACENOTIMPL

In Debugbuilds von ATL sendet die Zeichenfolge *"funcname* is not implemented" an das Dump-Gerät und gibt E_NOTIMPL zurück.

```
ATLTRACENOTIMPL(funcname);
```

### <a name="parameters"></a>Parameter

*Funcname*<br/>
[in] Eine Zeichenfolge, die den Namen der Funktion enthält, die nicht implementiert ist.

### <a name="remarks"></a>Bemerkungen

In Release-Builds gibt einfach E_NOTIMPL zurück.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#127](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_2.cpp)]

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atltrace.h

## <a name="atltrace"></a><a name="atltrace"></a>ATLTRACE

Meldet Warnungen an ein Ausgabegerät, z. B. das Debuggerfenster, entsprechend den angegebenen Flags und Ebenen. Für Abwärtskompatibilität enthalten.

```
ATLTRACE(exp);

ATLTRACE(
    DWORD category,
    UINT  level,
    LPCSTR lpszFormat, ...);
```

### <a name="parameters"></a>Parameter

*Exp*<br/>
[in] Die Zeichenfolge und die Variablen, die an das Ausgabefenster oder eine Anwendung gesendet werden sollen, die diese Nachrichten abfängt.

*category*<br/>
[in] Typ des Ereignisses oder der Methode, für die berichten soll. Eine Liste der Kategorien finden Sie in den Anmerkungen.

*Ebene*<br/>
[in] Die Ebene der zu meldenden Ablaufverfolgung. Weitere Informationen finden Sie in den Erläuterungen.

*lpszFormat*<br/>
[in] Die formatierte Zeichenfolge, die an das Dumpgerät gesendet werden soll.

### <a name="remarks"></a>Bemerkungen

Eine Beschreibung von ATLTRACE finden Sie unter [ATLTRACE2.](#atltrace2) ATLTRACE und ATLTRACE2 haben das gleiche Verhalten, ATLTRACE ist aus Gründen der Abwärtskompatibilität enthalten.

## <a name="atltrace2"></a><a name="atltrace2"></a>ATLTRACE2

Meldet Warnungen an ein Ausgabegerät, z. B. das Debuggerfenster, entsprechend den angegebenen Flags und Ebenen.

```
ATLTRACE2(exp);

ATLTRACE2(
    DWORD category,
    UINT level,
    LPCSTR lpszFormat,  ...);
```

### <a name="parameters"></a>Parameter

*Exp*<br/>
[in] Die Zeichenfolge, die an das Ausgabefenster oder eine Anwendung gesendet werden soll, die diese Nachrichten abfängt.

*category*<br/>
[in] Typ des Ereignisses oder der Methode, für die berichten soll. Eine Liste der Kategorien finden Sie in den Anmerkungen.

*Ebene*<br/>
[in] Die Ebene der zu meldenden Ablaufverfolgung. Weitere Informationen finden Sie in den Erläuterungen.

*lpszFormat*<br/>
[in] Die `printf`Formatzeichenfolge -style, die zum Erstellen einer Zeichenfolge verwendet werden soll, die an das Dumpgerät gesendet werden soll.

### <a name="remarks"></a>Bemerkungen

Die Kurzform von ATLTRACE2 schreibt eine Zeichenfolge in das Ausgabefenster des Debuggers. Die zweite Form von ATLTRACE2 schreibt auch die Ausgabe in das Ausgabefenster des Debuggers, unterliegt jedoch den Einstellungen des ATL/MFC Trace Tool (siehe [ATLTraceTool-Beispiel](../../overview/visual-cpp-samples.md)). Wenn Sie beispielsweise *Die Stufe* auf 4 und das ATL/MFC-Ablaufverfolgungstool auf Stufe 0 festlegen, wird die Meldung nicht angezeigt. *0,* 1, 2, 3 oder 4 sein. Die Standardeinstellung 0 meldet nur die schwerwiegendsten Probleme.

Der *Kategorieparameter* listet die festzulegenden Ablaufverfolgungsflags auf. Diese Flags entsprechen den Methodentypen, für die Sie Bericht erstatten möchten. In den folgenden Tabellen sind die gültigen Ablaufverfolgungsflags aufgeführt, die Sie für den *Kategorieparameter* verwenden können.

### <a name="atl-trace-flags"></a>ATL-Ablaufverfolgungsflags

|ATL-Kategorie|BESCHREIBUNG|
|------------------|-----------------|
|`atlTraceGeneral`|Berichte zu allen ATL-Anwendungen. Der Standardwert.|
|`atlTraceCOM`|Berichte zu COM-Methoden.|
|`atlTraceQI`|Berichte zu QueryInterface-Aufrufen.|
|`atlTraceRegistrar`|Berichte über die Registrierung von Objekten.|
|`atlTraceRefcount`|Berichte über die Änderung der Referenzanzahl.|
|`atlTraceWindowing`|Berichte zu Windows-Methoden; meldet z. B. eine ungültige Nachrichtenzuordnungs-ID.|
|`atlTraceControls`|Berichte über Kontrollen; z. B. Berichte, wenn ein Steuerelement oder sein Fenster zerstört wird.|
|`atlTraceHosting`|Berichte zum Hosten von Nachrichten; z. B. Berichte, wenn ein Client in einem Container aktiviert ist.|
|`atlTraceDBClient`|Berichte zur OLE DB Consumer Template; Wenn z. B. ein Aufruf von GetData fehlschlägt, kann die Ausgabe das HRESULT enthalten.|
|`atlTraceDBProvider`|Berichte zur OLE DB-Anbietervorlage; Z. B. Berichte, wenn die Erstellung einer Spalte fehlgeschlagen ist.|
|`atlTraceSnapin`|Berichte für MMC SnapIn-Anwendung.|
|`atlTraceNotImpl`|Meldet, dass die angegebene Funktion nicht implementiert ist.|
|`atlTraceAllocation`|Meldet Nachrichten, die von den Speicherdebuggingtools in atldbgmem.h gedruckt werden.|

### <a name="mfc-trace-flags"></a>MFC-Ablaufverfolgungsflags

|MFC-Kategorie|BESCHREIBUNG|
|------------------|-----------------|
|`traceAppMsg`|Allgemeiner Zweck, MFC-Nachrichten. Immer zu empfehlen.|
|`traceDumpContext`|Nachrichten von [CDumpContext](../../mfc/reference/cdumpcontext-class.md).|
|`traceWinMsg`|Nachrichten aus dem MFC-Nachrichtenbehandlungscode.|
|`traceMemory`|Nachrichten aus dem Speicherverwaltungscode von MFC.|
|`traceCmdRouting`|Nachrichten aus dem Windows-Befehlsroutingcode von MFC.|
|`traceHtml`|Nachrichten aus dem DHTML-Dialog von MFC unterstützen.|
|`traceSocket`|Nachrichten von der MFC-Socketunterstützung.|
|`traceOle`|Nachrichten von der OLE-Unterstützung von MFC.|
|`traceDatabase`|Nachrichten aus der MFC-Datenbankunterstützung.|
|`traceInternet`|Nachrichten aus der Internetunterstützung von MFC.|

Um eine benutzerdefinierte Ablaufverfolgungskategorie zu `CTraceCategory` deklarieren, deklarieren Sie eine globale Instanz der Klasse wie folgt:

[!code-cpp[NVC_ATL_Utilities#109](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_3.cpp)]

Der Kategoriename, MY_CATEGORY in diesem Beispiel, ist der Name, den Sie für den *Kategorieparameter* angeben. Der erste Parameter ist der Kategoriename, der im ATL/MFC-Ablaufverfolgungstool angezeigt wird. Der zweite Parameter ist die Standardablaufverfolgungsebene. Dieser Parameter ist optional, und die Standardablaufverfolgungsebene ist 0.

So verwenden Sie eine benutzerdefinierte Kategorie:

[!code-cpp[NVC_ATL_Utilities#110](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_4.cpp)]

Um anzugeben, dass Sie die Ablaufverfolgungsmeldungen filtern möchten, fügen Sie vor `#include <atlbase.h>` der Anweisung Definitionen für diese Makros in Stdafx.h ein.

Alternativ können Sie den Filter in den Präprozessordirektiven im Dialogfeld **Eigenschaftenseiten** festlegen. Klicken Sie auf die Registerkarte **Präprozessor,** und fügen Sie dann die globale in das Bearbeitungsfeld **Präprozessordefinitionen** ein.

Atlbase.h enthält Standarddefinitionen der ATLTRACE2-Makros und diese Definitionen werden verwendet, wenn Sie diese Symbole nicht definieren, bevor atlbase.h verarbeitet wird.

In Release-Builds kompiliert ATLTRACE2 in `(void) 0`.

ATLTRACE2 beschränkt den Inhalt der Zeichenfolge, die nach der Formatierung an das Dumpgerät gesendet werden soll, auf nicht mehr als 1023 Zeichen.

ATLTRACE und ATLTRACE2 haben das gleiche Verhalten, ATLTRACE ist aus Gründen der Abwärtskompatibilität enthalten.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#111](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_5.cpp)]

## <a name="see-also"></a>Siehe auch

[Makros](../../atl/reference/atl-macros.md)<br/>
[Debuggen und Fehlerberichterstattung Globale Funktionen](../../atl/reference/debugging-and-error-reporting-global-functions.md)
