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
ms.openlocfilehash: 5b4e39fa4d93893d288bb8de03d8a71b671be087
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78863188"
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
Die von `CComCoClass`abgeleitete Klasse.

*pclsid*<br/>
Ein Zeiger auf die CLSID des Objekts.

## <a name="members"></a>Members

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComCoClass:: kreateinzustance](#createinstance)|Kum Erstellt eine Instanz der-Klasse und fragt eine-Schnittstelle ab.|
|[CComCoClass:: Error](#error)|Kum Gibt umfangreiche Fehlerinformationen an den Client zurück.|
|[CComCoClass:: GetObjectCLSID](#getobjectclsid)|Kum Gibt den Klassen Bezeichner des-Objekts zurück.|
|[CComCoClass:: getobjectdescription](#getobjectdescription)|Kum Überschreiben, um die Beschreibung des Objekts zurückzugeben.|

## <a name="remarks"></a>Bemerkungen

`CComCoClass` stellt Methoden zum Abrufen der CLSID eines Objekts, zum Festlegen von Fehlerinformationen und zum Erstellen von Instanzen der-Klasse bereit. Jede Klasse, die in der Objekt Zuordnung registriert ist, sollte von `CComCoClass`abgeleitet werden.

`CComCoClass` definiert auch die Standardklassenfactory und das Aggregations Modell für Ihr Objekt. `CComCoClass` verwendet die folgenden beiden Makros:

- [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory) Deklariert die Klassenfactory als [CComClassFactory](../../atl/reference/ccomclassfactory-class.md).

- [DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable) Deklariert, dass das Objekt aggregiert werden kann.

Sie können diese Standardeinstellungen überschreiben, indem Sie in der Klassendefinition ein anderes Makro angeben. Wenn Sie z. b. [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md) anstelle von `CComClassFactory`verwenden möchten, geben Sie das [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) -Makro an:

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomcoclass-class_1.h)]

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Atlcom. h

##  <a name="createinstance"></a>CComCoClass:: kreateinzustance

Verwenden Sie diese `CreateInstance` Funktionen, um eine Instanz eines COM-Objekts zu erstellen und einen Schnittstellen Zeiger abzurufen, ohne die com-API zu verwenden.

```
template <class  Q>
static HRESULT CreateInstance( Q** pp);

template <class  Q>
static HRESULT CreateInstance(IUnknown* punkOuter, Q** pp);
```

### <a name="parameters"></a>Parameter

*Q*<br/>
Die COM-Schnittstelle, die über *PP*zurückgegeben werden soll.

*punkOuter*<br/>
in Das äußere unbekannte oder kontrollierende unbekannte des Aggregats.

*Trupp*<br/>
vorgenommen Die Adresse einer Zeiger Variablen, die den angeforderten Schnittstellen Zeiger empfängt, wenn die Erstellung erfolgreich ist.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert. Eine Beschreibung möglicher Rückgabewerte finden Sie unter [cokreateingestance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance) im Windows SDK.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie die erste Überladung dieser Funktion für die typische Objekt Erstellung. Verwenden Sie die zweite Überladung, wenn Sie das zu erstellende Objekt aggregieren müssen.

Die ATL-Klasse, die das erforderliche com-Objekt implementiert (d. h. die-Klasse, die als erster Vorlagen Parameter für [CComCoClass](../../atl/reference/ccomcoclass-class.md)verwendet wird), muss sich im gleichen Projekt wie der aufrufende Code befinden. Die Erstellung des COM-Objekts wird von der Klassenfactory durchgeführt, die für diese ATL-Klasse registriert ist.

Diese Funktionen sind nützlich zum Erstellen von Objekten, die durch die Verwendung des [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto) -Makros verhindert haben, dass Sie extern erstellt werden können. Sie sind auch in Situationen nützlich, in denen Sie die com-API aus Gründen der Effizienz vermeiden möchten.

Beachten Sie, dass der *Q* -Schnittstelle eine IID zugeordnet sein muss, die mit dem [__uuidof](../../cpp/uuidof-operator.md) -Operator abgerufen werden kann.

### <a name="example"></a>Beispiel

Im folgenden Beispiel ist `CDocument` eine vom Assistenten generierte ATL-Klasse, die von `CComCoClass` abgeleitet wird, der die `IDocument`-Schnittstelle implementiert. Die-Klasse wird in der Objekt Zuordnung mit dem OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO-Makro registriert, sodass Clients keine Instanzen des Dokuments mithilfe von [cokreateinstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)erstellen können. `CApplication` ist eine Co-Klasse, die eine Methode für eine ihrer eigenen COM-Schnittstellen bereitstellt, um Instanzen der Document-Klasse zu erstellen. Der folgende Code zeigt, wie einfach es ist, Instanzen der Document-Klasse mit dem `CreateInstance` Member zu erstellen, der von der `CComCoClass`-Basisklasse geerbt wurde.

[!code-cpp[NVC_ATL_COM#11](../../atl/codesnippet/cpp/ccomcoclass-class_2.cpp)]

##  <a name="error"></a>CComCoClass:: Error

Diese statische Funktion richtet die `IErrorInfo`-Schnittstelle ein, um dem Client Fehlerinformationen bereitzustellen.

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

*lpszde*<br/>
in Die Zeichenfolge, die den Fehler beschreibt. Die Unicode-Version von `Error` gibt an, dass *lpszdesc* vom Typ lpcolestr ist. die ANSI-Version gibt den LPCSTR-Typ an.

*IID*<br/>
in Die IID der Schnittstelle, die den Fehler definiert, oder GUID_NULL (Standardwert), wenn der Fehler vom Betriebssystem definiert wird.

*hres*<br/>
in Das HRESULT, das an den Aufrufer zurückgegeben werden soll. Der Standardwert ist 0. Weitere Informationen zu *hres*finden Sie unter "Hinweise".

*NID*<br/>
in Der Ressourcen Bezeichner, in dem die Zeichenfolge zur Fehlerbeschreibung gespeichert wird. Dieser Wert sollte zwischen 0x0200 und 0xFFFF (einschließlich) liegen. In Debugbuilds ergibt sich eine **Assert** -Bestätigung, wenn *NID* keine gültige Zeichenfolge indiziert. In Releasebuilds wird die Fehler Beschreibungs Zeichenfolge auf "Unbekannter Fehler" festgelegt.

*dwhelpid*<br/>
in Der Hilfe Kontext Bezeichner für den Fehler.

*lpszhelpfile*<br/>
in Der Pfad und der Name der Hilfedatei, die den Fehler beschreibt.

*hinst*<br/>
in Das Handle für die Ressource. Standardmäßig ist dieser Parameter `_AtlModule::GetResourceInstance`, wobei `_AtlModule` die globale [Instanz von "](../../atl/reference/catlmodule-class.md)".

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert. Einzelheiten finden Sie unter "Hinweise".

### <a name="remarks"></a>Bemerkungen

Um `Error`aufzurufen, muss das-Objekt die `ISupportErrorInfo Interface`-Schnittstelle implementieren.

Wenn der *hres* -Parameter ungleich NULL ist, gibt `Error` den Wert von *hres*zurück. Wenn *hres* NULL ist, geben die ersten vier Versionen von `Error` DISP_E_EXCEPTION zurück. Die letzten beiden Versionen geben das Ergebnis des Makros **MAKE_HRESULT (1, FACILITY_ITF,** *NID* **)** zurück.

##  <a name="getobjectclsid"></a>CComCoClass:: GetObjectCLSID

Bietet eine konsistente Methode zum Abrufen der CLSID des Objekts.

```
static const CLSID& WINAPI GetObjectCLSID();
```

### <a name="return-value"></a>Rückgabewert

Der Klassen Bezeichner des Objekts.

##  <a name="getobjectdescription"></a>CComCoClass:: getobjectdescription

Diese statische Funktion Ruft die Textbeschreibung für das Klassenobjekt ab.

```
static LPCTSTR WINAPI GetObjectDescription();
```

### <a name="return-value"></a>Rückgabewert

Die Beschreibung des Klassen Objekts.

### <a name="remarks"></a>Bemerkungen

Die Standard Implementierung gibt NULL zurück. Sie können diese Methode mit dem [DECLARE_OBJECT_DESCRIPTION](object-map-macros.md#declare_object_description) -Makro überschreiben. Beispiel:

[!code-cpp[NVC_ATL_COM#12](../../atl/codesnippet/cpp/ccomcoclass-class_3.h)]

`GetObjectDescription` wird von `IComponentRegistrar::GetComponents`aufgerufen. `IComponentRegistrar` ist eine Automatisierungsschnittstelle, mit der Sie einzelne Komponenten in einer DLL registrieren und deren Registrierung aufheben können. Wenn Sie ein komponentenregistrierungs Objekt mit dem ATL-Projekt-Assistenten erstellen, wird die `IComponentRegistrar`-Schnittstelle automatisch vom Assistenten implementiert. `IComponentRegistrar` wird in der Regel von Microsoft Transaction Server verwendet.

Weitere Informationen zum ATL-Projekt-Assistenten finden Sie im Artikel [Erstellen eines ATL-Projekts](../../atl/reference/creating-an-atl-project.md).

## <a name="see-also"></a>Weitere Informationen

[Klassen Übersicht](../../atl/atl-class-overview.md)
