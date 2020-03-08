---
title: Dispatchzuordnungen
ms.date: 06/20/2018
helpviewer_keywords:
- dispatch maps [MFC], macros
- dispatch maps [MFC]
- dispatch map macros [MFC]
ms.assetid: bef9d08b-ad35-4c3a-99d8-04150c7c04e2
ms.openlocfilehash: f1afa95d7c20d54f2015255a7e4e0d7ad9ae9c2b
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856649"
---
# <a name="dispatch-maps"></a>Dispatchzuordnungen

OLE-Automatisierung bietet Möglichkeiten zum Aufrufen von Methoden und zum Zugreifen auf Eigenschaften über Anwendungen hinweg. Der Mechanismus, der vom Microsoft Foundation Class-Bibliothek zum Verteilen dieser Anforderungen bereitgestellt wird, ist die "dispatchmap", die die internen und externen Namen von Objektfunktionen und-Eigenschaften sowie die Datentypen der Eigenschaften selbst und von angibt. Funktionsargumente.

|Dispatch-Zuordnungs Makro|BESCHREIBUNG|
|-|-|
|[DECLARE_DISPATCH_MAP](#declare_dispatch_map)|Deklariert, dass eine dispatchmap verwendet wird, um die Methoden und Eigenschaften einer Klasse verfügbar zu machen (muss in der Klassen Deklaration verwendet werden).|
|[BEGIN_DISPATCH_MAP](#begin_dispatch_map)|Startet die Definition einer Dispatchzuordnung.|
|[END_DISPATCH_MAP](#end_dispatch_map)|Beendet die Definition einer Dispatchzuordnung.|
|[DISP_FUNCTION](#disp_function)|Wird in einer Dispatchzuordnung verwendet, um eine OLE-Automatisierungsfunktion zu definieren.|
|[DISP_PROPERTY](#disp_property)|Definiert eine OLE-Automatisierungs Eigenschaft.|
|[DISP_PROPERTY_EX](#disp_property_ex)|Definiert eine OLE-Automatisierungs Eigenschaft und benennt die Get-und Set-Funktionen.|
|[DISP_PROPERTY_NOTIFY](#disp_property_notify)|Definiert eine OLE-Automatisierungs Eigenschaft mit Benachrichtigung.|
|[DISP_PROPERTY_PARAM](#disp_property_param)|Definiert eine OLE-Automatisierungs Eigenschaft, die Parameter annimmt und die Get-und Set-Funktionen benennt.|
|[DISP_DEFVALUE](#disp_defvalue)|Erstellt eine vorhandene Eigenschaft als Standardwert eines Objekts.|

## <a name="declare_dispatch_map"></a>DECLARE_DISPATCH_MAP

Wenn eine von `CCmdTarget`abgeleitete Klasse in Ihrem Programm OLE-Automatisierung unterstützt, muss diese Klasse eine Dispatchzuordnung bereitstellen, um die zugehörigen Methoden und Eigenschaften verfügbar zu machen.

```cpp
DECLARE_DISPATCH_MAP()
```

### <a name="remarks"></a>Bemerkungen

Verwenden Sie das DECLARE_DISPATCH_MAP-Makro am Ende der Klassen Deklaration. Klicken Sie anschließend in der auf. Cpp-Datei, die die Element Funktionen für die Klasse definiert. verwenden Sie das BEGIN_DISPATCH_MAP-Makro. Fügen Sie anschließend Makro Einträge für jede verfügbar gemachten Methoden und Eigenschaften der Klasse (DISP_FUNCTION, DISP_PROPERTY usw.) ein. Verwenden Sie abschließend das END_DISPATCH_MAP-Makro.

> [!NOTE]
> Wenn Sie nach DECLARE_DISPATCH_MAP Elemente deklarieren, müssen Sie einen neuen Zugriffstyp ( **öffentlich**, **Privat**oder **geschützt**) für Sie angeben.

Der Anwendungs-Assistent und die Code-Assistenten unterstützen Sie beim Erstellen von Automatisierungs Klassen und bei der Verwaltung von Dispatch Weitere Informationen zu dispatchmaps finden Sie unter [Automation Servers (Automatisierungsserver](../../mfc/automation-servers.md)).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCAutomation#10](../../mfc/codesnippet/cpp/dispatch-maps_1.h)]

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxwin.h

## <a name="begin_dispatch_map"></a>BEGIN_DISPATCH_MAP

Deklariert die Definition ihrer Dispatchzuordnung.

```cpp
BEGIN_DISPATCH_MAP(theClass, baseClass)
```

### <a name="parameters"></a>Parameter

*spiegeln*<br/>
Gibt den Namen der Klasse an, die diese Dispatchzuordnung besitzt.

*BaseClass*<br/>
Gibt den Basisklassen Namen von *TheClass*an.

### <a name="remarks"></a>Bemerkungen

Starten Sie in der Implementierungs Datei (. cpp), in der die Member-Funktionen für Ihre Klasse definiert sind, die Dispatchzuordnung mit dem BEGIN_DISPATCH_MAP-Makro, fügen Sie Makro Einträge für die einzelnen dispatchfunktionen und-Eigenschaften hinzu, und vervollständigen Sie die Dispatchzuordnung mit dem END_DISPATCH_ Map-Makro.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdisp.h

## <a name="end_dispatch_map"></a>END_DISPATCH_MAP

Beendet die Definition ihrer Dispatchzuordnung.

```cpp
END_DISPATCH_MAP()
```

### <a name="remarks"></a>Bemerkungen

Er muss in Verbindung mit BEGIN_DISPATCH_MAP verwendet werden.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdisp.h

## <a name="disp_function"></a>DISP_FUNCTION

Definiert eine OLE-Automatisierungsfunktion in einer dispatchmap.

```cpp
DISP_FUNCTION(
    theClass,
    pszName,
    pfnMember,
    vtRetVal,
    vtsParams)
```

### <a name="parameters"></a>Parameter

*spiegeln*<br/>
Name der Klasse.

*pszName*<br/>
Externer Name der Funktion.

*pfnmember*<br/>
Der Name der Member-Funktion.

*vtretval*<br/>
Ein-Wert, der den Rückgabetyp der Funktion angibt.

*vtsParams*<br/>
Eine durch Leerzeichen getrennte Liste von einer oder mehreren Konstanten, die die Parameterliste der Funktion angeben.

### <a name="remarks"></a>Bemerkungen

Das *vtretval* -Argument weist den Typ VarType auf. Die folgenden möglichen Werte für dieses Argument werden aus der `VARENUM`-Enumeration entnommen:

|Symbol|Rückgabetyp|
|------------|-----------------|
|VT_EMPTY|**void**|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATE|
|VT_BSTR|BSTR|
|VT_DISPATCH|Lpdispatch|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

Das *vtsParams* -Argument ist eine durch Leerzeichen getrennte Liste mit Werten aus den `VTS_*` Konstanten. Einer oder mehrere dieser Werte, getrennt durch Leerzeichen (nicht Kommas), gibt die Parameterliste der Funktion an. Beispiel:

[!code-cpp[NVC_MFCAutomation#14](../../mfc/codesnippet/cpp/dispatch-maps_2.cpp)]

gibt eine Liste mit einer kurzen Ganzzahl an, gefolgt von einem Zeiger auf eine kurze Ganzzahl.

Die `VTS_` Konstanten und ihre Bedeutungen lauten wie folgt:

|Symbol|Parametertyp|
|------------|--------------------|
|VTS_I2|**short**|
|VTS_I4|**long**|
|VTS_R4|**float**|
|VTS_R8|**double**|
|VTS_CY|`const CY` oder `CY*`|
|VTS_DATE|DATE|
|VTS_BSTR|LPCSTR|
|VTS_DISPATCH|Lpdispatch|
|VTS_SCODE|SCODE|
|VTS_BOOL|BOOL|
|VTS_VARIANT|`const VARIANT*` oder `VARIANT&`|
|VTS_UNKNOWN|LPUNKNOWN|
|VTS_PI2|__kurz\*__|
|VTS_PI4|__lange\*__|
|VTS_PR4|__float-\*__|
|VTS_PR8|__doppelte\*__|
|VTS_PCY|`CY*`|
|VTS_PDATE|`DATE*`|
|VTS_PBSTR|`BSTR*`|
|VTS_PDISPATCH|`LPDISPATCH*`|
|VTS_PSCODE|`SCODE*`|
|VTS_PBOOL|`BOOL*`|
|VTS_PVARIANT|`VARIANT*`|
|VTS_PUNKNOWN|`LPUNKNOWN*`|
|VTS_NONE|Keine Parameter|

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdisp.h

## <a name="disp_property"></a>DISP_PROPERTY

Definiert eine OLE-Automatisierungs Eigenschaft in einer Dispatchzuordnung.

```cpp
DISP_PROPERTY(
    theClass,
    pszName,
    memberName,
    vtPropType)
```

### <a name="parameters"></a>Parameter

*spiegeln*<br/>
Name der Klasse.

*pszName*<br/>
Externer Name der Eigenschaft.

*Membername*<br/>
Der Name der Element Variablen, in der die Eigenschaft gespeichert wird.

*vtPropType*<br/>
Ein-Wert, der den Eigenschaftentyp angibt.

### <a name="remarks"></a>Bemerkungen

Das *vtPropType* -Argument weist den Typ **VarType**auf. Mögliche Werte für dieses Argument stammen aus der varenumeration-Enumeration:

|Symbol|Eigenschaftstyp|
|------------|-----------------------|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATE|
|VT_BSTR|`CString`|
|VT_DISPATCH|Lpdispatch|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

Wenn ein externer Client die-Eigenschaft ändert, ändert sich der Wert der Element Variablen, die durch *Mitgliedschafts Name* angegeben wird. Es gibt keine Benachrichtigung über die Änderung.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdisp.h

## <a name="disp_property_ex"></a>DISP_PROPERTY_EX

Definiert eine OLE-Automatisierungs Eigenschaft und gibt die Funktionen an, die zum erhalten und Festlegen des Eigenschafts Werts in einer Dispatchzuordnung verwendet werden.

```cpp
DISP_PROPERTY_EX(
    theClass,
    pszName,
    memberGet,
    memberSet,
    vtPropType)
```

### <a name="parameters"></a>Parameter

*spiegeln*<br/>
Name der Klasse.

*pszName*<br/>
Externer Name der Eigenschaft.

*Mitgliedschaft*<br/>
Der Name der Member-Funktion, die zum erhalten der Eigenschaft verwendet wird.

*memberSet*<br/>
Der Name der Member-Funktion, die zum Festlegen der Eigenschaft verwendet wird.

*vtPropType*<br/>
Ein-Wert, der den Eigenschaftentyp angibt.

### <a name="remarks"></a>Bemerkungen

Die *mitgliedsatz* -und *mitgliedsatz* Funktionen verfügen über Signaturen, die vom *vtPropType* -Argument bestimmt werden. Die Funktion " *Membership Get* " nimmt keine Argumente an und gibt einen Wert des Typs zurück, der von *vtPropType*angegeben wird. Die- *mitgliedsatz* Funktion nimmt ein Argument des von *vtPropType* angegebenen Typs an und gibt nichts zurück.

Das *vtPropType* -Argument weist den Typ VarType auf. Mögliche Werte für dieses Argument stammen aus der varenumeration-Enumeration. Eine Liste dieser Werte finden Sie in den Hinweisen für den *vtretval* -Parameter in [DISP_FUNCTION](#disp_function). Beachten Sie, dass VT_EMPTY, die in den DISP_FUNCTION Anmerkungen aufgeführt ist, nicht als Eigenschafts Datentyp zulässig ist.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdisp.h

## <a name="disp_property_notify"></a>DISP_PROPERTY_NOTIFY

Definiert eine OLE-Automatisierungs Eigenschaft mit Benachrichtigung in einer dispatchmap.

```cpp
DISP_PROPERTY_NOTIFY(
    theClass,
    szExternalName,
    memberName,
    pfnAfterSet,
    vtPropType)
```

### <a name="parameters"></a>Parameter

*spiegeln*<br/>
Name der Klasse.

*szexternalname*<br/>
Externer Name der Eigenschaft.

*Membername*<br/>
Der Name der Element Variablen, in der die Eigenschaft gespeichert wird.

*pfnafäterset*<br/>
Name der Benachrichtigungsfunktion für *szexternalname*.

*vtPropType*<br/>
Ein-Wert, der den Eigenschaftentyp angibt.

### <a name="remarks"></a>Bemerkungen

Anders als Eigenschaften, die mit DISP_PROPERTY definiert werden, ruft eine Eigenschaft, die mit DISP_PROPERTY_NOTIFY definiert ist, automatisch die von *pfnafterset* angegebene Funktion auf, wenn die-Eigenschaft geändert wird.

Das *vtPropType* -Argument weist den Typ VarType auf. Mögliche Werte für dieses Argument stammen aus der varenumeration-Enumeration:

|Symbol|Eigenschaftstyp|
|------------|-----------------------|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_R4|**float**|
|VT_R8|**double**|
|VT_CY|CY|
|VT_DATE|DATE|
|VT_BSTR|`CString`|
|VT_DISPATCH|Lpdispatch|
|VT_ERROR|SCODE|
|VT_BOOL|BOOL|
|VT_VARIANT|VARIANT|
|VT_UNKNOWN|LPUNKNOWN|

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdisp.h

## <a name="disp_property_param"></a>DISP_PROPERTY_PARAM

Definiert eine Eigenschaft, auf die mit separaten `Get`-und `Set` Member-Funktionen zugegriffen wird.

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

*spiegeln*<br/>
Name der Klasse.

*pszExternalName*<br/>
Externer Name der Eigenschaft.

*pfnGet*<br/>
Der Name der Member-Funktion, die zum erhalten der Eigenschaft verwendet wird.

*pfnSet*<br/>
Der Name der Member-Funktion, die zum Festlegen der Eigenschaft verwendet wird.

*vtPropType*<br/>
Ein-Wert, der den Eigenschaftentyp angibt.

*vtsParams*<br/>
Eine Zeichenfolge mit durch Leerzeichen getrennten `VTS_*` Variant-Parametertypen, eine für jeden Parameter.

### <a name="remarks"></a>Bemerkungen

Im Gegensatz zum DISP_PROPERTY_EX-Makro können Sie mit diesem Makro eine Parameterliste für die-Eigenschaft angeben. Dies ist nützlich, um indizierte oder parametrisierte Eigenschaften zu implementieren.

### <a name="example"></a>Beispiel

Beachten Sie die folgende Deklaration von Get-und Set-Member-Funktionen, die es dem Benutzer ermöglichen, beim Zugriff auf die-Eigenschaft eine bestimmte Zeile und Spalte anzufordern:

[!code-cpp[NVC_MFCActiveXControl#9](../../mfc/codesnippet/cpp/dispatch-maps_3.h)]

Diese entsprechen dem folgenden DISP_PROPERTY_PARAM-Makro in der Steuerelement dispatchkarte:

[!code-cpp[NVC_MFCActiveXControl#10](../../mfc/codesnippet/cpp/dispatch-maps_4.cpp)]

Sehen Sie sich als weiteres Beispiel die folgenden Get-und Set Member-Funktionen an:

[!code-cpp[NVC_MFCActiveXControl#11](../../mfc/codesnippet/cpp/dispatch-maps_5.h)]

Diese entsprechen dem folgenden DISP_PROPERTY_PARAM-Makro in der Steuerelement dispatchkarte:

[!code-cpp[NVC_MFCActiveXControl#12](../../mfc/codesnippet/cpp/dispatch-maps_6.cpp)]

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdisp.h

## <a name="disp_defvalue"></a>DISP_DEFVALUE

Erstellt eine vorhandene Eigenschaft als Standardwert eines Objekts.

```cpp
DISP_DEFVALUE(theClass, pszName)
```

### <a name="parameters"></a>Parameter

*spiegeln*<br/>
Name der Klasse.

*pszName*<br/>
Externer Name der Eigenschaft, die den "Wert" des Objekts darstellt.

### <a name="remarks"></a>Bemerkungen

Die Verwendung eines Standardwerts kann das Programmieren Ihres Automation-Objekts für Visual Basic Anwendungen vereinfachen.

Der "Standardwert" des Objekts ist die Eigenschaft, die abgerufen oder festgelegt wird, wenn ein Verweis auf ein Objekt keine Eigenschaft oder Member-Funktion angibt.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdisp.h

## <a name="see-also"></a>Weitere Informationen

[Makros und Globals](../../mfc/reference/mfc-macros-and-globals.md)
