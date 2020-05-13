---
title: CDaoException-Klasse
ms.date: 09/17/2019
f1_keywords:
- CDaoException
- AFXDAO/CDaoException
- AFXDAO/CDaoException::CDaoException
- AFXDAO/CDaoException::GetErrorCount
- AFXDAO/CDaoException::GetErrorInfo
- AFXDAO/CDaoException::m_nAfxDaoError
- AFXDAO/CDaoException::m_pErrorInfo
- AFXDAO/CDaoException::m_scode
helpviewer_keywords:
- CDaoException [MFC], CDaoException
- CDaoException [MFC], GetErrorCount
- CDaoException [MFC], GetErrorInfo
- CDaoException [MFC], m_nAfxDaoError
- CDaoException [MFC], m_pErrorInfo
- CDaoException [MFC], m_scode
ms.assetid: b2b01fa9-7ce2-42a1-842e-40f13dc50da4
ms.openlocfilehash: 935d7870d68554d702e2ad762e83343cb518b2b8
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754729"
---
# <a name="cdaoexception-class"></a>CDaoException-Klasse

Stellt eine Ausnahmebedingung dar, die von MFC-Datenbankklassen in Bezug auf Datenzugriffsobjekte (DAOs) ausgelöst wird. DAO 3.6 ist die endgültige Version und gilt als veraltet.

## <a name="syntax"></a>Syntax

```
class CDaoException : public CException
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDaoException::CDaoException](#cdaoexception)|Erstellt ein `CDaoException`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDaoException::GetErrorCount](#geterrorcount)|Gibt die Anzahl der Fehler in der Errors-Auflistung des Datenbankmoduls zurück.|
|[CDaoException::GetErrorInfo](#geterrorinfo)|Gibt Fehlerinformationen zu einem bestimmten Fehlerobjekt in der Errors-Auflistung zurück.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDaoAusnahme::m_nAfxDaoError](#m_nafxdaoerror)|Enthält einen erweiterten Fehlercode für Fehler in den MFC DAO-Klassen.|
|[CDaoException::m_pErrorInfo](#m_perrorinfo)|Ein Zeiger auf ein [CDaoErrorInfo-Objekt,](../../mfc/reference/cdaoerrorinfo-structure.md) das Informationen zu einem DAO-Fehlerobjekt enthält.|
|[CDaoAusnahme::m_scode](#m_scode)|Der Dem Fehler zugeordnete [SCODE-Wert.](#m_scode)|

## <a name="remarks"></a>Bemerkungen

Die Klasse enthält öffentliche Datenmember, mit denen Sie die Ursache der Ausnahme ermitteln können. `CDaoException`Objekte werden von Memberfunktionen der DAO-Datenbankklassen erstellt und ausgelöst.

> [!NOTE]
> Die DAO-Datenbankklassen unterscheiden sich von den MFC-Datenbankklassen, die auf Open Database Connectivity (ODBC) basieren. Alle DAO-Datenbankklassennamen haben das Präfix "CDao". Sie können weiterhin mit den DAO-Klassen auf ODBC-Datenquellen zugreifen. Im Allgemeinen sind die Aufbasis von DAO basierenden MFC-Klassen leistungsfähiger als die MFC-Klassen, die auf ODBC basieren. Die DAO-basierten Klassen können über ihre eigene Datenbank-Engine auf Daten zugreifen, auch über ODBC-Treiber. Die DAO-basierten Klassen unterstützen auch DDL-Vorgänge (Data Definition Language), z. B. das Hinzufügen von Tabellen über die Klassen, ohne DAO direkt aufrufen zu müssen. Informationen zu Ausnahmen, die von den ODBC-Klassen ausgelöst werden, finden Sie unter [CDBException](../../mfc/reference/cdbexception-class.md).

Sie können im Rahmen eines [CATCH-Ausdrucks](../../mfc/reference/exception-processing.md#catch) auf Ausnahmeobjekte zugreifen. Sie können `CDaoException` auch Objekte aus Ihrem eigenen Code mit der globalen Funktion [AfxThrowDaoException](../../mfc/reference/exception-processing.md#afxthrowdaoexception) auslösen.

In MFC werden alle DAO-Fehler als `CDaoException`Ausnahmen vom Typ ausgedrückt. Wenn Sie eine Ausnahme dieses Typs `CDaoException` abfangen, können Sie Memberfunktionen verwenden, um Informationen aus allen DAO-Fehlerobjekten abzurufen, die in der Errors-Auflistung des Datenbankmoduls gespeichert sind. Wenn jeder Fehler auftritt, werden ein oder mehrere Fehlerobjekte in der Errors-Auflistung platziert. (Normalerweise enthält die Auflistung nur ein Fehlerobjekt; wenn Sie eine ODBC-Datenquelle verwenden, erhalten Sie mit größerer Wahrscheinlichkeit mehrere Fehlerobjekte.) Wenn ein anderer DAO-Vorgang einen Fehler generiert, wird die Errors-Auflistung gelöscht, und das neue Fehlerobjekt wird in der Errors-Auflistung platziert. DAO-Vorgänge, die keinen Fehler generieren, haben keine Auswirkungen auf die Errors-Auflistung.

DaO-Fehlercodes finden Sie in der Datei DAOERR. H. Weitere Informationen finden Sie im Thema "Trappable Data Access Errors" in der DAO-Hilfe.

Weitere Informationen zur Ausnahmebehandlung im `CDaoException` Allgemeinen oder zu Objekten finden Sie in den Artikeln [Exception Handling (MFC)](../../mfc/exception-handling-in-mfc.md) und [Exceptions: Database Exceptions](../../mfc/exceptions-database-exceptions.md). Der zweite Artikel enthält Beispielcode, der die Ausnahmebehandlung in DAO veranschaulicht.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CDaoException`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdao.h

## <a name="cdaoexceptioncdaoexception"></a><a name="cdaoexception"></a>CDaoException::CDaoException

Erstellt ein `CDaoException`-Objekt.

```
CDaoException();
```

### <a name="remarks"></a>Bemerkungen

Normalerweise erstellt das Framework Ausnahmeobjekte, wenn sein Code eine Ausnahme auslöst. Sie müssen selten ein Ausnahmeobjekt explizit erstellen. Wenn Sie eine `CDaoException` aus Ihrem eigenen Code auslösen möchten, rufen Sie die globale Funktion [AfxThrowDaoException](../../mfc/reference/exception-processing.md#afxthrowdaoexception)auf.

Sie können jedoch explizit ein Ausnahmeobjekt erstellen, wenn Sie über die DAO-Schnittstellenzeiger, die MFC-Klassen kapseln, direkte Aufrufe von DAO tätigen. In diesem Fall müssen Sie möglicherweise Fehlerinformationen von DAO abrufen. Angenommen, ein Fehler tritt in DAO auf, wenn Sie eine DAO-Methode über die DAODatabases-Schnittstelle zur Datenbanksammlung eines Arbeitsbereichs aufrufen.

##### <a name="to-retrieve-the-dao-error-information"></a>So rufen Sie die DAO-Fehlerinformationen ab

1. Konstruieren Sie ein `CDaoException`-Objekt.

1. Rufen Sie die [GetErrorCount-Memberfunktion](#geterrorcount) des Ausnahmeobjekts auf, um zu bestimmen, wie viele Fehlerobjekte sich in der Errors-Auflistung des Datenbankmoduls befinden. (Normalerweise nur eine, es sei denn, Sie verwenden eine ODBC-Datenquelle.)

1. Rufen Sie die [GetErrorInfo-Memberfunktion](#geterrorinfo) des Ausnahmeobjekts auf, um jeweils ein bestimmtes Fehlerobjekt nach Index in der Auflistung über das Ausnahmeobjekt abzurufen. Stellen Sie sich das Ausnahmeobjekt als Proxy für ein DAO-Fehlerobjekt vor.

1. Untersuchen Sie die aktuelle [CDaoErrorInfo-Struktur,](../../mfc/reference/cdaoerrorinfo-structure.md) die `GetErrorInfo` im [m_pErrorInfo-Datenmember](#m_perrorinfo) zurückgegeben wird. Seine Mitglieder geben Informationen über den DAO-Fehler.

1. Wiederholen Sie bei einer ODBC-Datenquelle die Schritte 3 und 4 nach Bedarf, um weitere Fehlerobjekte anzuzeigen.

1. Wenn Sie das Ausnahmeobjekt auf dem Heap erstellt haben, löschen Sie es mit dem **Löschoperator,** wenn Sie fertig sind.

Weitere Informationen zum Behandeln von Fehlern in den MFC DAO-Klassen finden Sie im Artikel [Ausnahmen: Datenbankausnahmen](../../mfc/exceptions-database-exceptions.md).

## <a name="cdaoexceptiongeterrorcount"></a><a name="geterrorcount"></a>CDaoException::GetErrorCount

Rufen Sie diese Memberfunktion auf, um die Anzahl der DAO-Fehlerobjekte in der Errors-Auflistung des Datenbankmoduls abzurufen.

```
short GetErrorCount();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der DAO-Fehlerobjekte in der Errors-Auflistung des Datenbankmoduls.

### <a name="remarks"></a>Bemerkungen

Diese Informationen sind nützlich, um die Errors-Auflistung zu durchlaufen, um jedes der mindestens ein DAO-Fehlerobjekte in der Auflistung abzurufen. Um ein Fehlerobjekt nach Index oder DAO-Fehlernummer abzurufen, rufen Sie die [GetErrorInfo-Memberfunktion](#geterrorinfo) auf.

> [!NOTE]
> Normalerweise gibt es nur ein Fehlerobjekt in der Errors-Auflistung. Wenn Sie jedoch mit einer ODBC-Datenquelle arbeiten, kann es mehrere geben.

## <a name="cdaoexceptiongeterrorinfo"></a><a name="geterrorinfo"></a>CDaoException::GetErrorInfo

Gibt Fehlerinformationen zu einem bestimmten Fehlerobjekt in der Errors-Auflistung zurück.

```cpp
void GetErrorInfo(int nIndex);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Der Index der Fehlerinformationen in der Errors-Auflistung des Datenbankmoduls für die Suche nach Index.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Memberfunktion auf, um die folgenden Arten von Informationen über die Ausnahme abzurufen:

- Fehlercode

- `Source`

- BESCHREIBUNG

- Hilfedatei

- Hilfekontext

`GetErrorInfo`speichert die Informationen im Datenmember des Ausnahmeobjekts. `m_pErrorInfo` Eine kurze Beschreibung der zurückgegebenen Informationen finden Sie [unter m_pErrorInfo](#m_perrorinfo). Wenn Sie eine Ausnahme `CDaoException` vom von MFC ausgelösten Typ abfangen, wird der `m_pErrorInfo` Member bereits ausgefüllt. Wenn Sie DAO direkt aufrufen möchten, müssen Sie `GetErrorInfo` die Memberfunktion `m_pErrorInfo`des Ausnahmeobjekts selbst aufrufen, um sie zu füllen. Eine ausführlichere Beschreibung finden Sie in der [CDaoErrorInfo-Struktur.](../../mfc/reference/cdaoerrorinfo-structure.md)

Informationen zu DAO-Ausnahmen und Beispielcode finden Sie im Artikel [Ausnahmen: Datenbankausnahmen](../../mfc/exceptions-database-exceptions.md).

## <a name="cdaoexceptionm_nafxdaoerror"></a><a name="m_nafxdaoerror"></a>CDaoAusnahme::m_nAfxDaoError

Enthält einen erweiterten MFC-Fehlercode.

### <a name="remarks"></a>Bemerkungen

Dieser Code wird in Fällen bereitgestellt, in denen eine bestimmte Komponente der MFC DAO-Klassen einen Fehler gemacht hat.

Mögliche Werte:

- NO_AFX_DAO_ERROR Der letzte Vorgang hat nicht zu einem erweiterten MFC-Fehler geführt. Der Vorgang könnte jedoch zu anderen Fehlern von DAO oder OLE führen können, daher sollten Sie [m_pErrorInfo](#m_perrorinfo) überprüfen und möglicherweise [m_scode](#m_scode).

- AFX_DAO_ERROR_ENGINE_INITIALIZATION MFC konnte das Microsoft Jet-Datenbankmodul nicht initialisieren. OLE konnte möglicherweise nicht initialisiert werden, oder es war nicht möglich, eine Instanz des DAO-Datenbankmodulobjekts zu erstellen. Diese Probleme deuten in der Regel auf eine fehlerhafte Installation von DAO oder OLE hin.

- AFX_DAO_ERROR_DFX_BIND Eine Adresse, die in einem DFX-Funktionsaufruf (DFX) (DAO Record Field Exchange) verwendet wird, ist nicht vorhanden oder ungültig (die Adresse wurde nicht zum Binden von Daten verwendet). Möglicherweise haben Sie eine fehlerhafte Adresse in einem DFX-Aufruf übergeben, oder die Adresse ist zwischen DFX-Vorgängen ungültig geworden.

- AFX_DAO_ERROR_OBJECT_NOT_OPEN Sie haben versucht, ein Recordset basierend auf einem querydef- oder tabledef-Objekt zu öffnen, das sich nicht in einem offenen Zustand befand.

## <a name="cdaoexceptionm_perrorinfo"></a><a name="m_perrorinfo"></a>CDaoException::m_pErrorInfo

Enthält einen Zeiger `CDaoErrorInfo` auf eine Struktur, die Informationen zum DAO-Fehlerobjekt bereitstellt, das Sie zuletzt durch Aufrufen von [GetErrorInfo](#geterrorinfo)abgerufen haben.

### <a name="remarks"></a>Bemerkungen

Dieses Objekt enthält die folgenden Informationen:

|CDaoErrorInfo-Member|Information|Bedeutung|
|--------------------------|-----------------|-------------|
|`m_lErrorCode`|Fehlercode|Der DAO-Fehlercode|
|`m_strSource`|`Source`|Der Name des Objekts oder der Anwendung, das den Fehler ursprünglich generiert hat|
|`m_strDescription`|BESCHREIBUNG|Eine beschreibende Zeichenfolge, die dem Fehler zugeordnet ist|
|`m_strHelpFile`|Hilfedatei|Ein Pfad zu einer Windows-Hilfedatei, in der der Benutzer Informationen über das Problem abrufen kann|
|`m_lHelpContext`|Hilfekontext|Die Kontext-ID für ein Thema in der DAO-Hilfedatei|

Ausführliche Informationen zu den im `CDaoErrorInfo` Objekt enthaltenen Informationen finden Sie in der [CDaoErrorInfo-Struktur.](../../mfc/reference/cdaoerrorinfo-structure.md)

## <a name="cdaoexceptionm_scode"></a><a name="m_scode"></a>CDaoAusnahme::m_scode

Enthält einen Wert `SCODE` des Typs, der den Fehler beschreibt.

### <a name="remarks"></a>Bemerkungen

Dies ist ein OLE-Code. Sie müssen diesen Wert selten verwenden, da in fast allen Fällen spezifischere MFC- `CDaoException` oder DAO-Fehlerinformationen in den anderen Datenmembern verfügbar sind.

Informationen zu SCODE finden Sie im Thema [Struktur von OLE-Fehlercodes](/windows/win32/com/structure-of-com-error-codes) im Windows SDK. Der SCODE-Datentyp wird dem HRESULT-Datentyp zugeordnet.

## <a name="see-also"></a>Weitere Informationen

[CException-Klasse](../../mfc/reference/cexception-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CException-Klasse](../../mfc/reference/cexception-class.md)
