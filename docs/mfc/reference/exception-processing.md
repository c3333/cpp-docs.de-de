---
title: Ausnahmeverarbeitung
ms.date: 11/04/2016
helpviewer_keywords:
- macros [MFC], exception handling
- DAO (Data Access Objects), exceptions [MFC]
- OLE exceptions [MFC], MFC functions
- exceptions [MFC], processing
- exception macros [MFC]
- termination functions, MFC
- MFC, exceptions
- exceptions [MFC], MFC throwing functions
ms.assetid: 26d4457c-8350-48f5-916e-78f919787c30
ms.openlocfilehash: bdf9dee88c29621bdc77c83d2633d93b4b9d10a7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751610"
---
# <a name="exception-processing"></a>Ausnahmeverarbeitung

Wenn ein Programm ausgeführt wird, kann es zu einer Reihe ungewöhnlicher Bedingungen und Fehler kommen, die als "Ausnahmen" bezeichnet werden. Dazu gehören das Auslaufen des Arbeitsspeichers, Ressourcenzuordnungsfehler und das Nichtermitteln von Dateien.

Die Microsoft Foundation-Klassenbibliothek verwendet ein Ausnahmebehandlungsschema, das eng an dem vom ANSI-Standardsausschuss für C++ vorgeschlagenen Modell modelliert ist. Vor dem Aufrufen einer Funktion, die auf eine ungewöhnliche Situation stoßen kann, muss ein Ausnahmehandler eingerichtet werden. Wenn die Funktion auf eine abnormale Bedingung stößt, löst sie eine Ausnahme aus, und das Steuerelement wird an den Ausnahmehandler übergeben.

Mehrere Makros, die in der Microsoft Foundation-Klassenbibliothek enthalten sind, richten Ausnahmehandler ein. Eine Reihe anderer globaler Funktionen helfen, spezielle Ausnahmen auszulösen und Programme bei Bedarf zu beenden. Diese Makros und globalen Funktionen fallen in die folgenden Kategorien:

- Ausnahmemakros, die den Ausnahmehandler strukturieren.

- Exception-Throwing-Funktionen), die Ausnahmen bestimmter Typen generieren.

- Beendigungsfunktionen, die zur Beendigung des Programms führen.

Beispiele und weitere Details finden Sie im Artikel [Ausnahmen](../../mfc/exception-handling-in-mfc.md).

### <a name="exception-macros"></a>Ausnahmemakros

|||
|-|-|
|[TRY](#try)|Bezeichnet einen Codeblock für die Ausnahmeverarbeitung.|
|[Fangen](#catch)|Bezeichnet einen Codeblock zum Abfangen einer **TRY** Ausnahme vom vorherigen TRY-Block.|
|[CATCH_ALL](#catch_all)|Bezeichnet einen Codeblock zum Abfangen aller **TRY** Ausnahmen aus dem vorherigen TRY-Block.|
|[AND_CATCH](#and_catch)|Legt einen Codeblock zum Abfangen zusätzlicher Ausnahmetypen aus dem vorherigen **TRY-Block** fest.|
|[AND_CATCH_ALL](#and_catch_all)|Legt einen Codeblock zum Abfangen aller anderen zusätzlichen Ausnahmetypen fest, die in einem vorherigen **TRY-Block** ausgelöst wurden.|
|[END_CATCH](#end_catch)|Beendet den letzten **CATCH-** oder AND_CATCH-Codeblock. **AND_CATCH**|
|[END_CATCH_ALL](#end_catch_all)|Beendet den letzten **CATCH_ALL** Codeblock.|
|[THROW](#throw)|Löst eine angegebene Ausnahme aus.|
|[THROW_LAST](#throw_last)|Löst die aktuell behandelte Ausnahme an den nächsten äußeren Handler aus.|

### <a name="exception-throwing-functions"></a>Exception-Throwing-Funktionen

|||
|-|-|
|[AfxThrowArchiveException](#afxthrowarchiveexception)|Löst eine Archivausnahme aus.|
|[AfxThrowFileException](#afxthrowfileexception)|Löst eine Dateiausnahme aus.|
|[AfxThrowInvalidArgException](#afxthrowinvalidargexception)|Löst eine ungültige Argumentausnahme aus.|
|[AfxThrowMemoryException](#afxthrowmemoryexception)|Löst eine Speicherausnahme aus.|
|[AfxThrowNotSupportedException](#afxthrownotsupportedexception)|Löst eine nicht unterstützte Ausnahme aus.|
|[AfxThrowResourceException](#afxthrowresourceexception)|Löst eine Windows-Ressource-nicht gefundene Ausnahme aus.|
|[AfxThrowUserException](#afxthrowuserexception)|Löst eine Ausnahme in einer vom Benutzer initiierten Programmaktion aus.|

MFC bietet zwei Ausnahmeauslösende Funktionen speziell für OLE-Ausnahmen:

### <a name="ole-exception-functions"></a>OLE-Ausnahmefunktionen

|||
|-|-|
|[AfxThrowOleDispatchException](#afxthrowoledispatchexception)|Löst eine Ausnahme innerhalb einer OLE-Automatisierungsfunktion aus.|
|[AfxThrowOleException](#afxthrowoleexception)|Löst eine OLE-Ausnahme aus.|

Um Datenbankausnahmen zu unterstützen, stellen die `CDBException` Datenbankklassen zwei Ausnahmeklassen sowie `CDaoException`und globale Funktionen zur Unterstützung der Ausnahmetypen bereit:

### <a name="dao-exception-functions"></a>DAO-Ausnahmefunktionen

|||
|-|-|
|[AfxThrowDAOException](#afxthrowdaoexception)|Löst eine [CDaoException](../../mfc/reference/cdaoexception-class.md) aus Ihrem eigenen Code aus.|
|[AfxThrowDBException](#afxthrowdbexception)|Löst eine [CDBException](../../mfc/reference/cdbexception-class.md) aus Ihrem eigenen Code aus.|

MFC bietet die folgende Beendigungsfunktion:

### <a name="termination-functions"></a>Beendigungsfunktionen

|||
|-|-|
|[AfxAbort](#afxabort)|Wird aufgerufen, um eine Anwendung zu beenden, wenn ein schwerwiegender Fehler auftritt.|

## <a name="try"></a><a name="try"></a>Versuchen

Richtet einen **TRY-Block** ein.

```
TRY
```

### <a name="remarks"></a>Bemerkungen

Ein **TRY-Block** identifiziert einen Codeblock, der Ausnahmen auslösen kann. Diese Ausnahmen werden in den folgenden **CATCH-** und **AND_CATCH-Blöcken** behandelt. Rekursion ist zulässig: Ausnahmen können an einen äußeren **TRY-Block** übergeben werden, entweder durch Ignorieren oder durch Verwendung des THROW_LAST-Makros. Beenden Sie den **TRY-Block** mit einem END_CATCH oder END_CATCH_ALL Makro.

Weitere Informationen finden Sie im Artikel [Ausnahmen](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Beispiel

Siehe Beispiel für [CATCH](#catch).

### <a name="requirements"></a>Requirements (Anforderungen)

Header: afx.h

## <a name="catch"></a><a name="catch"></a>Fangen

Definiert einen Codeblock, der den ersten Ausnahmetyp abfängt, der im vorherigen **TRY-Block** ausgelöst wurde.

```
CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>Parameter

*exception_class*<br/>
Gibt den Ausnahmetyp an, für den getestet werden soll. Eine Liste der Standardausnahmeklassen finden Sie unter Klasse [CException](../../mfc/reference/cexception-class.md).

*exception_object_pointer_name*<br/>
Gibt einen Namen für einen Ausnahmeobjektzeiger an, der vom Makro erstellt wird. Sie können den Zeigernamen verwenden, um auf das Ausnahmeobjekt innerhalb des **CATCH-Blocks** zuzugreifen. Diese Variable wird für Sie deklariert.

### <a name="remarks"></a>Bemerkungen

Der Ausnahmeverarbeitungscode kann das Ausnahmeobjekt ggf. abgefragt, um weitere Informationen über die spezifische Ursache der Ausnahme zu erhalten. Rufen Sie das THROW_LAST Makros auf, um die Verarbeitung auf den nächsten äußeren Ausnahmerahmen zu verschieben. Beenden Sie den **TRY-Block** mit einem END_CATCH-Makro.

Wenn *exception_class* die `CException`Klasse ist, werden alle Ausnahmetypen abgefangen. Sie können die [Memberfunktion CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof) verwenden, um zu bestimmen, welche bestimmte Ausnahme ausgelöst wurde. Eine bessere Möglichkeit, mehrere Arten von Ausnahmen abzufangen, besteht darin, sequenzielle **AND_CATCH** Anweisungen mit jeweils einem anderen Ausnahmetyp zu verwenden.

Der Ausnahmeobjektzeiger wird vom Makro erstellt. Sie müssen es nicht selbst erklären.

> [!NOTE]
> Der **CATCH-Block** ist als C++-Bereich definiert, der durch geschweifte Klammern abgegrenzt wird. Wenn Sie Variablen in diesem Bereich deklarieren, können sie nur innerhalb dieses Bereichs zugänglich sein. Dies gilt auch für *exception_object_pointer_name*.

Weitere Informationen zu Ausnahmen und dem CATCH-Makro finden Sie im Artikel [Ausnahmen](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCExceptions#26](../../mfc/codesnippet/cpp/exception-processing_1.cpp)]

## <a name="catch_all"></a><a name="catch_all"></a>CATCH_ALL

Definiert einen Codeblock, der alle Ausnahmetypen abfängt, die im vorherigen **TRY-Block** ausgelöst werden.

```
CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>Parameter

*exception_object_pointer_name*<br/>
Gibt einen Namen für einen Ausnahmeobjektzeiger an, der vom Makro erstellt wird. Sie können den Zeigernamen verwenden, um `CATCH_ALL` auf das Ausnahmeobjekt innerhalb des Blocks zuzugreifen. Diese Variable wird für Sie deklariert.

### <a name="remarks"></a>Bemerkungen

Der Ausnahmeverarbeitungscode kann das Ausnahmeobjekt ggf. abgefragt, um weitere Informationen über die spezifische Ursache der Ausnahme zu erhalten. Rufen `THROW_LAST` Sie das Makro auf, um die Verarbeitung auf den nächsten äußeren Ausnahmerahmen zu verschieben. Wenn Sie **CATCH_ALL**verwenden, beenden Sie den **TRY-Block** mit einem END_CATCH_ALL-Makro.

> [!NOTE]
> Der **CATCH_ALL-Block** wird als C++-Bereich definiert, der durch geschweifte Klammern abgegrenzt wird. Wenn Sie Variablen in diesem Bereich deklarieren, können sie nur innerhalb dieses Bereichs zugänglich sein.

Weitere Informationen zu Ausnahmen finden Sie im Artikel [Ausnahmen](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Beispiel

Siehe Beispiel für [CFile::Abort](../../mfc/reference/cfile-class.md#abort).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afx.h

## <a name="and_catch"></a><a name="and_catch"></a>AND_CATCH

Definiert einen Codeblock zum Abfangen zusätzlicher Ausnahmetypen, die in einem vorherigen **TRY-Block** ausgelöst werden.

```
AND_CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>Parameter

*exception_class*<br/>
Gibt den Ausnahmetyp an, für den getestet werden soll. Eine Liste der Standardausnahmeklassen finden Sie unter Klasse [CException](../../mfc/reference/cexception-class.md).

*exception_object_pointer_name*<br/>
Ein Name für einen Ausnahmeobjektzeiger, der vom Makro erstellt wird. Sie können den Zeigernamen verwenden, um auf das Ausnahmeobjekt im **AND_CATCH-Block** zuzugreifen. Diese Variable wird für Sie deklariert.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie das CATCH-Makro, um einen Ausnahmetyp abzufangen, und dann das AND_CATCH Makro, um jeden nachfolgenden Typ abzufangen. Beenden Sie den **TRY-Block** mit einem END_CATCH-Makro.

Der Ausnahmeverarbeitungscode kann das Ausnahmeobjekt ggf. abgefragt, um weitere Informationen über die spezifische Ursache der Ausnahme zu erhalten. Rufen Sie das THROW_LAST Makro innerhalb des **AND_CATCH-Blocks** auf, um die Verarbeitung auf den nächsten äußeren Ausnahmerahmen zu verschieben. **AND_CATCH** markiert das Ende des vorhergehenden **CATCH-** oder **AND_CATCH-Blocks.**

> [!NOTE]
> Der **AND_CATCH-Block** wird als C++-Bereich definiert (durch geschweifte Klammern abgegrenzt). Wenn Sie Variablen in diesem Bereich deklarieren, denken Sie daran, dass nur innerhalb dieses Bereichs darauf zugegriffen werden kann. Dies gilt auch für die *exception_object_pointer_name* Variable.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CATCH](#catch).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afx.h

## <a name="and_catch_all"></a><a name="and_catch_all"></a>AND_CATCH_ALL

Definiert einen Codeblock zum Abfangen zusätzlicher Ausnahmetypen, die in einem vorherigen **TRY-Block** ausgelöst werden.

```
AND_CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>Parameter

*exception_object_pointer_name*<br/>
Ein Name für einen Ausnahmeobjektzeiger, der vom Makro erstellt wird. Sie können den Zeigernamen verwenden, um auf das Ausnahmeobjekt im **AND_CATCH_ALL-Block** zuzugreifen. Diese Variable wird für Sie deklariert.

### <a name="remarks"></a>Bemerkungen

Verwenden **CATCH** Sie das CATCH-Makro, um einen Ausnahmetyp abzufangen, und anschließend das AND_CATCH_ALL Makro, um alle anderen nachfolgenden Typen abzufangen. Wenn Sie AND_CATCH_ALL verwenden, beenden Sie den **TRY-Block** mit einem END_CATCH_ALL-Makro.

Der Ausnahmeverarbeitungscode kann das Ausnahmeobjekt ggf. abgefragt, um weitere Informationen über die spezifische Ursache der Ausnahme zu erhalten. Rufen Sie das THROW_LAST Makro innerhalb des **AND_CATCH_ALL-Blocks** auf, um die Verarbeitung auf den nächsten äußeren Ausnahmerahmen zu verschieben. **AND_CATCH_ALL** markiert das Ende des vorhergehenden **CATCH-** oder **AND_CATCH_ALL-Blocks.**

> [!NOTE]
> Der **AND_CATCH_ALL-Block** ist als C++-Bereich definiert (durch geschweifte Klammern definiert). Wenn Sie Variablen in diesem Bereich deklarieren, denken Sie daran, dass nur innerhalb dieses Bereichs darauf zugegriffen werden kann.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afx.h

## <a name="end_catch"></a><a name="end_catch"></a>END_CATCH

Markiert das Ende des letzten **CATCH-** oder **AND_CATCH-Blocks.**

```
END_CATCH
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zum END_CATCH-Makro finden Sie im Artikel [Ausnahmen](../../mfc/exception-handling-in-mfc.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afx.h

## <a name="end_catch_all"></a><a name="end_catch_all"></a>END_CATCH_ALL

Markiert das Ende des letzten **CATCH_ALL88** oder **AND_CATCH_ALL** Blocks.

```
END_CATCH_ALL
```

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afx.h

## <a name="throw-mfc"></a><a name="throw"></a>THROW (MFC)

Löst die angegebene Ausnahme aus.

```
THROW(exception_object_pointer)
```

### <a name="parameters"></a>Parameter

*exception_object_pointer*<br/>
Verweist auf ein Ausnahmeobjekt, das von `CException`abgeleitet wurde.

### <a name="remarks"></a>Bemerkungen

**THROW** unterbricht die Programmausführung und übergibt die Steuerung an den zugehörigen **CATCH-Block** in Ihrem Programm. Wenn Sie den **CATCH-Block** nicht bereitgestellt haben, wird das Steuerelement an ein Microsoft Foundation-Klassenbibliotheksmodul übergeben, das eine Fehlermeldung druckt und beendet.

Weitere Informationen finden Sie im Artikel [Ausnahmen](../../mfc/exception-handling-in-mfc.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afx.h

## <a name="throw_last"></a><a name="throw_last"></a>THROW_LAST

Löst die Ausnahme zurück **CATCH** zum nächsten äußeren CATCH-Block.

```
THROW_LAST()
```

### <a name="remarks"></a>Bemerkungen

Mit diesem Makro können Sie eine lokal erstellte Ausnahme auslösen. Wenn Sie versuchen, eine Ausnahme auszulösen, die Sie gerade abgefangen haben, wird sie normalerweise aus dem Gültigkeitsbereich entfernt und gelöscht. Mit **THROW_LAST**wird die Ausnahme korrekt an den nächsten **CATCH-Handler** übergeben.

Weitere Informationen finden Sie im Artikel [Ausnahmen](../../mfc/exception-handling-in-mfc.md).

### <a name="example"></a>Beispiel

Siehe Beispiel für [CFile::Abort](../../mfc/reference/cfile-class.md#abort).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afx.h

## <a name="afxthrowarchiveexception"></a><a name="afxthrowarchiveexception"></a>AfxThrowArchiveException

Löst eine Archivausnahme aus.

```cpp
void  AfxThrowArchiveException(int cause, LPCTSTR lpszArchiveName);
```

### <a name="parameters"></a>Parameter

*Ursache*<br/>
Gibt eine ganze Zahl an, die den Grund für die Ausnahme angibt. Eine Liste der möglichen Werte finden Sie unter [CArchiveException::m_cause](../../mfc/reference/carchiveexception-class.md#m_cause).

*lpszArchiveName*<br/>
Zeigt auf eine Zeichenfolge, `CArchive` die den Namen des Objekts enthält, das die Ausnahme verursacht hat (sofern verfügbar).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afx.h

## <a name="afxthrowfileexception"></a><a name="afxthrowfileexception"></a>AfxThrowFileException

Löst eine Dateiausnahme aus.

```cpp
void AfxThrowFileException(
    int cause,
    LONG lOsError = -1,
    LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>Parameter

*Ursache*<br/>
Gibt eine ganze Zahl an, die den Grund für die Ausnahme angibt. Eine Liste der möglichen Werte finden Sie unter [CFileException::m_cause](../../mfc/reference/cfileexception-class.md#m_cause).

*lOsError*<br/>
Enthält die Fehlernummer des Betriebssystems (falls verfügbar), die den Grund für die Ausnahme angibt. Eine Liste der Fehlercodes finden Sie in Ihrem Betriebssystemhandbuch.

*lpszFileName*<br/>
Zeigt auf eine Zeichenfolge, die den Namen der Datei enthält, die die Ausnahme verursacht hat (sofern verfügbar).

### <a name="remarks"></a>Bemerkungen

Sie sind für die Ermittlung der Ursache auf der Grundlage des Betriebssystemfehlercodes verantwortlich.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afx.h

## <a name="afxthrowinvalidargexception"></a><a name="afxthrowinvalidargexception"></a>AfxThrowInvalidArgException

Löst eine ungültige Argumentausnahme aus.

### <a name="syntax"></a>Syntax

```cpp
void AfxThrowInvalidArgException( );
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird aufgerufen, wenn ungültige Argumente verwendet werden.

### <a name="requirements"></a>Requirements (Anforderungen)

**Kopf:** afx.h

## <a name="afxthrowmemoryexception"></a><a name="afxthrowmemoryexception"></a>AfxThrowMemoryException

Löst eine Speicherausnahme aus.

```cpp
void AfxThrowMemoryException();
```

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, wenn Aufrufe von zugrunde liegenden Systemspeicherzuweisungen (z. B. **malloc** und die [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) Windows-Funktion) fehlschlagen. Sie müssen es nicht für **neu** aufrufen, da **new** automatisch eine Speicherausnahme auslöst, wenn die Speicherzuweisung fehlschlägt.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afx.h

## <a name="afxthrownotsupportedexception"></a><a name="afxthrownotsupportedexception"></a>AfxThrowNotSupportedException

Löst eine Ausnahme aus, die das Ergebnis einer Anforderung für ein nicht unterstütztes Feature ist.

```cpp
void AfxThrowNotSupportedException();
```

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afx.h

## <a name="afxthrowresourceexception"></a><a name="afxthrowresourceexception"></a>AfxThrowResourceException

Löst eine Ressourcenausnahme aus.

```cpp
void  AfxThrowResourceException();
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird normalerweise aufgerufen, wenn eine Windows-Ressource nicht geladen werden kann.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afx.h

## <a name="afxthrowuserexception"></a><a name="afxthrowuserexception"></a>AfxThrowUserException

Löst eine Ausnahme aus, um einen Endbenutzervorgang zu beenden.

```cpp
void AfxThrowUserException();
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird normalerweise `AfxMessageBox` sofort aufgerufen, nachdem sie dem Benutzer einen Fehler gemeldet hat.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afx.h

## <a name="afxthrowoledispatchexception"></a><a name="afxthrowoledispatchexception"></a>AfxThrowOleDispatchException

Verwenden Sie diese Funktion, um eine Ausnahme innerhalb einer OLE-Automatisierungsfunktion auszulösen.

```cpp
void AFXAPI AfxThrowOleDispatchException(
    WORD wCode ,
    LPCSTR lpszDescription,
    UINT nHelpID = 0);

void AFXAPI AfxThrowOleDispatchException(
    WORD wCode,
    UINT nDescriptionID,
    UINT nHelpID = -1);
```

### <a name="parameters"></a>Parameter

*wCode*<br/>
Ein für Ihre Anwendung spezifischer Fehlercode.

*lpszBeschreibung*<br/>
Verbale Beschreibung des Fehlers.

*nDescriptionID*<br/>
Ressourcen-ID für die verbale Fehlerbeschreibung.

*nHelpID*<br/>
Ein Hilfekontext für die Hilfe Ihrer Anwendung (. HLP)-Datei.

### <a name="remarks"></a>Bemerkungen

Die für diese Funktion bereitgestellten Informationen können von der treibern Anwendung (Microsoft Visual Basic oder einer anderen OLE-Automatisierungsclientanwendung) angezeigt werden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCExceptions#25](../../mfc/codesnippet/cpp/exception-processing_2.cpp)]

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afx.h

## <a name="afxthrowoleexception"></a><a name="afxthrowoleexception"></a>AfxThrowOleException

Erstellt ein Objekt `COleException` vom Typ und löst eine Ausnahme aus.

```cpp
void AFXAPI AfxThrowOleException(SCODE sc);
void AFXAPI AfxThrowOleException(HRESULT hr);
```

### <a name="parameters"></a>Parameter

*Sc*<br/>
Ein OLE-Statuscode, der den Grund für die Ausnahme angibt.

*Hr*<br/>
Behandeln Sie einen Ergebniscode, der den Grund für die Ausnahme angibt.

### <a name="remarks"></a>Bemerkungen

Die Version, die ein HRESULT als Argument verwendet, konvertiert diesen Ergebniscode in den entsprechenden SCODE. Weitere Informationen zu HRESULT und SCODE finden Sie unter [Struktur von COM-Fehlercodes](/windows/win32/com/structure-of-com-error-codes) im Windows SDK.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdao.h

## <a name="afxthrowdaoexception"></a><a name="afxthrowdaoexception"></a>AfxThrowDaoException

Rufen Sie diese Funktion auf, um eine Ausnahme vom Typ [CDaoException](../../mfc/reference/cdaoexception-class.md) aus Ihrem eigenen Code auszulösen.

```cpp
void AFXAPI AfxThrowDaoException(
    int nAfxDaoError = NO_AFX_DAO_ERROR,
    SCODE scode = S_OK);
```

### <a name="parameters"></a>Parameter

*nAfxDaoError*<br/>
Ein Ganzzahlwert, der einen erweiterten DAO-Fehlercode darstellt, der einer der unter [CDaoException::m_nAfxDaoError](../../mfc/reference/cdaoexception-class.md#m_nafxdaoerror)aufgelisteten Werte sein kann.

*scode*<br/>
Ein OLE-Fehlercode von DAO vom Typ SCODE. Weitere Informationen finden Sie unter [CDaoException::m_scode](../../mfc/reference/cdaoexception-class.md#m_scode).

### <a name="remarks"></a>Bemerkungen

Der Rahmen `AfxThrowDaoException`ruft auch auf . In Ihrem Aufruf können Sie einen der Parameter oder beide übergeben. Wenn Sie z. B. einen der in **CDaoException::nAfxDaoError** definierten Fehler auslösen möchten, sich jedoch nicht um den *scode-Parameter* kümmern, übergeben Sie einen gültigen Code im Parameter *nAfxDaoError,* und akzeptieren Sie den Standardwert für *scode*.

Informationen zu Ausnahmen im Zusammenhang mit den MFC `CDaoException` DAO-Klassen finden Sie in der Klasse in diesem Buch und im Artikel [Ausnahmen: Datenbankausnahmen](../../mfc/exceptions-database-exceptions.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdb.h

## <a name="afxthrowdbexception"></a><a name="afxthrowdbexception"></a>AfxThrowDBException

Rufen Sie diese Funktion auf, um eine Ausnahme des Typs `CDBException` aus Ihrem eigenen Code auszulösen.

```cpp
void AfxThrowDBException(
    RETCODE nRetCode,
    CDatabase* pdb,
    HSTMT hstmt);
```

### <a name="parameters"></a>Parameter

*nRetCode*<br/>
Ein Wert vom Typ RETCODE, der den Fehlertyp definiert, der das Auslösen der Ausnahme verursacht hat.

*Pdb*<br/>
Ein Zeiger auf `CDatabase` das Objekt, das die Datenquellenverbindung darstellt, der die Ausnahme zugeordnet ist.

*hstmt*<br/>
Ein ODBC HSTMT-Handle, das das Anweisungshandle angibt, dem die Ausnahme zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

Das Framework `AfxThrowDBException` ruft auf, wenn es einen ODBC RETCODE von einem Aufruf an eine ODBC-API-Funktion empfängt, und interpretiert den RETCODE als außergewöhnliche Bedingung und nicht als erwarteten Fehler. Beispielsweise kann ein Datenzugriffsvorgang aufgrund eines Datenträgerlesefehlers fehlschlagen.

Informationen zu den von ODBC definierten RETCODE-Werten finden Sie in Kapitel 8, "Abrufen von Status und Fehlerinformationen", im Windows SDK. Informationen zu MFC-Erweiterungen dieser Codes finden Sie unter Klasse [CDBException](../../mfc/reference/cdbexception-class.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afx.h

## <a name="afxabort"></a><a name="afxabort"></a>AfxAbort

Die von MFC bereitgestellte Standardbeendigungsfunktion.

```cpp
void  AfxAbort();
```

### <a name="remarks"></a>Bemerkungen

`AfxAbort`wird intern von MFC-Memberfunktionen aufgerufen, wenn ein schwerwiegender Fehler auftritt, z. B. eine nicht abgefangene Ausnahme, die nicht behandelt werden kann. Sie können `AfxAbort` in dem seltenen Fall anrufen, wenn sie auf einen katastrophalen Fehler stoßen, von dem Sie nicht wiederherstellen können.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CATCH](#catch).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afx.h

## <a name="see-also"></a>Weitere Informationen

[MFC-Makros, globale Funktionen und globale Variablen](mfc-macros-and-globals.md)<br/>
[CException-Klasse](cexception-class.md)<br/>
[CInvalidArgException-Klasse](cinvalidargexception-class.md)
