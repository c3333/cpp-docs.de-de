---
title: Diagnosedienste
ms.date: 11/04/2016
helpviewer_keywords:
- diagnosi [MFC]s, diagnostic services
- diagnostic macros [MFC], list of general MFC
- services [MFC], diagnostic
- MFC, diagnostic services
- general diagnostic functions and variables [MFC]
- diagnostics [MFC], diagnostic functions and variables
- diagnostics [MFC], list of general MFC
- diagnosis [MFC], diagnostic functions and variables
- diagnosis [MFC], list of general MFC
- general diagnostic macros in MFC
- diagnostic macros [MFC]
- diagnostic services [MFC]
- object diagnostic functions in MFC
- diagnostics [MFC], diagnostic services
- diagnostic functions and variables [MFC]
ms.assetid: 8d78454f-9fae-49c2-88c9-d3fabd5393e8
ms.openlocfilehash: 8db12a73d64641a52fea3056de8ab3180c9239b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365795"
---
# <a name="diagnostic-services"></a>Diagnosedienste

Die Microsoft Foundation Class-Bibliothek bietet viele Diagnosedienste, die das Debuggen von Programmen erleichtern. Zu diesen Diagnosediensten zählen Makros und globale Funktionen, die Ihnen das Nachverfolgen der Speicherzuweisungen von Programmen, das Sichern des Inhalts von Objekten zur Laufzeit und das Ausgeben von Debugmeldungen zur Laufzeit ermöglichen. Die Makros und globalen Funktionen für Diagnosedienste sind in folgende Kategorien gruppiert:

- Allgemeine Diagnosemakros

- Allgemeine Diagnosefunktionen und -Variablen

- Objektdiagnosefunktionen

Diese Makros und Funktionen stehen in den Debug- und den endgültigen Produktversionen von MFC für alle von `CObject` abgeleiteten Klassen zur Verfügung. Alle außer DEBUG_NEW und VERIFY tun jedoch nichts in der Release-Version.

In der Debugbibliothek stehen alle zugewiesenen Speicherblöcke in aus einer Reihe von "Wächterbytes" bestehenden Klammern. Wenn diese Bytes durch einen fehlerhaften Schreibzugriff auf den Speicher gestört werden, können die Diagnoseroutinen ein Speicherproblem melden. Wenn Sie diese Zeile:

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

In Ihrer Implementierungsdatei speichern alle Aufrufe zu **new** den Dateinamen und die Zeilennummer, in der die Speicherzuweisung stattgefunden hat. Die Funktion [CMemoryState::DumpAllObjectsSince](cmemorystate-structure.md#dumpallobjectssince) zeigt diese zusätzlichen Informationen an, sodass Sie Speicherverluste identifizieren können. Weitere Informationen zur Diagnoseausgabe finden Sie auch in der Klasse [CDumpContext.](../../mfc/reference/cdumpcontext-class.md)

Darüber hinaus unterstützt die C-Laufzeitbibliothek auch eine Reihe von Diagnosefunktionen, die Sie zum Debuggen von Anwendungen verwenden können. Weitere Informationen finden Sie unter [Debugroutinen](../../c-runtime-library/debug-routines.md) in der Laufzeitbibliotheksreferenz.

### <a name="mfc-general-diagnostic-macros"></a>Allgemeine MFC-Diagnosemakros

|||
|-|-|
|[Assert](#assert)|Gibt eine Meldung aus und bricht dann das Programm ab, wenn der angegebene Ausdruck in der Debugversion der Bibliothek als FALSE ausgewertet wird.|
|[ASSERT_KINDOF](#assert_kindof)|Prüft, ob ein Objekt ein Objekt der angegebenen Klasse oder einer aus der angegebenen Klasse abgeleiteten Klasse ist.|
|[ASSERT_VALID](#assert_valid)|Prüft die interne Gültigkeit eines Objekts durch Aufrufen seiner `AssertValid` -Memberfunktion; normalerweise durch `CObject`außer Kraft gesetzt.|
|[Debug_new](#debug_new)|Gibt einen Dateinamen und eine Zeilennummer für alle Objektzuweisungen im Debugmodus an, um die Suche nach Speicherlecks zu unterstützen.|
|[DEBUG_ONLY](#debug_only)|Ähnlich wie ASSERT, prüft jedoch nicht den Wert des Ausdrucks; nützlich für Code, der nur im Debugmodus ausgeführt werden soll.|
|[ENSURE und ENSURE_VALID](#ensure)|Wird verwendet, um die Datenkorrektheit zu überprüfen.|
|[THIS_FILE](#this_file)|Erweitert auf den Namen der Datei, die kompiliert wird.|
|[Spur](#trace)|Stellt eine `printf`-ähnliche Funktionalität in der Debugversion der Bibliothek zur Verfügung.|
|[Überprüfen](#verify)|Ähnlich wie ASSERT, wertet den Ausdruck aber sowohl in der Releaseversion der Bibliothek als auch in der Debugversion aus.|

### <a name="mfc-general-diagnostic-variables-and-functions"></a>Allgemeine MFC-Diagnosevariablen und -Funktionen

|||
|-|-|
|[afxDump](#afxdump)|Globale Variable, die [CDumpContext-Informationen](../../mfc/reference/cdumpcontext-class.md) an das Debuggerausgabefenster oder an das Debugterminal sendet.|
|[afxMemDF](#afxmemdf)|Globale Variable, die das Verhalten der Debugspeicherzuweisung steuert.|
|[AfxCheckError](#afxcheckerror)|Globale Variable, die zum Prüfen des übergebenen SCODEs verwendet wird, um festzustellen, ob es sich um einen Fehler handelt; löst in diesem Fall den entsprechenden Fehler aus.|
|[AfxCheckMemory](#afxcheckmemory)|Überprüft die Integrität des gesamten derzeit zugewiesenen Speichers.|
|[AfxDebugBreak](#afxdebugbreak)|Verursacht einen Unterbrechungs-In-Ausführungs-|
|[afxDump](#cdumpcontext_in_mfc)|Sichert bei einem Aufruf im Debugger den Status eines Objekts während des Debuggens.|
|[afxDump](#afxdump)|Interne Funktion, die den Status eines Objekts während des Debuggens abgibt.|
|[AfxDumpStack](#afxdumpstack)|Generiert ein Image des aktuellen Stapels. Diese Funktion wird immer statisch gelinkt.|
|[AfxEnableMemoryLeakDump](#afxenablememoryleakdump)|Ermöglicht das Sichern von Speicherlecks.|
|[AfxEnableMemoryTracking](#afxenablememorytracking)|Aktiviert und deaktiviert die Arbeitsspeicher-Nachverfolgung.|
|[AfxIsMemoryBlock](#afxismemoryblock)|Überprüft, ob ein Speicherblock ordnungsgemäß zugewiesen wurde.|
|[AfxIsValidAddress](#afxisvalidaddress)|Überprüft, ob ein Speicheradressbereich innerhalb der Grenzen des Programms liegt.|
|[AfxIsValidString](#afxisvalidstring)|Bestimmt, ob ein Zeiger auf eine Zeichenfolge gültig ist.|
|[AfxSetAllocHook](#afxsetallochook)|Ermöglicht das Aufrufen einer Funktion für jede Speicherzuweisung.|

### <a name="mfc-object-diagnostic-functions"></a>MFC-Objektdiagnosefunktionen

|||
|-|-|
|[AfxDoForAllClasses](#afxdoforallclasses)|Führt eine angegebene Funktion für alle von `CObject`abgeleiteten Klassen aus, die Typprüfung zur Laufzeit unterstützen.|
|[AfxDoForAllObjects](#afxdoforallobjects)|Führt eine angegebene Funktion für alle von `CObject`abgeleiteten Objekte aus, die mithilfe von **new**zugewiesen wurden.|

### <a name="mfc-compilation-macros"></a>MFC-Kompilierungsmakros

|||
|-|-|
|[_AFX_SECURE_NO_WARNINGS](#afx_secure_no_warnings)|Unterdrückt Compilerwarnungen für die Verwendung veralteter MFC-Funktionen.|

## <a name="_afx_secure_no_warnings"></a><a name="afx_secure_no_warnings"></a>_AFX_SECURE_NO_WARNINGS

Unterdrückt Compilerwarnungen für die Verwendung veralteter MFC-Funktionen.

### <a name="syntax"></a>Syntax

```
_AFX_SECURE_NO_WARNINGS
```

### <a name="example"></a>Beispiel

Dieses Codebeispiel würde eine Compilerwarnung auslösen, wenn _AFX_SECURE_NO_WARNINGS nicht definiert sind.

```cpp
// define this before including any afx files in *pch.h* (*stdafx.h* in Visual Studio 2017 and earlier)
#define _AFX_SECURE_NO_WARNINGS
```

```cpp
CRichEditCtrl* pRichEdit = new CRichEditCtrl;
pRichEdit->Create(WS_CHILD|WS_VISIBLE|WS_BORDER|ES_MULTILINE,
   CRect(10,10,100,200), pParentWnd, 1);
char sz[256];
pRichEdit->GetSelText(sz);
```

## <a name="afxdebugbreak"></a><a name="afxdebugbreak"></a>AfxDebugBreak

Rufen Sie diese Funktion auf, um eine `AfxDebugBreak`Unterbrechung (am Speicherort des Aufrufs von ) bei der Ausführung der Debugversion Ihrer MFC-Anwendung zu verursachen.

### <a name="syntax"></a>Syntax

```
void AfxDebugBreak( );
```

### <a name="remarks"></a>Bemerkungen

`AfxDebugBreak`hat keine Auswirkungen in Releaseversionen einer MFC-Anwendung und sollte entfernt werden. Diese Funktion sollte nur in MFC-Anwendungen verwendet werden. Verwenden Sie die Win32-API-Version , `DebugBreak`um einen Bruch in Nicht-MFC-Anwendungen zu verursachen.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxver_.h

## <a name="assert"></a><a name="assert"></a>Assert

Bewertet sein Argument.

```
ASSERT(booleanExpression)
```

### <a name="parameters"></a>Parameter

*booleanExpression*<br/>
Gibt einen Ausdruck (einschließlich Zeigerwerte) an, der als Unwert oder Null ausgewertet wird.

### <a name="remarks"></a>Bemerkungen

Wenn das Ergebnis 0 ist, druckt das Makro eine Diagnosemeldung und bricht das Programm ab. Wenn die Bedingung ungleich Null ist, tut sie nichts.

Die Diagnosemeldung hat die Form

`assertion failed in file <name> in line <num>`

wobei *Name* der Name der Quelldatei und *num* die Zeilennummer der Assertion ist, die in der Quelldatei fehlgeschlagen ist.

In der Release-Version von MFC wertet ASSERT den Ausdruck nicht aus und unterbricht daher das Programm nicht. Wenn der Ausdruck unabhängig von der Umgebung ausgewertet werden muss, verwenden Sie das VERIFY-Makro anstelle von ASSERT.

> [!NOTE]
> Diese Funktion ist nur in der Debug-Version von MFC verfügbar.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_Utilities#44](../../mfc/codesnippet/cpp/diagnostic-services_2.cpp)]

### <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="assert_kindof"></a><a name="assert_kindof"></a>ASSERT_KINDOF

Dieses Makro bestätigt, dass das Objekt, auf das verwiesen wird, ein Objekt der angegebenen Klasse oder ein Objekt einer Klasse ist, die von der angegebenen Klasse abgeleitet wurde.

```
ASSERT_KINDOF(classname, pobject)
```

### <a name="parameters"></a>Parameter

*Classname*<br/>
Der Name `CObject`einer -derived-Klasse.

*pobject*<br/>
Ein Zeiger auf ein Klassenobjekt.

### <a name="remarks"></a>Bemerkungen

Der *pobject-Parameter* sollte ein Zeiger auf ein Objekt sein und kann **const**sein. Auf das Objekt und die `CObject` Klasse wird Die Informationen zur Laufzeitklasse unterstützen. Um beispielsweise sicherzustellen, `pDocument` dass es sich um einen `CMyDoc` Zeiger auf ein Objekt der Klasse oder eines ihrer Abgeleiteten handelt, können Sie wie aus den folgenden Punkten kodieren:

[!code-cpp[NVC_MFCDocView#194](../../mfc/codesnippet/cpp/diagnostic-services_3.cpp)]

Die `ASSERT_KINDOF` Verwendung des Makros ist genau das gleiche wie die Codierung:

[!code-cpp[NVC_MFCDocView#195](../../mfc/codesnippet/cpp/diagnostic-services_4.cpp)]

Diese Funktion funktioniert nur für Klassen, die mit dem Makro [DECLARE_DYNAMIC] deklariert sind(run-time-object-model-services.md-declare_dynamic oder [DECLARE_SERIAL.](run-time-object-model-services.md#declare_serial)

> [!NOTE]
> Diese Funktion ist nur in der Debug-Version von MFC verfügbar.

### <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="assert_valid"></a><a name="assert_valid"></a>ASSERT_VALID

Verwenden Sie diese Form, um Ihre Annahmen über die Gültigkeit des internen Zustands eines Objekts zu testen.

```
ASSERT_VALID(pObject)
```

### <a name="parameters"></a>Parameter

*pObject*<br/>
Gibt ein Objekt einer Von `CObject` einer Klasse abgeleiteten `AssertValid` Klasse an, die über eine übergeordnete Version der Memberfunktion verfügt.

### <a name="remarks"></a>Bemerkungen

ASSERT_VALID ruft `AssertValid` die Memberfunktion des Objekts auf, das als Argument übergeben wird.

In der Release-Version von MFC führt ASSERT_VALID nichts aus. In der Debugversion überprüft sie den Zeiger, überprüft NULL und ruft `AssertValid` die eigenen Memberfunktionen des Objekts auf. Wenn einer dieser Tests fehlschlägt, wird eine Warnmeldung auf die gleiche Weise wie [ASSERT](#assert)angezeigt.

> [!NOTE]
> Diese Funktion ist nur in der Debug-Version von MFC verfügbar.

Weitere Informationen und Beispiele finden Sie unter [Debuggen von MFC-Anwendungen](/visualstudio/debugger/mfc-debugging-techniques).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCObjectSample#19](../../mfc/codesnippet/cpp/diagnostic-services_5.cpp)]

### <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="debug_new"></a><a name="debug_new"></a>Debug_new

Hilft bei der Suche nach Speicherverlusten.

```
#define  new DEBUG_NEW
```

### <a name="remarks"></a>Bemerkungen

Sie können DEBUG_NEW überall in Ihrem Programm verwenden, die Sie normalerweise **verwenden** würden, um Heapspeicher zuzuweisen.

Im Debugmodus (wenn das **_DEBUG-Symbol** definiert ist) verfolgt DEBUG_NEW den Dateinamen und die Zeilennummer für jedes Objekt, das es zuweist. Wenn Sie dann die Memberfunktion [CMemoryState::DumpAllObjectsSince](cmemorystate-structure.md#dumpallobjectssince) verwenden, wird jedes mit DEBUG_NEW zugewiesene Objekt mit dem Dateinamen und der Zeilennummer angezeigt, an der es zugewiesen wurde.

Um DEBUG_NEW zu verwenden, fügen Sie die folgende Direktive in ihre Quelldateien ein:

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

Sobald Sie diese Direktive eingefügt haben, fügt der Präprozessor DEBUG_NEW ein, wo immer Sie **neue**verwenden, und MFC übernimmt den Rest. Wenn Sie eine Releaseversion Ihres Programms kompilieren, löst DEBUG_NEW einen einfachen **neuen** Vorgang auf, und die Dateinamen- und Zeilennummerninformationen werden nicht generiert.

> [!NOTE]
> In früheren Versionen von MFC (4.1 und `#define` früher) mussten Sie die Anweisung nach allen Anweisungen setzen, die den IMPLEMENT_DYNCREATE oder IMPLEMENT_SERIAL Makros aufgerufen haben. Dies ist nicht mehr erforderlich.

### <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="debug_only"></a><a name="debug_only"></a>DEBUG_ONLY

Im Debugmodus (wenn das **_DEBUG-Symbol** definiert wird), wertet DEBUG_ONLY sein Argument aus.

```
DEBUG_ONLY(expression)
```

### <a name="remarks"></a>Bemerkungen

In einem Releasebuild bewertet DEBUG_ONLY sein Argument nicht. Dies ist nützlich, wenn Sie Code haben, der nur in Debugbuilds ausgeführt werden soll.

Das DEBUG_ONLY Makro entspricht dem `#ifdef _DEBUG` `#endif`umgebenden *Ausdruck* mit und .

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_Utilities#32](../../mfc/codesnippet/cpp/diagnostic-services_6.cpp)]

### <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

### <a name="ensure-and-ensure_valid"></a><a name="ensure"></a>ENSURE und ENSURE_VALID

Wird verwendet, um die Datenkorrektheit zu überprüfen.

### <a name="syntax"></a>Syntax

```
ENSURE(  booleanExpression )
ENSURE_VALID( booleanExpression  )
```

### <a name="parameters"></a>Parameter

*booleanExpression*<br/>
Gibt einen booleschen Ausdruck an, der getestet werden soll.

### <a name="remarks"></a>Bemerkungen

Der Zweck dieser Makros ist es, die Validierung von Parametern zu verbessern. Die Makros verhindern die weitere Verarbeitung falscher Parameter im Code. Im Gegensatz zu den ASSERT-Makros werfen die ENSURE-Makros zusätzlich zum Generieren einer Assertion eine Ausnahme aus.

Die Makros verhalten sich je nach Projektkonfiguration auf zwei Arten. Die Makros rufen ASSERT auf und rufen dann eine Ausnahme aus, wenn die Assertion fehlschlägt. Daher erzeugen die Makros in Debugkonfigurationen (d. h. wo _DEBUG definiert ist) eine Assertion und eine Ausnahme, während die Makros in Releasekonfigurationen nur die Ausnahme erzeugen (ASSERT wertet den Ausdruck in Release-Konfigurationen nicht aus).

Das Makro ENSURE_ARG wirkt wie das ENSURE-Makro.

ENSURE_VALID ruft das ASSERT_VALID Makro auf (das sich nur in Debugbuilds auswirkt). Außerdem löst ENSURE_VALID eine Ausnahme aus, wenn der Zeiger NULL ist. Der NULL-Test wird sowohl in Debug- als auch in Release-Konfigurationen durchgeführt.

Wenn einer dieser Tests fehlschlägt, wird eine Warnmeldung auf die gleiche Weise wie ASSERT angezeigt. Das Makro löst bei Bedarf eine ungültige Argumentausnahme aus.

### <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="this_file"></a><a name="this_file"></a>THIS_FILE

Erweitert auf den Namen der Datei, die kompiliert wird.

### <a name="syntax"></a>Syntax

```
THIS_FILE
```

### <a name="remarks"></a>Bemerkungen

Die Informationen werden von den Makros ASSERT und VERIFY verwendet. Der Anwendungs-Assistent und die Code-Assistenten platzieren das Makro in den von ihnen erstellten Quellcodedateien.

### <a name="example"></a>Beispiel

```cpp
#ifdef _DEBUG
#undef THIS_FILE
static char THIS_FILE[] = __FILE__;
#endif

// __FILE__ is one of the six predefined ANSI C macros that the
// compiler recognizes.
```

### <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="trace"></a><a name="trace"></a>Spur

Sendet die angegebene Zeichenfolge an den Debugger der aktuellen Anwendung.

```
TRACE(exp)
TRACE(DWORD  category,  UINT  level, LPCSTR lpszFormat, ...)
```

### <a name="remarks"></a>Bemerkungen

Eine Beschreibung von TRACE finden Sie unter [ATLTRACE2.](../../atl/reference/debugging-and-error-reporting-macros.md#atltrace2) TRACE und ATLTRACE2 haben das gleiche Verhalten.

In der Debugversion von MFC sendet dieses Makro die angegebene Zeichenfolge an den Debugger der aktuellen Anwendung. In einem Release-Build wird dieses Makro zu nichts kompiliert (es wird überhaupt kein Code generiert).

Weitere Informationen finden Sie unter [Debuggen von MFC-Anwendungen](/visualstudio/debugger/mfc-debugging-techniques).

### <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="verify"></a><a name="verify"></a>Überprüfen

In der Debug-Version von MFC wird sein Argument ausgewertet.

```
VERIFY(booleanExpression)
```

### <a name="parameters"></a>Parameter

*booleanExpression*<br/>
Gibt einen Ausdruck (einschließlich Zeigerwerte) an, der als Unwert oder Null ausgewertet wird.

### <a name="remarks"></a>Bemerkungen

Wenn das Ergebnis 0 ist, druckt das Makro eine Diagnosemeldung und hält das Programm an. Wenn die Bedingung ungleich Null ist, tut sie nichts.

Die Diagnosemeldung hat die Form

`assertion failed in file <name> in line <num>`

wobei *Name* der Name der Quelldatei und *num* die Zeilennummer der Assertion ist, die in der Quelldatei fehlgeschlagen ist.

In der Release-Version von MFC wertet VERIFY den Ausdruck aus, druckt oder unterbricht das Programm jedoch nicht. Wenn es sich bei dem Ausdruck beispielsweise um einen Funktionsaufruf handelt, wird der Aufruf durchgeführt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#198](../../mfc/codesnippet/cpp/diagnostic-services_7.cpp)]

### <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="afxdump-cdumpcontext-in-mfc"></a><a name="cdumpcontext_in_mfc"></a>afxDump (CDumpContext in MFC)

Stellt grundlegende Objekt-Dumping-Funktionen in Ihrer Anwendung bereit.

```
CDumpContext  afxDump;
```

### <a name="remarks"></a>Bemerkungen

`afxDump`ist ein vordefiniertes [CDumpContext-Objekt,](../../mfc/reference/cdumpcontext-class.md) mit dem Sie Informationen an das Debuggerausgabefenster oder an ein Debugterminal senden `CDumpContext` können. In der `afxDump` Regel geben `CObject::Dump`Sie als Parameter an .

Unter Windows NT und allen `afxDump` Versionen von Windows wird die Ausgabe an das Ausgabe-Debug-Fenster von Visual C++ gesendet, wenn Sie Ihre Anwendung debuggen.

Diese Variable wird nur in der Debugversion von MFC definiert. Weitere Informationen `afxDump`zu finden Sie unter [Debuggen von MFC-Anwendungen](/visualstudio/debugger/mfc-debugging-techniques).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_Utilities#23](../../mfc/codesnippet/cpp/diagnostic-services_8.cpp)]

### <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="afxdump-internal"></a><a name="afxdump"></a>AfxDump (Intern)

Interne Funktion, die MFC verwendet, um den Status eines Objekts während des Debuggens zu verwerfen.

### <a name="syntax"></a>Syntax

```
void AfxDump(const CObject* pOb);
```

### <a name="parameters"></a>Parameter

*Pob*<br/>
Ein Zeiger auf ein Objekt einer `CObject`Klasse, die von abgeleitet wurde.

### <a name="remarks"></a>Bemerkungen

`AfxDump`ruft die Memberfunktion eines Objekts `Dump` auf und sendet `afxDump` die Informationen an den von der Variablen angegebenen Speicherort. `AfxDump`ist nur in der Debug-Version von MFC verfügbar.

Ihr Programmcode sollte `AfxDump`nicht aufrufen, `Dump` sondern stattdessen die Memberfunktion des entsprechenden Objekts aufrufen.

### <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="afxmemdf"></a><a name="afxmemdf"></a>afxMemDF

Auf diese Variable kann über einen Debugger oder Ihr Programm zugegriffen werden und Sie können die Zuweisungsdiagnose optimieren.

```
int  afxMemDF;
```

### <a name="remarks"></a>Bemerkungen

`afxMemDF`kann die folgenden Werte aufweisen, die `afxMemDF`durch die Enumeration angegeben werden:

- `allocMemDF`Aktiviert das Debuggen des Allokators (Standardeinstellung in der Debugbibliothek).

- `delayFreeMemDF`Verzögert die Freigabe des Speichers. Während das Programm einen Speicherblock freigibt, gibt der Zuweisungsspeicher diesen Speicher nicht an das zugrunde liegende Betriebssystem zurück. Dadurch wird Ihr Programm maximal belastet.

- `checkAlwaysMemDF`Ruft `AfxCheckMemory` jedes Mal auf, wenn Speicher zugewiesen oder freigegeben wird. Dies wird die Speicherzuweisungen und Deallocations erheblich verlangsamen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_Utilities#30](../../mfc/codesnippet/cpp/diagnostic-services_9.cpp)]

### <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="afxcheckerror"></a><a name="afxcheckerror"></a>AfxCheckError

Diese Funktion testet den übergebenen SCODE, um festzustellen, ob es sich um einen Fehler handelt.

```
void AFXAPI AfxCheckError(SCODE sc);
throw CMemoryException*
throw COleException*
```

### <a name="remarks"></a>Bemerkungen

Wenn es sich um einen Fehler handelt, löst die Funktion eine Ausnahme aus. Wenn der übergebene SCODE E_OUTOFMEMORY ist, löst die Funktion eine [CMemoryException](../../mfc/reference/cmemoryexception-class.md) aus, indem [AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception)aufgerufen wird. Andernfalls löst die Funktion eine [COleException](../../mfc/reference/coleexception-class.md) aus, indem [afxThrowOleException](exception-processing.md#afxthrowoleexception)aufgerufen wird.

Diese Funktion kann verwendet werden, um die Rückgabewerte von Aufrufen von OLE-Funktionen in Ihrer Anwendung zu überprüfen. Durch Das Testen des Rückgabewerts mit dieser Funktion in Ihrer Anwendung können Sie mit einer minimalen Menge an Code richtig auf Fehlerbedingungen reagieren.

> [!NOTE]
> Diese Funktion hat den gleichen Effekt in Debug- und Nicht-Debug-Builds.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#33](../../mfc/codesnippet/cpp/diagnostic-services_10.cpp)]

### <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="afxcheckmemory"></a><a name="afxcheckmemory"></a>AfxCheckMemory

Diese Funktion überprüft den freien Speicherpool und druckt bei Bedarf Fehlermeldungen.

```
BOOL  AfxCheckMemory();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn keine Speicherfehler auftreten; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Wenn die Funktion keine Speicherbeschädigung erkennt, wird nichts gedruckt.

Alle Speicherblöcke, die derzeit auf dem Heap zugewiesen sind, werden überprüft, einschließlich der Speicherblöcke, die von **neuen,** aber nicht von direkten Aufrufen an zugrunde liegende Speicherzuweisungen, wie die **malloc-Funktion** oder die Windows-Funktion, `GlobalAlloc` zugewiesen wurden. Wenn ein Block beschädigt ist, wird eine Nachricht an die Debuggerausgabe gedruckt.

Wenn Sie die Zeile

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

in einem Programmmodul, dann `AfxCheckMemory` nachfolgende Aufrufe, um den Dateinamen und die Zeilennummer anzuzeigen, an der der Speicher zugewiesen wurde.

> [!NOTE]
> Wenn Ihr Modul eine oder mehrere Implementierungen serialisierbarer `#define` Klassen enthält, müssen Sie die Zeile nach dem letzten IMPLEMENT_SERIAL-Makroaufrufs setzen.

Diese Funktion funktioniert nur in der Debug-Version von MFC.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCObjectSample#26](../../mfc/codesnippet/cpp/diagnostic-services_11.cpp)]

### <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="afxdump-mfc"></a><a name="afxdump"></a>AfxDump (MFC)

Rufen Sie diese Funktion auf, während Sie sich im Debugger befinden, um den Status eines Objekts während des Debuggens zu verwerfen.

```
void AfxDump(const CObject* pOb);
```

### <a name="parameters"></a>Parameter

*Pob*<br/>
Ein Zeiger auf ein Objekt einer `CObject`Klasse, die von abgeleitet wurde.

### <a name="remarks"></a>Bemerkungen

`AfxDump`ruft die Memberfunktion eines Objekts `Dump` auf und sendet `afxDump` die Informationen an den von der Variablen angegebenen Speicherort. `AfxDump`ist nur in der Debug-Version von MFC verfügbar.

Ihr Programmcode sollte `AfxDump`nicht aufrufen, `Dump` sondern stattdessen die Memberfunktion des entsprechenden Objekts aufrufen.

### <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="afxdumpstack"></a><a name="afxdumpstack"></a>AfxDumpStack

Diese globale Funktion kann verwendet werden, um ein Abbild des aktuellen Stapels zu generieren.

```
void AFXAPI AfxDumpStack(DWORD dwTarget = AFX_STACK_DUMP_TARGET_DEFAULT);
```

### <a name="parameters"></a>Parameter

*dwTarget*<br/>
Gibt das Ziel der Dump-Ausgabe an. Mögliche Werte, die mit dem Operator bitwise-OR ( **&#124;**) kombiniert werden können, sind:

- AFX_STACK_DUMP_TARGET_TRACE Sendet die Ausgabe [TRACE](#trace) über das TRACE-Makro. Das TRACE-Makro generiert nur die Ausgabe in Debugbuilds. es generiert keine Ausgabe in Release-Builds. Außerdem kann TRACE auf andere Ziele neben dem Debugger umgeleitet werden.

- AFX_STACK_DUMP_TARGET_DEFAULT Sendet die Dumpausgabe an das Standardziel. Bei einem Debugbuild wird die Ausgabe an das TRACE-Makro ausgegeben. In einem Release-Build wird die Ausgabe an die Zwischenablage ausgegeben.

- AFX_STACK_DUMP_TARGET_CLIPBOARD Sendet die Ausgabe nur an die Zwischenablage. Die Daten werden in der Zwischenablage als Nur-Text im Format CF_TEXT Zwischenablage abgelegt.

- AFX_STACK_DUMP_TARGET_BOTH Sendet die Ausgabe gleichzeitig an die Zwischenablage und an das TRACE-Makro.

- AFX_STACK_DUMP_TARGET_ODS Sendet die Ausgabe direkt über die Win32-Funktion `OutputDebugString()`an den Debugger . Diese Option generiert die Debuggerausgabe sowohl in Debug- als auch in Releasebuilds, wenn ein Debugger an den Prozess angefügt wird. AFX_STACK_DUMP_TARGET_ODS erreicht immer den Debugger (wenn er angefügt ist) und kann nicht umgeleitet werden.

### <a name="remarks"></a>Bemerkungen

Das folgende Beispiel zeigt eine einzelne Zeile `AfxDumpStack` der Ausgabe, die durch Aufrufen von einem Schaltflächenhandler in einer MFC-Dialoganwendung generiert wird:

```Output
=== begin AfxDumpStack output ===
00427D55: DUMP2\DEBUG\DUMP2.EXE! void AfxDumpStack(unsigned long) + 181 bytes
0040160B: DUMP2\DEBUG\DUMP2.EXE! void CDump2Dlg::OnClipboard(void) + 14 bytes
0044F884: DUMP2\DEBUG\DUMP2.EXE! int _AfxDispatchCmdMsg(class CCmdTarget *,
unsigned int,int,void ( CCmdTarget::*)(void),void *,unsigned int,struct
AFX_CMDHANDLE
0044FF7B: DUMP2\DEBUG\DUMP2.EXE! virtual int CCmdTarget::OnCmdMsg(unsigned
int,int,void *,struct AFX_CMDHANDLERINFO *) + 626 bytes
00450C71: DUMP2\DEBUG\DUMP2.EXE! virtual int CDialog::OnCmdMsg(unsigned
int,int,void *,struct AFX_CMDHANDLERINFO *) + 36 bytes
00455B27: DUMP2\DEBUG\DUMP2.EXE! virtual int CWnd::OnCommand(unsigned
int,long) + 312 bytes
00454D3D: DUMP2\DEBUG\DUMP2.EXE! virtual int CWnd::OnWndMsg(unsigned
int,unsigned int,long,long *) + 83 bytes
00454CC0: DUMP2\DEBUG\DUMP2.EXE! virtual long CWnd::WindowProc(unsigned
int,unsigned int,long) + 46 bytes
004528D9: DUMP2\DEBUG\DUMP2.EXE! long AfxCallWndProc(class CWnd *,struct
HWND__ *,unsigned int,unsigned int,long) + 237 bytes
00452D34: DUMP2\DEBUG\DUMP2.EXE! long AfxWndProc(struct HWND__ *,unsigned
int,unsigned int,long) + 129 bytes
BFF73663: WINDOWS\SYSTEM\KERNEL32.DLL! ThunkConnect32 + 2148 bytes
BFF928E0: WINDOWS\SYSTEM\KERNEL32.DLL! UTUnRegister + 2492 bytes
=== end AfxDumpStack() output ===
```

Jede Zeile in der Ausgabe oben gibt die Adresse des letzten Funktionsaufrufs, den vollständigen Pfadnamen des Moduls, das den Funktionsaufruf enthält, und den aufgerufenen Funktionsprototyp an. Wenn der Funktionsaufruf auf dem Stack nicht an der genauen Adresse der Funktion erfolgt, wird ein Satz von Bytes angezeigt.

Die folgende Tabelle beschreibt z. B. die erste Zeile der obigen Ausgabe:

|Output|BESCHREIBUNG|
|------------|-----------------|
|`00427D55:`|Die Rückgabeadresse des letzten Funktionsaufrufs.|
|`DUMP2\DEBUG\DUMP2.EXE!`|Der vollständige Pfadname des Moduls, das den Funktionsaufruf enthält.|
|`void AfxDumpStack(unsigned long)`|Der aufgerufene Funktionsprototyp.|
|`+ 181 bytes`|Der Offset in Bytes von der Adresse des `void AfxDumpStack(unsigned long)`Funktionsprototyps (in diesem Fall `00427D55`) bis zur Rückgabeadresse (in diesem Fall ).|

`AfxDumpStack`ist in Debug- und Nichtdebug-Versionen der MFC-Bibliotheken verfügbar; Die Funktion ist jedoch immer statisch verknüpft, auch wenn Ihre ausführbare Datei MFC in einer freigegebenen DLL verwendet. In Shared-Library-Implementierungen befindet sich die Funktion im MFCS42. LIB-Bibliothek (und ihre Varianten).

So verwenden Sie diese Funktion erfolgreich:

- Die Datei IMAGEHLP. DLL muss sich auf Ihrem Pfad befinden. Wenn Sie nicht über diese DLL verfügen, wird in der Funktion eine Fehlermeldung angezeigt. Informationen zum von IMAGEHLP bereitgestellten Funktionssatz finden Sie unter [Bildhilfebibliothek.](/windows/win32/Debug/image-help-library)

- Die Module, die Frames auf dem Stapel haben, müssen Debuginformationen enthalten. Wenn sie keine Debuginformationen enthalten, generiert die Funktion weiterhin eine Stapelablaufverfolgung, aber die Ablaufverfolgung wird weniger detailliert.

### <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="afxenablememoryleakdump"></a><a name="afxenablememoryleakdump"></a>AfxEnableMemoryLeakDump

Aktiviert und deaktiviert die Speicherverlustableitung im AFX_DEBUG_STATE Destruktor.

```
BOOL AFXAPI AfxEnableMemoryLeakDump(BOOL bDump);
```

### <a name="parameters"></a>Parameter

*bDump*<br/>
[in] TRUE gibt an, dass der Speicherverlustdump aktiviert ist. FALSE gibt an, dass der Speicherverlustdump deaktiviert ist.

### <a name="return-value"></a>Rückgabewert

Der vorherige Wert für dieses Flag.

### <a name="remarks"></a>Bemerkungen

Wenn eine Anwendung die MFC-Bibliothek entlädt, führt die MFC-Bibliothek eine Überprüfung auf Speicherverluste aus. Zu diesem Zeitpunkt werden alle Speicherverluste über das **Debugfenster** von Visual Studio an den Benutzer gemeldet.

Wenn Ihre Anwendung eine andere Bibliothek vor der MFC-Bibliothek lädt, werden einige Speicherbelegungen in dieser Bibliothek fälschlicherweise als Arbeitsspeicherverluste gemeldet. Wegen Arbeitsspeicherverlusten, die eigentlich keine sind, wird Ihre Anwendung möglicherweise langsam beendet, da die MFC-Bibliothek die Speicherverluste meldet. Verwenden Sie in diesem Fall `AfxEnableMemoryLeakDump` , um das Speicherabbild des Arbeitsspeicherverlusts zu deaktivieren.

> [!NOTE]
> Wenn Sie diese Methode verwenden, um das Speicherabbild des Arbeitsspeicherverlusts deaktivieren, erhalten Sie keine Berichte über tatsächliche Arbeitsspeicherverluste in Ihrer Anwendung. Sie sollten diese Methode nur verwenden, wenn Sie sicher sind, dass der Bericht über die Arbeitsspeicherverluste falsche Meldungen enthält.

### <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="afxenablememorytracking"></a><a name="afxenablememorytracking"></a>AfxEnableMemoryTracking

Die Diagnosespeicherverfolgung ist normalerweise in der Debugversion von MFC aktiviert.

```
BOOL AfxEnableMemoryTracking(BOOL bTrack);
```

### <a name="parameters"></a>Parameter

*bTrack*<br/>
Wenn Sie diesen Wert auf TRUE setzen, wird die Speicherverfolgung aktiviert. FALSE schaltet es aus.

### <a name="return-value"></a>Rückgabewert

Die vorherige Einstellung des Tracking-Enable-Flags.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Funktion, um die Nachverfolgung von Abschnitten des Codes zu deaktivieren, von denen Sie wissen, dass sie Blöcke korrekt zuordnen.

Weitere Informationen `AfxEnableMemoryTracking`zu finden Sie unter [Debuggen von MFC-Anwendungen](/visualstudio/debugger/mfc-debugging-techniques).

> [!NOTE]
> Diese Funktion funktioniert nur in der Debug-Version von MFC.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_Utilities#24](../../mfc/codesnippet/cpp/diagnostic-services_12.cpp)]

### <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="afxismemoryblock"></a><a name="afxismemoryblock"></a>AfxIsMemoryBlock

Testet eine Speicheradresse, um sicherzustellen, dass sie einen derzeit aktiven Speicherblock darstellt, der von der Diagnoseversion von **new**zugewiesen wurde.

```
BOOL AfxIsMemoryBlock(
    const void* p,
    UINT nBytes,
    LONG* plRequestNumber = NULL);
```

### <a name="parameters"></a>Parameter

*P*<br/>
Zeigt auf den zu testenden Speicherblock.

*nBytes*<br/>
Enthält die Länge des Speicherblocks in Bytes.

*plRequestNumber*<br/>
Zeigt auf eine **lange** ganze Zahl, die mit der Zuweisungssequenznummer des Speicherblocks ausgefüllt wird, oder Null, wenn sie keinen derzeit aktiven Speicherblock darstellt.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Speicherblock derzeit zugewiesen ist und die Länge korrekt ist; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Außerdem wird die angegebene Größe mit der ursprünglichen zugewiesenen Größe überprüft. Wenn die Funktion einen Wert ungleich Null zurückgibt, wird die Zuordnungssequenznummer in *plRequestNumber*zurückgegeben. Diese Zahl stellt die Reihenfolge dar, in der der Block relativ zu allen anderen **neuen** Zuordnungen zugeordnet wurde.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_Utilities#27](../../mfc/codesnippet/cpp/diagnostic-services_13.cpp)]

### <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="afxisvalidaddress"></a><a name="afxisvalidaddress"></a>AfxIsValidAddress

Testet jede Speicheradresse, um sicherzustellen, dass sie vollständig im Speicherbereich des Programms enthalten ist.

```
BOOL AfxIsValidAddress(
    const void* lp,
    UINT nBytes,
    BOOL bReadWrite = TRUE);
```

### <a name="parameters"></a>Parameter

*Lp*<br/>
Zeigt auf die zu testende Speicheradresse.

*nBytes*<br/>
Enthält die Anzahl der zu testenden Bytes an Arbeitsspeicher.

*bReadWrite*<br/>
Gibt an, ob der Speicher sowohl zum Lesen und Schreiben (TRUE) als auch nur zum Lesen (FALSE) dient.

### <a name="return-value"></a>Rückgabewert

In Debugbuilds ein Wert ungleich Null, wenn der angegebene Speicherblock vollständig im Speicherbereich des Programms enthalten ist. andernfalls 0.

In Nicht-Debug-Builds ein Wert ungleich Null, wenn *lp* nicht NULL ist; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die Adresse ist nicht auf Blöcke beschränkt, die von **new**zugewiesen wurden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_Utilities#28](../../mfc/codesnippet/cpp/diagnostic-services_14.cpp)]

### <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="afxisvalidstring"></a><a name="afxisvalidstring"></a>AfxIsValidString

Verwenden Sie diese Funktion, um zu bestimmen, ob ein Zeiger auf eine Zeichenfolge gültig ist.

```
BOOL  AfxIsValidString(
    LPCSTR lpsz,
    int nLength = -1);
```

### <a name="parameters"></a>Parameter

*lpsz*<br/>
Der zu testende Zeiger.

*nLänge*<br/>
Gibt die Länge der zu testenden Zeichenfolge in Bytes an. Der Wert -1 gibt an, dass die Zeichenfolge null-beendet wird.

### <a name="return-value"></a>Rückgabewert

In Debugbuilds ein Wert ungleich Null, wenn der angegebene Zeiger auf eine Zeichenfolge der angegebenen Größe zeigt. andernfalls 0.

In Nicht-Debug-Builds ein Wert ungleich Null, wenn *lpsz* nicht NULL ist; andernfalls 0.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_Utilities#29](../../mfc/codesnippet/cpp/diagnostic-services_15.cpp)]

### <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="afxsetallochook"></a><a name="afxsetallochook"></a>AfxSetAllocHook

Legt einen Hook fest, der das Aufrufen der angegebenen Funktion ermöglicht, bevor jeder Speicherblock zugewiesen wird.

```
AFX_ALLOC_HOOK AfxSetAllocHook(AFX_ALLOC_HOOK pfnAllocHook);
```

### <a name="parameters"></a>Parameter

*pfnAllocHook*<br/>
Gibt den Namen der aufzurufenden Funktion an. Siehe Hinweise zum Prototyp einer Zuweisungsfunktion.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn Sie die Zuordnung zulassen möchten; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Der Debugspeicherzuweisungszuweisungsgeber der Microsoft Foundation-Klassenbibliothek kann eine benutzerdefinierte Hook-Funktion aufrufen, damit der Benutzer eine Speicherzuweisung überwachen und steuern kann, ob die Zuweisung zulässig ist. Zuweisungs-Hook-Funktionen werden wie folgt prototypiert:

**BOOL AFXAPI AllocHook( size_t** `nSize` **, BOOL** `bObject` **, LONG** `lRequestNumber` **);**

*nGröße*<br/>
Die Größe der vorgeschlagenen Speicherzuweisung.

*bObject*<br/>
TRUE, wenn die `CObject`Zuordnung für ein -derived-Objekt gilt; andernfalls FALSE.

*lRequestNumber*<br/>
Die Sequenznummer der Speicherzuordnung.

Beachten Sie, dass die AFXAPI-Aufrufkonvention impliziert, dass der Angerufene die Parameter aus dem Stapel entfernen muss.

### <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="afxdoforallclasses"></a><a name="afxdoforallclasses"></a>AfxDoForAllClasses

Ruft die angegebene Iterationsfunktion `CObject`für alle serialisierbaren -abgeleiteten Klassen im Speicherbereich der Anwendung auf.

```
void
AFXAPI AfxDoForAllClasses(
    void (* pfn)(const CRuntimeClass* pClass, void* pContext),
    void* pContext);
```

### <a name="parameters"></a>Parameter

*pfn*<br/>
Verweist auf eine Iterationsfunktion, die für jede Klasse aufgerufen werden soll. Die Funktionsargumente sind ein `CRuntimeClass` Zeiger auf ein Objekt und ein Leererzeiger auf zusätzliche Daten, die der Aufrufer für die Funktion bereitstellt.

*pContext*<br/>
Verweist auf optionale Daten, die der Aufrufer an die Iterationsfunktion liefern kann. Dieser Zeiger kann NULL sein.

### <a name="remarks"></a>Bemerkungen

Serialisierbare -abgeleitete `CObject`Klassen sind Klassen, die mit dem DECLARE_SERIAL-Makro abgeleitet werden. Der Zeiger, an `AfxDoForAllClasses` den in *pContext* übergeben wird, wird bei jedem Aufruf an die angegebene Iterationsfunktion übergeben.

> [!NOTE]
> Diese Funktion funktioniert nur in der Debug-Version von MFC.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#113](../../mfc/codesnippet/cpp/diagnostic-services_16.cpp)]

[!code-cpp[NVC_MFCCollections#114](../../mfc/codesnippet/cpp/diagnostic-services_17.cpp)]

### <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="afxdoforallobjects"></a><a name="afxdoforallobjects"></a>AfxDoForAllObjects

Führt die angegebene Iterationsfunktion für `CObject` alle Objekte aus, die von denen abgeleitet wurden, die mit **neuen**zugeordnet wurden.

```
void AfxDoForAllObjects(
    void (* pfn)(CObject* pObject, void* pContext),
    void* pContext);
```

### <a name="parameters"></a>Parameter

*pfn*<br/>
Zeigt auf eine Iterationsfunktion, die für jedes Objekt ausgeführt werden soll. Die Funktionsargumente sind ein `CObject` Zeiger auf einen und ein ungültiger Zeiger auf zusätzliche Daten, die der Aufrufer an die Funktion bereitstellt.

*pContext*<br/>
Verweist auf optionale Daten, die der Aufrufer an die Iterationsfunktion liefern kann. Dieser Zeiger kann NULL sein.

### <a name="remarks"></a>Bemerkungen

Stapel-, globale oder eingebettete Objekte werden nicht aufgezählt. Der Zeiger, `AfxDoForAllObjects` an den in *pContext* übergeben wird, wird bei jedem Aufruf an die angegebene Iterationsfunktion übergeben.

> [!NOTE]
> Diese Funktion funktioniert nur in der Debug-Version von MFC.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#115](../../mfc/codesnippet/cpp/diagnostic-services_18.cpp)]

[!code-cpp[NVC_MFCCollections#116](../../mfc/codesnippet/cpp/diagnostic-services_19.cpp)]

## <a name="see-also"></a>Siehe auch

[MFC-Makros, globale Funktionen und globale Variablen](mfc-macros-and-globals.md)<br/>
[CObject::Dump](cobject-class.md#dump)
