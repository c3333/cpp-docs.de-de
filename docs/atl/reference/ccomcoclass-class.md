---
title: CComCoClass-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComCoClass
- ATLCOM/ATL::CComCoClass
- ATLCOM/ATL::CComCoClass::CreateInstance
- ATLCOM/ATL::CComCoClass::Error
- ATLCOM/ATL::CComCoClass::GetObjectCLSID
- ATLCOM/ATL::CComCoClass::GetObjectDescription
helpviewer_keywords:
- CComCoClass class
- aggregation [C++], aggregation models
ms.assetid: 67cfefa4-8df9-47fa-ad58-2d1a1ae25762
ms.openlocfilehash: 11e724a982f3a2f404473dbdd34d848842cc8e14
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320825"
---
# <a name="ccomcoclass-class"></a>CComCoClass-Klasse

Diese Klasse stellt Methoden zum Erstellen von Instanzen einer Klasse und zum Abrufen ihrer Eigenschaften bereit.

## <a name="syntax"></a>Syntax

```
template <class T, const CLSID* pclsid = &CLSID_NULL>
class CComCoClass
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Ihre Klasse, `CComCoClass`abgeleitet von .

*pclsid*<br/>
Ein Zeiger auf die CLSID des Objekts.

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComCoClass::CreateInstance](#createinstance)|(Statisch) Erstellt eine Instanz der Klasse und fragt nach einer Schnittstelle ab.|
|[CComCoClass::Fehler](#error)|(Statisch) Gibt umfangreiche Fehlerinformationen an den Client zurück.|
|[CComCoClass::GetObjectCLSID](#getobjectclsid)|(Statisch) Gibt den Klassenbezeichner des Objekts zurück.|
|[CComCoClass::GetObjectDescription](#getobjectdescription)|(Statisch) Überschreiben, um die Beschreibung des Objekts zurückzugeben.|

## <a name="remarks"></a>Bemerkungen

`CComCoClass`stellt Methoden zum Abrufen der CLSID eines Objekts, zum Festlegen von Fehlerinformationen und zum Erstellen von Instanzen der Klasse bereit. Jede Klasse, die in der `CComCoClass`Objektzuordnung registriert ist, sollte von abgeleitet werden.

`CComCoClass`definiert auch die Standardklassenfactory und das Aggregationsmodell für Ihr Objekt. `CComCoClass`verwendet die folgenden beiden Makros:

- [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory) Deklariert die Klassenfactory als [CComClassFactory](../../atl/reference/ccomclassfactory-class.md).

- [DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable) Deklariert, dass Ihr Objekt aggregiert werden kann.

Sie können eine dieser Standardeinstellungen überschreiben, indem Sie ein anderes Makro in der Klassendefinition angeben. Um z. B. [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) anstelle von `CComClassFactory`zu verwenden, geben Sie das [DECLARE_CLASSFACTORY2-Makro](aggregation-and-class-factory-macros.md#declare_classfactory2) an:

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomcoclass-class_1.h)]

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="ccomcoclasscreateinstance"></a><a name="createinstance"></a>CComCoClass::CreateInstance

Verwenden `CreateInstance` Sie diese Funktionen, um eine Instanz eines COM-Objekts zu erstellen und einen Schnittstellenzeiger ohne Verwendung der COM-API abzurufen.

```
template <class  Q>
static HRESULT CreateInstance( Q** pp);

template <class  Q>
static HRESULT CreateInstance(IUnknown* punkOuter, Q** pp);
```

### <a name="parameters"></a>Parameter

*Q*<br/>
Die COM-Schnittstelle, die über *pp*zurückgegeben werden soll.

*punkOuter*<br/>
[in] Das äußere Unbekannte oder Steuern unbekannt des Aggregats.

*Pp*<br/>
[out] Die Adresse einer Zeigervariablen, die den angeforderten Schnittstellenzeiger empfängt, wenn die Erstellung erfolgreich ist.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert. Eine Beschreibung möglicher Rückgabewerte finden Sie unter [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance) im Windows SDK.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie die erste Überladung dieser Funktion für die typische Objekterstellung. Verwenden Sie die zweite Überladung, wenn Sie das zu erstellende Objekt aggregieren müssen.

Die ATL-Klasse, die das erforderliche COM-Objekt implementiert (d. h. die Klasse, die als erster Vorlagenparameter für [CComCoClass](../../atl/reference/ccomcoclass-class.md)verwendet wird), muss sich im selben Projekt wie der aufrufende Code befinden. Die Erstellung des COM-Objekts wird von der für diese ATL-Klasse registrierten Klassenfactory durchgeführt.

Diese Funktionen sind nützlich zum Erstellen von Objekten, die Sie mithilfe des [Makros OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto) verhindert haben. Sie sind auch in Situationen nützlich, in denen Sie die COM-API aus Gründen der Effizienz vermeiden möchten.

Beachten Sie, dass der Schnittstelle *Q* eine IID zugeordnet sein muss, die mit dem [Operator __uuidof](../../cpp/uuidof-operator.md) abgerufen werden kann.

### <a name="example"></a>Beispiel

Im folgenden Beispiel `CDocument` wird eine vom Assistenten generierte ATL-Klasse verwendet, die von `CComCoClass` der `IDocument` Schnittstelle abgeleitet wird. Die Klasse wird in der Objektzuordnung mit dem OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO Makro registriert, sodass Clients keine Instanzen des Dokuments mit [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)erstellen können. `CApplication`ist eine CoClass, die eine Methode auf einer ihrer eigenen COM-Schnittstellen bereitstellt, um Instanzen der Dokumentklasse zu erstellen. Der folgende Code zeigt, wie einfach es ist, Instanzen der Dokumentklasse mit dem member zu erstellen, der `CreateInstance` von der `CComCoClass` Basisklasse geerbt wurde.

[!code-cpp[NVC_ATL_COM#11](../../atl/codesnippet/cpp/ccomcoclass-class_2.cpp)]

## <a name="ccomcoclasserror"></a><a name="error"></a>CComCoClass::Fehler

Diese statische Funktion `IErrorInfo` richtet die Schnittstelle ein, um dem Client Fehlerinformationen bereitzustellen.

```
static HRESULT WINAPI Error(
    LPCOLESTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    LPCOLESTR lpszDesc,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    LPCSTR lpszDesc,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    LPCSTR lpszDesc,
    DWORD dwHelpID,
    LPCSTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0);

static HRESULT WINAPI Error(
    UINT nID,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance ());

static HRESULT Error(
    UINT nID,
    DWORD dwHelpID,
    LPCOLESTR lpszHelpFile,
    const IID& iid = GUID_NULL,
    HRESULT hRes = 0,
    HINSTANCE hInst = _AtlBaseModule.GetResourceInstance());
```

### <a name="parameters"></a>Parameter

*lpszDesc*<br/>
[in] Die Zeichenfolge, die den Fehler beschreibt. Die Unicode-Version von `Error` gibt an, dass *lpszDesc* vom Typ LPCOLESTR ist. Die ANSI-Version gibt einen LPCSTR-Typ an.

*Iid*<br/>
[in] Die IID der Schnittstelle, die den Fehler oder GUID_NULL (Standardwert) definiert, wenn der Fehler vom Betriebssystem definiert wird.

*hRes*<br/>
[in] Das HRESULT, das an den Aufrufer zurückgegeben werden soll. Der Standardwert ist 0. Weitere Informationen zu *hRes*finden Sie unter Bemerkungen.

*nID*<br/>
[in] Der Ressourcenbezeichner, in dem die Fehlerbeschreibungszeichenfolge gespeichert ist. Dieser Wert sollte zwischen 0x0200 und 0xFFFF liegen, einschließlich. In Debugbuilds wird ein **ASSERT** resultiert, wenn *nID* keine gültige Zeichenfolge indiziert. In Releasebuilds wird die Fehlerbeschreibungszeichenfolge auf "Unbekannter Fehler" festgelegt.

*dwHelpID*<br/>
[in] Der Hilfekontextbezeichner für den Fehler.

*lpszHelpFile*<br/>
[in] Der Pfad und der Name der Hilfedatei, die den Fehler beschreibt.

*hInst*<br/>
[in] Das Handle für die Ressource. Standardmäßig ist `_AtlModule::GetResourceInstance`dieser Parameter `_AtlModule` , wobei sich die globale Instanz von [CAtlModule](../../atl/reference/catlmodule-class.md)befindet.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert. Einzelheiten finden Sie unter "Hinweise".

### <a name="remarks"></a>Bemerkungen

Zum `Error`Aufrufen muss das `ISupportErrorInfo Interface` Objekt die Schnittstelle implementieren.

Wenn der *hRes-Parameter* ungleich Null ist, gibt er `Error` den Wert von *hRes*zurück. Wenn *hRes* Null ist, werden `Error` die ersten vier Versionen von return DISP_E_EXCEPTION. Die letzten beiden Versionen geben das Ergebnis des Makros **zurück MAKE_HRESULT( 1, FACILITY_ITF,** *nID* **)**.

## <a name="ccomcoclassgetobjectclsid"></a><a name="getobjectclsid"></a>CComCoClass::GetObjectCLSID

Bietet eine konsistente Möglichkeit zum Abrufen der CLSID des Objekts.

```
static const CLSID& WINAPI GetObjectCLSID();
```

### <a name="return-value"></a>Rückgabewert

Der Klassenbezeichner des Objekts.

## <a name="ccomcoclassgetobjectdescription"></a><a name="getobjectdescription"></a>CComCoClass::GetObjectDescription

Diese statische Funktion ruft die Textbeschreibung für Ihr Klassenobjekt ab.

```
static LPCTSTR WINAPI GetObjectDescription();
```

### <a name="return-value"></a>Rückgabewert

Die Beschreibung des Klassenobjekts.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung gibt NULL zurück. Sie können diese Methode mit dem [DECLARE_OBJECT_DESCRIPTION-Makro](object-map-macros.md#declare_object_description) überschreiben. Beispiel:

[!code-cpp[NVC_ATL_COM#12](../../atl/codesnippet/cpp/ccomcoclass-class_3.h)]

`GetObjectDescription`wird von `IComponentRegistrar::GetComponents`aufgerufen. `IComponentRegistrar`ist eine Automatisierungsschnittstelle, mit der Sie einzelne Komponenten in einer DLL registrieren und aufheben können. Wenn Sie ein Component-Registrar-Objekt mit dem ATL-Projekt-Assistenten erstellen, implementiert der Assistent die `IComponentRegistrar` Schnittstelle automatisch. `IComponentRegistrar`wird in der Regel von Microsoft Transaction Server verwendet.

Weitere Informationen zum ATL-Projekt-Assistenten finden Sie im Artikel [Erstellen eines ATL-Projekts](../../atl/reference/creating-an-atl-project.md).

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)
