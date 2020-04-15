---
title: Debuggen und Fehlerberichterstattung Globale Funktionen
ms.date: 11/04/2016
f1_keywords:
- atlcomcli/ATL::AtlHresultFromLastError
- atlcom/ATL::AtlReportError
- atldef/ATL::AtlThrow
helpviewer_keywords:
- functions [ATL], error reporting
ms.assetid: 11339c02-98cd-428d-b3b9-7deeb155a6a3
ms.openlocfilehash: f7636b1f4e13340b223edd8c63c39bbeb21c8bd0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330208"
---
# <a name="debugging-and-error-reporting-global-functions"></a>Debuggen und Fehlerberichterstattung Globale Funktionen

Diese Funktionen bieten nützliche Debugging- und Ablaufverfolgungsfunktionen.

|||
|-|-|
|[AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror)|Gibt `GetLastError` einen Fehlercode in Form eines HRESULT zurück.|
|[AtlHresultFromWin32](debugging-and-error-reporting-global-functions.md#atlhresultfromwin32)|Konvertiert einen Win32-Fehlercode in ein HRESULT.|
|[AtlReportError](debugging-and-error-reporting-global-functions.md#atlreporterror)|Legt `IErrorInfo` fest, dass einem Client Fehlerdetails zur Verfügung stehen.|
|[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)|Löst eine `CAtlException` aus.|
|[AtlThrowLastWin32](debugging-and-error-reporting-global-functions.md#atlthrowlastwin32)|Mit dieser Funktion können Sie auf der Grundlage des Ergebnisses der Windows-Funktion `GetLastError` einen Fehler signalisieren.|

## <a name="atlhresultfromlasterror"></a><a name="atlhresultfromlasterror"></a>AtlHresultFromLastError

Gibt den Codewert des letzten Fehlers des aufrufenden Threads in Form eines HRESULT zurück.

```
HRESULT AtlHresultFromLastError();
```

### <a name="remarks"></a>Bemerkungen

`AtlHresultFromLastError`ruft `GetLastError` auf, um den letzten Fehler zu erhalten, und gibt den Fehler zurück, nachdem er mithilfe des HRESULT_FROM_WIN32-Makros in ein HRESULT konvertiert wurde.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcomcli.h

## <a name="atlhresultfromwin32"></a><a name="atlhresultfromwin32"></a>AtlHresultVonWin32

Konvertiert einen Win32-Fehlercode in ein HRESULT.

```
AtlHresultFromWin32(DWORD error);
```

### <a name="parameters"></a>Parameter

*error*<br/>
Der zu konvertierende Fehlerwert.

### <a name="remarks"></a>Bemerkungen

Konvertiert einen Win32-Fehlercode mithilfe des Makros HRESULT_FROM_WIN32 in ein HRESULT.

> [!NOTE]
> Anstatt zu `HRESULT_FROM_WIN32(GetLastError())`verwenden, verwenden Sie die Funktion [AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror).

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcomcli.h

## <a name="atlreporterror"></a><a name="atlreporterror"></a>AtlReportError

Richtet die `IErrorInfo` Schnittstelle so ein, dass Fehlerinformationen für Clients des Objekts zurückgegeben werden.

```
HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCOLESTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCOLESTR lpszDesc,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCSTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    LPCSTR lpszDesc,
    DWORD dwHelpID,
    LPCSTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    UINT nID,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance());

HRESULT WINAPI AtlReportError(
    const CLSID& clsid,
    UINT nID,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance());
```

### <a name="parameters"></a>Parameter

*clsid*<br/>
[in] Die CLSID des Objekts, das den Fehler meldet.

*lpszDesc*<br/>
[in] Die Zeichenfolge, die den Fehler beschreibt. Die Unicode-Versionen geben an, dass *lpszDesc* vom Typ LPCOLESTR ist. Die ANSI-Version gibt einen LPCSTR-Typ an.

*Iid*<br/>
[in] Die IID der Schnittstelle, die den Fehler definiert oder GUID_NULL, wenn der Fehler vom Betriebssystem definiert wird.

*hRes*<br/>
[in] Das HRESULT, das an den Aufrufer zurückgegeben werden soll.

*nID*<br/>
[in] Der Ressourcenbezeichner, in dem die Fehlerbeschreibungszeichenfolge gespeichert ist. Dieser Wert sollte zwischen 0x0200 und 0xFFFF liegen, einschließlich. In Debugbuilds wird ein **ASSERT** resultiert, wenn *nID* keine gültige Zeichenfolge indiziert. In Releasebuilds wird die Fehlerbeschreibungszeichenfolge auf "Unbekannter Fehler" festgelegt.

*dwHelpID*<br/>
[in] Der Hilfekontextbezeichner für den Fehler.

*lpszHelpFile*<br/>
[in] Der Pfad und der Name der Hilfedatei, die den Fehler beschreibt.

*hInst*<br/>
[in] Das Handle für die Ressource. Standardmäßig ist `__AtlBaseModuleModule::GetResourceInstance`dieser Parameter `__AtlBaseModuleModule` , wobei sich die globale Instanz von [CAtlBaseModule](../../atl/reference/catlbasemodule-class.md) oder eine von ihr abgeleitete Klasse befindet.

### <a name="return-value"></a>Rückgabewert

Wenn der *hRes-Parameter* ungleich Null ist, gibt der Wert von *hRes*zurück. Wenn *hRes* Null ist, werden `AtlReportError` die ersten vier Versionen von return DISP_E_EXCEPTION. Die letzten beiden Versionen geben das Ergebnis des **Makros MAKE_HRESULT( 1, FACILITY_ITF,** `nID` **)** zurück.

### <a name="remarks"></a>Bemerkungen

Die Zeichenfolge *lpszDesc* wird als Textbeschreibung des Fehlers verwendet. Wenn der Client die *hRes* empfängt, von `AtlReportError` `IErrorInfo` denen Sie zurückkehren, kann der Client auf die Struktur zugreifen, um Details zum Fehler zu erhalten.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_COM#52](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_1.cpp)]

> [!CAUTION]
> Verwenden `AtlReportError` Sie sie nicht in C++-Catch-Handlern. Einige Überschreibungen dieser Funktionen verwenden intern die ATL-Zeichenfolgenkonvertierungsmakros, die wiederum die `_alloca` Funktion intern verwenden. Die `AtlReportError` Verwendung in einem C++-Catch-Handler kann Ausnahmen in C++-Catch-Handlern verursachen.

### <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="atlthrow"></a><a name="atlthrow"></a>AtlThrow

Rufen Sie diese Funktion auf, um einen Fehler basierend auf einem HRESULT-Statuscode zu signalisieren.

```
__declspec(noreturn) inline void AtlThrow(HRESULT hr);
```

### <a name="parameters"></a>Parameter

*Hr*<br/>
Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird von ATL- und MFC-Code im Falle einer Fehlerbedingung verwendet. Es kann auch aus Ihrem eigenen Code aufgerufen werden. Die Standardimplementierung dieser Funktion hängt von der Definition des Symbols _ATL_NO_EXCEPTIONS und vom Projekttyp, MFC oder ATL ab.

In allen Fällen verfolgt diese Funktion das HRESULT auf den Debugger.

In Visual Studio 2015 Update 3 und höher wird dieser Funktion __declspec(Noreturn) zugeschrieben, um falsche SAL-Warnungen zu vermeiden.

Wenn _ATL_NO_EXCEPTIONS nicht in einem MFC-Projekt definiert ist, löst diese Funktion eine [CMemoryException](../../mfc/reference/cmemoryexception-class.md) oder eine [COleException](../../mfc/reference/coleexception-class.md) basierend auf dem Wert des HRESULT aus.

Wenn _ATL_NO_EXCEPTIONS nicht in einem ATL-Projekt definiert ist, löst die Funktion eine [CAtlException](../../atl/reference/catlexception-class.md)aus.

Wenn _ATL_NO_EXCEPTIONS definiert ist, verursacht die Funktion einen Assertionsfehler, anstatt eine Ausnahme auszulösen.

Bei ATL-Projekten ist es möglich, eine eigene Implementierung dieser Funktion bereitzustellen, die ATL im Falle eines Fehlers verwenden kann. Definieren Sie dazu Ihre eigene Funktion mit `AtlThrow` derselben `AtlThrow` Signatur und #define, um den Namen Ihrer Funktion zu sein. Dies muss vor dem Einschließen von atlexcept.h erfolgen (was bedeutet, dass dies vor dem Einschließen von ATL-Headern erfolgen muss, da atlbase.h atlexcept.h enthält). Weisen Sie `__declspec(noreturn)` Ihre Funktion zu, um falsche SAL-Warnungen zu vermeiden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#95](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_2.h)]

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atldef.h

## <a name="atlthrowlastwin32"></a><a name="atlthrowlastwin32"></a>AtlThrowLastWin32

Mit dieser Funktion können Sie auf der Grundlage des Ergebnisses der Windows-Funktion `GetLastError` einen Fehler signalisieren.

```
inline void AtlThrowLastWin32();
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verfolgt `GetLastError` das Ergebnis von bis zum Debugger nach.

Wenn _ATL_NO_EXCEPTIONS nicht in einem MFC-Projekt definiert ist, löst diese Funktion eine [CMemoryException](../../mfc/reference/cmemoryexception-class.md) oder eine [COleException](../../mfc/reference/coleexception-class.md) basierend auf dem von `GetLastError`zurückgegebenen Wert aus.

Wenn _ATL_NO_EXCEPTIONS nicht in einem ATL-Projekt definiert ist, löst die Funktion eine [CAtlException](../../atl/reference/catlexception-class.md)aus.

Wenn _ATL_NO_EXCEPTIONS definiert ist, verursacht die Funktion einen Assertionsfehler, anstatt eine Ausnahme auszulösen.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atldef.h

## <a name="see-also"></a>Siehe auch

[Functions](../../atl/reference/atl-functions.md)<br/>
[Debuggen und Fehlerberichterstattungsmakros](../../atl/reference/debugging-and-error-reporting-macros.md)
