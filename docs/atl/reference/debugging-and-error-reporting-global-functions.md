---
title: Globale Funktionen zum Debuggen und zur Fehlerberichterstattung
ms.date: 11/04/2016
f1_keywords:
- atlcomcli/ATL::AtlHresultFromLastError
- atlcom/ATL::AtlReportError
- atldef/ATL::AtlThrow
helpviewer_keywords:
- functions [ATL], error reporting
ms.assetid: 11339c02-98cd-428d-b3b9-7deeb155a6a3
ms.openlocfilehash: 10aca6862f6989c126981a9f6437c61f1c07bdae
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742787"
---
# <a name="debugging-and-error-reporting-global-functions"></a>Globale Funktionen zum Debuggen und zur Fehlerberichterstattung

Diese Funktionen bieten nützliche Debugging-und Ablauf Verfolgungs Funktionen.

|Name|Beschreibung|
|-|-|
|[AtlHresultFromLastError](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror)|Gibt einen `GetLastError` Fehlercode in Form eines HRESULT zurück.|
|[AtlHresultFromWin32](debugging-and-error-reporting-global-functions.md#atlhresultfromwin32)|Konvertiert einen Win32-Fehlercode in ein HRESULT.|
|[AtlReportError](debugging-and-error-reporting-global-functions.md#atlreporterror)|Legt fest `IErrorInfo` , dass Fehlerdetails für einen Client bereitgestellt werden.|
|[AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow)|Löst eine `CAtlException` aus.|
|[AtlThrowLastWin32](debugging-and-error-reporting-global-functions.md#atlthrowlastwin32)|Mit dieser Funktion können Sie auf der Grundlage des Ergebnisses der Windows-Funktion `GetLastError` einen Fehler signalisieren.|

## <a name="atlhresultfromlasterror"></a><a name="atlhresultfromlasterror"></a> Atlhresultfromlasterror

Gibt den Codewert des letzten Fehlers des aufrufenden Threads in Form eines HRESULT zurück.

```
HRESULT AtlHresultFromLastError();
```

### <a name="remarks"></a>Bemerkungen

`AtlHresultFromLastError` Ruft `GetLastError` auf, um den letzten Fehler abzurufen, und gibt den Fehler zurück, nachdem er mithilfe des HRESULT_FROM_WIN32-Makros in ein HRESULT-Wert umgerechnet wurde

### <a name="requirements"></a>Anforderungen

**Header:** atlcomcli. h

## <a name="atlhresultfromwin32"></a><a name="atlhresultfromwin32"></a> AtlHresultFromWin32

Konvertiert einen Win32-Fehlercode in ein HRESULT.

```
AtlHresultFromWin32(DWORD error);
```

### <a name="parameters"></a>Parameter

*error*<br/>
Der zu konvertierende Fehlerwert.

### <a name="remarks"></a>Bemerkungen

Konvertiert einen Win32-Fehlercode unter Verwendung des Makro HRESULT_FROM_WIN32 in ein HRESULT.

> [!NOTE]
> Verwenden Sie anstelle von `HRESULT_FROM_WIN32(GetLastError())` die Funktion [atlhresultfromlasterror](debugging-and-error-reporting-global-functions.md#atlhresultfromlasterror).

### <a name="requirements"></a>Anforderungen

**Header:** atlcomcli. h

## <a name="atlreporterror"></a><a name="atlreporterror"></a> Atlreporterror

Richtet die- `IErrorInfo` Schnittstelle zum Bereitstellen von Fehlerinformationen für Clients des-Objekts ein.

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

*CLSID*<br/>
in Die CLSID des Objekts, das den Fehler meldet.

*lpszde*<br/>
in Die Zeichenfolge, die den Fehler beschreibt. Die Unicode-Versionen geben an, dass *lpszdesc* vom Typ lpcolestr ist. die ANSI-Version gibt den LPCSTR-Typ an.

*IID*<br/>
in Die IID der Schnittstelle, die den Fehler definiert, oder GUID_NULL, wenn der Fehler vom Betriebssystem definiert wird.

*hres*<br/>
in Das HRESULT, das an den Aufrufer zurückgegeben werden soll.

*nID*<br/>
in Der Ressourcen Bezeichner, in dem die Zeichenfolge zur Fehlerbeschreibung gespeichert wird. Dieser Wert sollte zwischen 0x0200 und 0xFFFF (einschließlich) liegen. In Debugbuilds ergibt sich eine **Assert** -Bestätigung, wenn *NID* keine gültige Zeichenfolge indiziert. In Releasebuilds wird die Fehler Beschreibungs Zeichenfolge auf "Unbekannter Fehler" festgelegt.

*dwhelpid*<br/>
in Der Hilfe Kontext Bezeichner für den Fehler.

*lpszhelpfile*<br/>
in Der Pfad und der Name der Hilfedatei, die den Fehler beschreibt.

*hinst*<br/>
in Das Handle für die Ressource. Standardmäßig ist dieser Parameter `__AtlBaseModuleModule::GetResourceInstance` , wobei `__AtlBaseModuleModule` die globale Instanz von "" [von "](../../atl/reference/catlbasemodule-class.md) " oder eine von ihr abgeleitete Klasse ist.

### <a name="return-value"></a>Rückgabewert

Wenn der *hres* -Parameter ungleich NULL ist, wird der Wert von *hres*zurückgegeben. Wenn *hres* 0 (null) ist, werden die ersten vier Versionen von `AtlReportError` DISP_E_EXCEPTION zurückgegeben. In den letzten beiden Versionen wird das Ergebnis des Makros zurückgegeben **MAKE_HRESULT (1, FACILITY_ITF,** `nID` **)**.

### <a name="remarks"></a>Bemerkungen

Die Zeichenfolge *lpszentsc* wird als Textbeschreibung des Fehlers verwendet. Wenn der Client die von Ihnen zurückgegebenen *hres* empfängt `AtlReportError` , kann der Client auf die-Struktur zugreifen, `IErrorInfo` um Details zum Fehler zu erhalten.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_COM#52](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_1.cpp)]

> [!CAUTION]
> Verwenden Sie `AtlReportError` in C++ catch-Handlern nicht. Einige über schreibungen dieser Funktionen verwenden intern die ATL-Zeichen folgen Konvertierungs Makros, die wiederum die `_alloca` Funktion intern verwenden. Die Verwendung von `AtlReportError` in einem C++ catch-Handler kann Ausnahmen in C++ catch-Handlern verursachen.

### <a name="requirements"></a>Anforderungen

**Header:** Atlcom. h

## <a name="atlthrow"></a><a name="atlthrow"></a> "Atlthrow"

Mit dieser Funktion wird ein Fehler auf der Grundlage eines HRESULT-Statuscodes signalisiert.

```
__declspec(noreturn) inline void AtlThrow(HRESULT hr);
```

### <a name="parameters"></a>Parameter

*Std.*<br/>
Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird von ATL-und MFC-Code im Fall eines Fehler Zustands verwendet. Sie kann auch über ihren eigenen Code aufgerufen werden. Die Standard Implementierung dieser Funktion hängt von der Definition des Symbols _ATL_NO_EXCEPTIONS und vom Projekttyp (MFC oder ATL) ab.

In allen Fällen verfolgt diese Funktion das HRESULT an den Debugger.

In Visual Studio 2015 Update 3 und höher wird diese Funktion __declspec (noreturn) attributiert, um falsche SAL-Warnungen zu vermeiden.

Wenn _ATL_NO_EXCEPTIONS nicht in einem MFC-Projekt definiert ist, löst diese Funktion eine [cmemoryexception](../../mfc/reference/cmemoryexception-class.md) oder eine [COleException](../../mfc/reference/coleexception-class.md) basierend auf dem Wert von HRESULT aus.

Wenn _ATL_NO_EXCEPTIONS nicht in einem ATL-Projekt definiert ist, löst die Funktion eine ""- [Ausnahme](../../atl/reference/catlexception-class.md)aus.

Wenn _ATL_NO_EXCEPTIONS definiert ist, verursacht die Funktion einen Fehler bei der Übersetzung, anstatt eine Ausnahme auszulösen.

Bei ATL-Projekten ist es möglich, eine eigene Implementierung dieser Funktion bereitzustellen, die von ATL bei einem Fehler verwendet werden kann. Definieren Sie zu diesem Zweck ihre eigene Funktion mit der gleichen Signatur wie `AtlThrow` und #define `AtlThrow` , um den Namen ihrer Funktion zu verwenden. Dies muss vor dem einschließen von "atlexcept. h" erfolgen (was bedeutet, dass es vor dem einschließen von ATL-Headern erfolgen muss, da "atlxcept. h" in "atlbase. h" enthalten ist). Attribut ihrer Funktion `__declspec(noreturn)` , um falsche SAL-Warnungen zu vermeiden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#95](../../atl/codesnippet/cpp/debugging-and-error-reporting-global-functions_2.h)]

### <a name="requirements"></a>Anforderungen

**Header:** atldef. h

## <a name="atlthrowlastwin32"></a><a name="atlthrowlastwin32"></a> AtlThrowLastWin32

Mit dieser Funktion können Sie auf der Grundlage des Ergebnisses der Windows-Funktion `GetLastError` einen Fehler signalisieren.

```
inline void AtlThrowLastWin32();
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion verfolgt das Ergebnis von `GetLastError` an den Debugger.

Wenn _ATL_NO_EXCEPTIONS nicht in einem MFC-Projekt definiert ist, löst diese Funktion eine [cmemoryexception](../../mfc/reference/cmemoryexception-class.md) oder eine [COleException](../../mfc/reference/coleexception-class.md) basierend auf dem Wert aus, der von zurückgegeben wird `GetLastError` .

Wenn _ATL_NO_EXCEPTIONS nicht in einem ATL-Projekt definiert ist, löst die Funktion eine ""- [Ausnahme](../../atl/reference/catlexception-class.md)aus.

Wenn _ATL_NO_EXCEPTIONS definiert ist, verursacht die Funktion einen Fehler bei der Übersetzung, anstatt eine Ausnahme auszulösen.

### <a name="requirements"></a>Anforderungen

**Header:** atldef. h

## <a name="see-also"></a>Siehe auch

[Funktionen](../../atl/reference/atl-functions.md)<br/>
[Debugging-und Fehlerberichterstattungs-Makros](../../atl/reference/debugging-and-error-reporting-macros.md)
