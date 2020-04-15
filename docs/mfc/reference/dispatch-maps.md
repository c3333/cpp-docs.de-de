---
title: Dispatchzuordnungen
ms.date: 06/20/2018
helpviewer_keywords:
- dispatch maps [MFC], macros
- dispatch maps [MFC]
- dispatch map macros [MFC]
ms.assetid: bef9d08b-ad35-4c3a-99d8-04150c7c04e2
ms.openlocfilehash: 59dd8c7a7b0b930ffdb68fd96410fd73aeb02e81
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365758"
---
# <a name="dispatch-maps"></a>Dispatchzuordnungen

OLE Automation bietet Möglichkeiten zum Aufrufen von Methoden und zum Zugriff auf Eigenschaften über Anwendungen hinweg. Der von der Microsoft Foundation-Klassenbibliothek bereitgestellte Mechanismus zum Versenden dieser Anforderungen ist die "Dispatch-Map", die die internen und externen Namen von Objektfunktionen und -eigenschaften sowie die Datentypen der Eigenschaften selbst und der Funktionsargumente kennzeichnet.

|Dispatch-Map-Makro|BESCHREIBUNG|
|-|-|
|[DECLARE_DISPATCH_MAP](#declare_dispatch_map)|Deklariert, dass eine Dispatchzuordnung verwendet wird, um die Methoden und Eigenschaften einer Klasse verfügbar zu machen (muss in der Klassendeklaration verwendet werden).|
|[BEGIN_DISPATCH_MAP](#begin_dispatch_map)|Startet die Definition einer Dispatchzuordnung.|
|[END_DISPATCH_MAP](#end_dispatch_map)|Beendet die Definition einer Dispatchzuordnung.|
|[DISP_FUNCTION](#disp_function)|Wird in einer Dispatchzuordnung verwendet, um eine OLE-Automatisierungsfunktion zu definieren.|
|[DISP_PROPERTY](#disp_property)|Definiert eine OLE-Automatisierungseigenschaft.|
|[DISP_PROPERTY_EX](#disp_property_ex)|Definiert eine OLE-Automatisierungseigenschaft und benennt die Get- und Set-Funktionen.|
|[DISP_PROPERTY_NOTIFY](#disp_property_notify)|Definiert eine OLE-Automatisierungseigenschaft mit Benachrichtigung.|
|[DISP_PROPERTY_PARAM](#disp_property_param)|Definiert eine OLE-Automatisierungseigenschaft, die Parameter annimmt und die Get- und Set-Funktionen benennt.|
|[DISP_DEFVALUE](#disp_defvalue)|Macht eine vorhandene Eigenschaft zum Standardwert eines Objekts.|

## <a name="declare_dispatch_map"></a><a name="declare_dispatch_map"></a>DECLARE_DISPATCH_MAP

Wenn `CCmdTarget`eine -derived-Klasse in Ihrem Programm OLE Automation unterstützt, muss diese Klasse eine Dispatchzuordnung bereitstellen, um ihre Methoden und Eigenschaften verfügbar zu machen.

```cpp
DECLARE_DISPATCH_MAP()
```

### <a name="remarks"></a>Bemerkungen

Verwenden Sie das DECLARE_DISPATCH_MAP-Makro am Ende der Klassendeklaration. Dann, in der . CPP-Datei, die die Memberfunktionen für die Klasse definiert, verwenden Sie die BEGIN_DISPATCH_MAP Makro. Fügen Sie dann Makroeinträge für jede der verfügbar gemachten Methoden und Eigenschaften Ihrer Klasse ein (DISP_FUNCTION, DISP_PROPERTY usw.). Verwenden Sie schließlich das END_DISPATCH_MAP-Makro.

> [!NOTE]
> Wenn Sie Mitglieder nach DECLARE_DISPATCH_MAP deklarieren, müssen Sie für sie einen neuen Zugriffstyp ( **öffentlich**, **privat**oder **geschützt**) angeben.

Der Anwendungs-Assistent und die Code-Assistenten unterstützen das Erstellen von Automatisierungsklassen und das Verwalten von Dispatchzuordnungen. Weitere Informationen zu Dispatch-Maps finden Sie unter [Automatisierungsserver](../../mfc/automation-servers.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCAutomation#10](../../mfc/codesnippet/cpp/dispatch-maps_1.h)]

### <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="begin_dispatch_map"></a><a name="begin_dispatch_map"></a>BEGIN_DISPATCH_MAP

Deklariert die Definition Ihrer Dispatch-Map.

```cpp
BEGIN_DISPATCH_MAP(theClass, baseClass)
```

### <a name="parameters"></a>Parameter

*theClass*<br/>
Gibt den Namen der Klasse an, die diese Dispatchzuordnung besitzt.

*Baseclass*<br/>
Gibt den Basisklassennamen *derKlasse*an.

### <a name="remarks"></a>Bemerkungen

Starten Sie in der Implementierungsdatei (.cpp), die die Memberfunktionen für Ihre Klasse definiert, die Dispatch-Zuordnung mit dem BEGIN_DISPATCH_MAP-Makro, fügen Sie Makroeinträge für jede Ihrer Dispatch-Funktionen und -Eigenschaften hinzu, und schließen Sie die Dispatch-Zuordnung mit dem END_DISPATCH_MAP-Makro ab.

### <a name="requirements"></a>Anforderungen

**Header:** afxdisp.h

## <a name="end_dispatch_map"></a><a name="end_dispatch_map"></a>END_DISPATCH_MAP

Beendet die Definition der Dispatch-Map.

```cpp
END_DISPATCH_MAP()
```

### <a name="remarks"></a>Bemerkungen

Es muss in Verbindung mit BEGIN_DISPATCH_MAP verwendet werden.

### <a name="requirements"></a>Anforderungen

**Header:** afxdisp.h

## <a name="disp_function"></a><a name="disp_function"></a>DISP_FUNCTION

Definiert eine OLE-Automatisierungsfunktion in einer Dispatchzuordnung.

```cpp
DISP_FUNCTION(
    theClass,
    pszName,
    pfnMember,
    vtRetVal,
    vtsParams)
```

### <a name="parameters"></a>Parameter

*theClass*<br/>
Name der Klasse.

*pszName*<br/>
Externer Name der Funktion.

*pfnMember*<br/>
Name der Memberfunktion.

*vtRetVal*<br/>
Ein Wert, der den Rückgabetyp der Funktion angibt.

*vtsParams*<br/>
Eine durch Leerzeichen getrennte Liste einer oder mehrerer Konstanten, die die Parameterliste der Funktion angeben.

### <a name="remarks"></a>Bemerkungen

Das Argument *vtRetVal* ist vom Typ VARTYPE. Die folgenden möglichen Werte für dieses `VARENUM` Argument werden der Enumeration entnommen:

|Symbol|Rückgabetyp|
|------------|-----------------|
|VT_EMPTY|**void**|
|VT_I2|**short**|
|VT_I4|**Lange**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATE|
|VT_BSTR|BSTR|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

Das Argument *vtsParams* ist eine durch Leerzeichen getrennte Liste von Werten aus den `VTS_*` Konstanten. Mindestens einer dieser Werte, die durch Leerzeichen (keine Kommas) getrennt sind, gibt die Parameterliste der Funktion an. Beispiel:

[!code-cpp[NVC_MFCAutomation#14](../../mfc/codesnippet/cpp/dispatch-maps_2.cpp)]

gibt eine Liste an, die eine kurze ganze Zahl gefolgt von einem Zeiger auf eine kurze ganze Zahl enthält.

Die `VTS_` Konstanten und ihre Bedeutungen sind wie folgt:

|Symbol|Parametertyp|
|------------|--------------------|
|VTS_I2|**short**|
|VTS_I4|**Lange**|
|VTS_R4|**float**|
|VTS_R8|**double**|
|VTS_CY|`const CY` oder `CY*`|
|VTS_DATE|DATE|
|VTS_BSTR|LPCSTR|
|VTS_DISPATCH|LPDISPATCH|
|VTS_SCODE|SCODE|
|VTS_BOOL|BOOL|
|VTS_VARIANT|`const VARIANT*` oder `VARIANT&`|
|VTS_UNKNOWN|LPUNKNOWN|
|VTS_PI2|__kurz\*__|
|VTS_PI4|__Lange\*__|
|VTS_PR4|__float\*__|
|VTS_PR8|__Doppel\*__|
|VTS_PCY|`CY*`|
|VTS_PDATE|`DATE*`|
|VTS_PBSTR|`BSTR*`|
|VTS_PDISPATCH|`LPDISPATCH*`|
|VTS_PSCODE|`SCODE*`|
|VTS_PBOOL|`BOOL*`|
|VTS_PVARIANT|`VARIANT*`|
|VTS_PUNKNOWN|`LPUNKNOWN*`|
|VTS_NONE|Keine Parameter|

### <a name="requirements"></a>Anforderungen

**Header:** afxdisp.h

## <a name="disp_property"></a><a name="disp_property"></a>DISP_PROPERTY

Definiert eine OLE-Automatisierungseigenschaft in einer Dispatchzuordnung.

```cpp
DISP_PROPERTY(
    theClass,
    pszName,
    memberName,
    vtPropType)
```

### <a name="parameters"></a>Parameter

*theClass*<br/>
Name der Klasse.

*pszName*<br/>
Externer Name der Eigenschaft.

*Membername*<br/>
Name der Membervariablen, in der die Eigenschaft gespeichert ist.

*vtPropType*<br/>
Ein Wert, der den Typ der Eigenschaft angibt.

### <a name="remarks"></a>Bemerkungen

Das *Argument vtPropType* ist vom Typ **VARTYPE**. Mögliche Werte für dieses Argument stammen aus der VARENUM-Enumeration:

|Symbol|Eigenschaftstyp|
|------------|-----------------------|
|VT_I2|**short**|
|VT_I4|**Lange**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATE|
|VT_BSTR|`CString`|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

Wenn ein externer Client die Eigenschaft ändert, ändert sich der Wert der Membervariablen, die durch *memberName* angegeben wird. Es gibt keine Benachrichtigung über die Änderung.

### <a name="requirements"></a>Anforderungen

**Header:** afxdisp.h

## <a name="disp_property_ex"></a><a name="disp_property_ex"></a>DISP_PROPERTY_EX

Definiert eine OLE-Automatisierungseigenschaft und nennt die Funktionen, die zum Abrufen und Festlegen des Eigenschaftswerts in einer Dispatchzuordnung verwendet werden.

```cpp
DISP_PROPERTY_EX(
    theClass,
    pszName,
    memberGet,
    memberSet,
    vtPropType)
```

### <a name="parameters"></a>Parameter

*theClass*<br/>
Name der Klasse.

*pszName*<br/>
Externer Name der Eigenschaft.

*MemberGet*<br/>
Name der Memberfunktion, die zum Abrufen der Eigenschaft verwendet wird.

*memberSet*<br/>
Name der Memberfunktion, die zum Festlegen der Eigenschaft verwendet wird.

*vtPropType*<br/>
Ein Wert, der den Typ der Eigenschaft angibt.

### <a name="remarks"></a>Bemerkungen

Die *MemberGet-* und *memberSet-Funktionen* verfügen über Signaturen, die durch das *Argument vtPropType* bestimmt werden. Die *memberGet-Funktion* nimmt keine Argumente und gibt einen Wert des von *vtPropType*angegebenen Typs zurück. Die *memberSet-Funktion* nimmt ein Argument des von *vtPropType* angegebenen Typs und gibt nichts zurück.

Das *Argument vtPropType* ist vom Typ VARTYPE. Mögliche Werte für dieses Argument stammen aus der VARENUMeration. Eine Liste dieser Werte finden Sie unter Hinweise zum Parameter *vtRetVal* in [DISP_FUNCTION](#disp_function). Beachten Sie, dass VT_EMPTY, die in den DISP_FUNCTION Bemerkungen aufgeführt sind, nicht als Eigenschaftsdatentyp zulässig ist.

### <a name="requirements"></a>Anforderungen

**Header:** afxdisp.h

## <a name="disp_property_notify"></a><a name="disp_property_notify"></a>DISP_PROPERTY_NOTIFY

Definiert eine OLE-Automatisierungseigenschaft mit Benachrichtigung in einer Dispatchzuordnung.

```cpp
DISP_PROPERTY_NOTIFY(
    theClass,
    szExternalName,
    memberName,
    pfnAfterSet,
    vtPropType)
```

### <a name="parameters"></a>Parameter

*theClass*<br/>
Name der Klasse.

*szExternalName*<br/>
Externer Name der Eigenschaft.

*Membername*<br/>
Name der Membervariablen, in der die Eigenschaft gespeichert ist.

*pfnAfterSet*<br/>
Name der Benachrichtigungsfunktion für *szExternalName*.

*vtPropType*<br/>
Ein Wert, der den Typ der Eigenschaft angibt.

### <a name="remarks"></a>Bemerkungen

Im Gegensatz zu Eigenschaften, die mit DISP_PROPERTY definiert sind, ruft eine mit DISP_PROPERTY_NOTIFY definierte Eigenschaft automatisch die von *pfnAfterSet* angegebene Funktion auf, wenn die Eigenschaft geändert wird.

Das *Argument vtPropType* ist vom Typ VARTYPE. Mögliche Werte für dieses Argument stammen aus der VARENUM-Enumeration:

|Symbol|Eigenschaftstyp|
|------------|-----------------------|
|VT_I2|**short**|
|VT_I4|**Lange**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATE|
|VT_BSTR|`CString`|
|VT_DISPATCH|LPDISPATCH|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

### <a name="requirements"></a>Anforderungen

**Header:** afxdisp.h

## <a name="disp_property_param"></a><a name="disp_property_param"></a>DISP_PROPERTY_PARAM

Definiert eine Eigenschaft, `Get` auf `Set` die mit separaten und Memberfunktionen zugegriffen wird.

```cpp
DISP_PROPERTY_PARAM(
    theClass,
    pszExternalName,
    pfnGet,
    pfnSet,
    vtPropType,
    vtsParams)
```

### <a name="parameters"></a>Parameter

*theClass*<br/>
Name der Klasse.

*pszExternalName*<br/>
Externer Name der Eigenschaft.

*pfnGet*<br/>
Name der Memberfunktion, die zum Abrufen der Eigenschaft verwendet wird.

*pfnSet*<br/>
Name der Memberfunktion, die zum Festlegen der Eigenschaft verwendet wird.

*vtPropType*<br/>
Ein Wert, der den Typ der Eigenschaft angibt.

*vtsParams*<br/>
Eine Zeichenfolge von `VTS_*` leer getrennten Variantenparametertypen, eine für jeden Parameter.

### <a name="remarks"></a>Bemerkungen

Im Gegensatz zum DISP_PROPERTY_EX Makro können Sie mit diesem Makro eine Parameterliste für die Eigenschaft angeben. Dies ist nützlich, um Eigenschaften zu implementieren, die indiziert oder parametrisiert sind.

### <a name="example"></a>Beispiel

Betrachten Sie die folgende Deklaration von get- und set-Memberfunktionen, die es dem Benutzer ermöglichen, beim Zugriff auf die Eigenschaft eine bestimmte Zeile und Spalte anzufordern:

[!code-cpp[NVC_MFCActiveXControl#9](../../mfc/codesnippet/cpp/dispatch-maps_3.h)]

Diese entsprechen den folgenden DISP_PROPERTY_PARAM Makros in der Kontrolldispatchzuordnung:

[!code-cpp[NVC_MFCActiveXControl#10](../../mfc/codesnippet/cpp/dispatch-maps_4.cpp)]

Als weiteres Beispiel betrachten Sie die folgenden get- und set-Memberfunktionen:

[!code-cpp[NVC_MFCActiveXControl#11](../../mfc/codesnippet/cpp/dispatch-maps_5.h)]

Diese entsprechen den folgenden DISP_PROPERTY_PARAM Makros in der Kontrolldispatchzuordnung:

[!code-cpp[NVC_MFCActiveXControl#12](../../mfc/codesnippet/cpp/dispatch-maps_6.cpp)]

### <a name="requirements"></a>Anforderungen

**Header:** afxdisp.h

## <a name="disp_defvalue"></a><a name="disp_defvalue"></a>DISP_DEFVALUE

Macht eine vorhandene Eigenschaft zum Standardwert eines Objekts.

```cpp
DISP_DEFVALUE(theClass, pszName)
```

### <a name="parameters"></a>Parameter

*theClass*<br/>
Name der Klasse.

*pszName*<br/>
Externer Name der Eigenschaft, die den "Wert" des Objekts darstellt.

### <a name="remarks"></a>Bemerkungen

Die Verwendung eines Standardwerts kann die Programmierung Ihres Automatisierungsobjekts für Visual Basic-Anwendungen vereinfachen.

Der "Standardwert" Ihres Objekts ist die Eigenschaft, die abgerufen oder festgelegt wird, wenn ein Verweis auf ein Objekt keine Eigenschaft oder Memberfunktion angibt.

### <a name="requirements"></a>Anforderungen

**Header:** afxdisp.h

## <a name="see-also"></a>Siehe auch

[MFC-Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md)
