---
title: Objektmodelldienste zur Laufzeit
ms.date: 03/27/2019
helpviewer_keywords:
- run-time object model services macros
ms.assetid: 4a3e79df-2ee3-43a4-8193-20298828de85
ms.openlocfilehash: f8b891467d91d0c945b6c59c90dbc49fd7cbcb30
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426702"
---
# <a name="run-time-object-model-services"></a>Objektmodelldienste zur Laufzeit

Die Klassen [CObject](../../mfc/reference/cobject-class.md) und [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) Kapseln mehrere Objekt Dienste, einschließlich des Zugriffs auf Lauf Zeit Klassen Informationen, Serialisierung und dynamische Objekt Erstellung. Alle von abgeleiteten Klassen `CObject` diese Funktion erben.

Der Zugriff auf Lauf Zeit Klassen Informationen ermöglicht es Ihnen, Informationen über die Klasse eines Objekts zur Laufzeit zu bestimmen. Die Möglichkeit, die Klasse eines Objekts zur Laufzeit zu bestimmen, ist nützlich, wenn Sie eine zusätzliche Typüberprüfung von Funktions Argumenten benötigen und wenn Sie speziellen Code basierend auf der Klasse eines Objekts schreiben müssen. Lauf Zeit Klassen Informationen werden nicht direkt von der C++ Sprache unterstützt.

Serialisierung ist der Prozess, bei dem ein Objekt Inhalt in eine oder aus einer Datei geschrieben oder gelesen wird. Sie können die Serialisierung auch verwenden, um den Inhalt eines Objekts zu speichern, auch nachdem die Anwendung beendet wurde. Das Objekt kann dann aus der Datei gelesen werden, wenn die Anwendung neu gestartet wird. Solche Datenobjekte werden als "persistent" bezeichnet.

Die dynamische Objekt Erstellung ermöglicht es Ihnen, ein Objekt einer angegebenen Klasse zur Laufzeit zu erstellen. Beispielsweise müssen Dokument-, Sicht-und Frame Objekte die dynamische Erstellung unterstützen, da Sie vom Framework dynamisch erstellt werden muss.

In der folgenden Tabelle werden die MFC-Makros aufgelistet, die Lauf Zeit Klassen Informationen, Serialisierung und dynamische Erstellung unterstützen.

Weitere Informationen zu diesen Laufzeitobjekt Diensten und zur Serialisierung finden Sie im Artikel [CObject-Klasse: Zugreifen auf Lauf Zeit Klassen Informationen](../../mfc/accessing-run-time-class-information.md).

### <a name="run-time-object-model-services-macros"></a>Laufzeitobjekt Modell Dienste-Makros

|||
|-|-|
|[DECLARE_DYNAMIC](#declare_dynamic)|Ermöglicht den Zugriff auf Lauf Zeit Klassen Informationen (muss in der Klassen Deklaration verwendet werden).|
|[DECLARE_DYNCREATE](#declare_dyncreate)|Ermöglicht die dynamische Erstellung und den Zugriff auf Lauf Zeit Klassen Informationen (muss in der Klassen Deklaration verwendet werden).|
|[DECLARE_SERIAL](#declare_serial)|Aktiviert die Serialisierung und den Zugriff auf Lauf Zeit Klassen Informationen (muss in der Klassen Deklaration verwendet werden).|
|[IMPLEMENT_DYNAMIC](#implement_dynamic)|Ermöglicht den Zugriff auf Lauf Zeit Klassen Informationen (muss in der Klassen Implementierung verwendet werden).|
|[IMPLEMENT_DYNCREATE](#implement_dyncreate)|Ermöglicht die dynamische Erstellung und den Zugriff auf Laufzeitinformationen (muss in der Klassen Implementierung verwendet werden).|
|[IMPLEMENT_SERIAL](#implement_serial)|Ermöglicht die Serialisierung und den Zugriff auf Lauf Zeit Klassen Informationen (muss in der Klassen Implementierung verwendet werden).|
|[RUNTIME_CLASS](#runtime_class)|Gibt die `CRuntimeClass`-Struktur zurück, die der benannten Klasse entspricht.|

OLE erfordert häufig die dynamische Erstellung von Objekten zur Laufzeit. Beispielsweise muss eine OLE Server-Anwendung in der Lage sein, OLE-Elemente dynamisch als Reaktion auf eine Anforderung von einem Client zu erstellen. Ebenso muss ein Automatisierungsserver in der Lage sein, Elemente als Reaktion auf Anforderungen von Automatisierungs Clients zu erstellen.

Der Microsoft Foundation Class-Bibliothek stellt zwei für OLE spezifische Makros bereit.

### <a name="dynamic-creation-of-ole-objects"></a>Dynamische Erstellung von OLE-Objekten

|||
|-|-|
|[AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)|Bestimmt, ob die allgemeine Steuerelement Bibliothek die angegebene API implementiert.|
|[AFX_COMCTL32_IF_EXISTS2](#afx_comctl32_if_exists2)|Bestimmt, ob die allgemeine Steuerelement Bibliothek die angegebene API implementiert.|
|[DECLARE_OLECREATE](#declare_olecreate)|Ermöglicht das Erstellen von Objekten durch OLE-Automatisierung.|
|[DECLARE_OLECTLTYPE](#declare_olectltype)|Deklariert die `GetUserTypeNameID`-und `GetMiscStatus` Member-Funktionen Ihrer Steuerelement Klasse.|
|[DECLARE_PROPPAGEIDS](#declare_proppageids)|Deklariert, dass das OLE-Steuerelement eine Liste von Eigenschaften Seiten zum Anzeigen seiner Eigenschaften bereitstellt.|
|[IMPLEMENT_OLECREATE](#implement_olecreate)|Ermöglicht das Erstellen von Objekten durch das OLE-System.|
|[IMPLEMENT_OLECTLTYPE](#implement_olectltype)|Implementiert die Funktionen `GetUserTypeNameID` und `GetMiscStatus` Member der Steuerelement Klasse.|
|[IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags)|Entweder dieses Makro oder [IMPLEMENT_OLECREATE](#implement_olecreate) muss in der Implementierungs Datei für jede Klasse, die `DECLARE_OLECREATE`verwendet, angezeigt werden. |

## <a name="afx_comctl32_if_exists"></a>AFX_COMCTL32_IF_EXISTS

Bestimmt, ob die allgemeine Steuerelement Bibliothek die angegebene API implementiert.

### <a name="syntax"></a>Syntax

```
AFX_COMCTL32_IF_EXISTS(  proc );
```

### <a name="parameters"></a>Parameter

*proc*<br/>
Zeiger auf eine mit NULL endenden Zeichenfolge, die den Funktionsnamen enthält, oder gibt den Ordinalwert der Funktion an. Wenn dieser Parameter ein Ordinalwert ist, muss er im nieder wertigen Wort liegen. das höchst wertige Wort muss NULL sein. Dieser Parameter muss im Unicode-Format vorliegen.

### <a name="remarks"></a>Hinweise

Verwenden Sie dieses Makro, um zu bestimmen, ob die gemeinsame Steuerelement Bibliothek die von *proc* angegebene Funktion (anstelle von [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress)aufgerufen hat).

### <a name="requirements"></a>Voraussetzungen

afxcomctl32. h, afxcomctl32. INL

## <a name="afx_comctl32_if_exists2"></a>AFX_COMCTL32_IF_EXISTS2

Bestimmt, ob die allgemeine Steuerelement Bibliothek die angegebene API implementiert (Hierbei handelt es sich um die Unicode-Version von [AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)).

### <a name="syntax"></a>Syntax

```
AFX_COMCTL32_IF_EXISTS2( proc );
```

### <a name="parameters"></a>Parameter

*proc*<br/>
Zeiger auf eine mit NULL endenden Zeichenfolge, die den Funktionsnamen enthält, oder gibt den Ordinalwert der Funktion an. Wenn dieser Parameter ein Ordinalwert ist, muss er im nieder wertigen Wort liegen. das höchst wertige Wort muss NULL sein. Dieser Parameter muss im Unicode-Format vorliegen.

### <a name="remarks"></a>Hinweise

Verwenden Sie dieses Makro, um zu bestimmen, ob die gemeinsame Steuerelement Bibliothek die von *proc* angegebene Funktion (anstelle von [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress)aufgerufen hat). Dieses Makro ist die Unicode-Version von AFX_COMCTL32_IF_EXISTS.

### <a name="requirements"></a>Voraussetzungen

afxcomctl32. h, afxcomctl32. INL

##  <a name="declare_dynamic"></a>DECLARE_DYNAMIC

Fügt die Möglichkeit hinzu, auf Laufzeitinformationen über die Klasse eines Objekts zuzugreifen, wenn eine Klasse von `CObject`abgeleitet wird.

```
DECLARE_DYNAMIC(class_name)
```

### <a name="parameters"></a>Parameter

*class_name*<br/>
Der tatsächliche Name der Klasse.

### <a name="remarks"></a>Hinweise

Fügen Sie das DECLARE_DYNAMIC-Makro dem Header (. h) für die Klasse hinzu, und schließen Sie dann das Modul in alle cpp-Module ein, die Zugriff auf die Objekte dieser Klasse benötigen.

Wenn Sie die DECLARE_ dynamischen und IMPLEMENT_DYNAMIC Makros wie beschrieben verwenden, können Sie das RUNTIME_CLASS-Makro und die `CObject::IsKindOf`-Funktion verwenden, um die Klasse der Objekte zur Laufzeit zu bestimmen.

Wenn DECLARE_DYNAMIC in der Klassen Deklaration enthalten ist, müssen IMPLEMENT_DYNAMIC in die Klassen Implementierung eingeschlossen werden.

Weitere Informationen zum DECLARE_DYNAMIC-Makro finden Sie unter [CObject Class topics](../../mfc/using-cobject.md).

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [IMPLEMENT_DYNAMIC](#implement_dynamic).

### <a name="requirements"></a>Voraussetzungen

**Header:** afx.h

##  <a name="declare_dyncreate"></a>DECLARE_DYNCREATE

Ermöglicht die dynamische Erstellung von Objekten `CObject`abgeleiteter Klassen zur Laufzeit.

```
DECLARE_DYNCREATE(class_name)
```

### <a name="parameters"></a>Parameter

*class_name*<br/>
Der tatsächliche Name der Klasse.

### <a name="remarks"></a>Hinweise

Das Framework verwendet diese Möglichkeit zum dynamischen Erstellen neuer Objekte. Beispielsweise die neue Ansicht, die beim Öffnen eines neuen Dokuments erstellt wird. Die Klassen "Document", "View" und "Frame" sollten die dynamische Erstellung unterstützen, da Sie vom Framework dynamisch erstellt werden muss

Fügen Sie das DECLARE_DYNCREATE-Makro im. h-Modul für die-Klasse hinzu, und schließen Sie dann dieses Modul in alle cpp-Module ein, die Zugriff auf Objekte dieser Klasse benötigen.

Wenn DECLARE_DYNCREATE in der Klassen Deklaration enthalten ist, müssen IMPLEMENT_DYNCREATE in die Klassen Implementierung eingeschlossen werden.

Weitere Informationen zum DECLARE_DYNCREATE-Makro finden Sie unter [CObject Class topics](../../mfc/using-cobject.md).

> [!NOTE]
>  Das DECLARE_DYNCREATE-Makro umfasst die gesamte Funktionalität von DECLARE_DYNAMIC.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [IMPLEMENT_DYNCREATE](#implement_dyncreate).

### <a name="requirements"></a>Voraussetzungen

**Header:** afx.h

## <a name="declare_olectltype"></a>DECLARE_OLECTLTYPE

Deklariert die `GetUserTypeNameID`-und `GetMiscStatus` Member-Funktionen Ihrer Steuerelement Klasse.

### <a name="syntax"></a>Syntax

```
DECLARE_OLECTLTYPE( class_name )
```

### <a name="parameters"></a>Parameter

*class_name*<br/>
Der Name der Steuerelement Klasse.

### <a name="remarks"></a>Hinweise

`GetUserTypeNameID` und `GetMiscStatus` sind rein virtuelle Funktionen, die in `COleControl`deklariert werden. Da diese Funktionen rein virtuell sind, müssen Sie in der Steuerelement Klasse überschrieben werden. Zusätzlich zu DECLARE_OLECTLTYPE müssen Sie das IMPLEMENT_OLECTLTYPE-Makro der Deklaration der Steuerelement Klasse hinzufügen.

### <a name="requirements"></a>Voraussetzungen

**Header:** afxctl. h

## <a name="declare_proppageids"></a>DECLARE_PROPPAGEIDS

Deklariert, dass das OLE-Steuerelement eine Liste von Eigenschaften Seiten zum Anzeigen seiner Eigenschaften bereitstellt.

### <a name="syntax"></a>Syntax

```
DECLARE_PROPPAGEIDS( class_name )
```

### <a name="parameters"></a>Parameter

*class_name*<br/>
Der Name der Steuerelement Klasse, die Besitzer der Eigenschaften Seiten ist.

### <a name="remarks"></a>Hinweise

Verwenden Sie das `DECLARE_PROPPAGEIDS`-Makro am Ende der Klassen Deklaration. Verwenden Sie dann in der CPP-Datei, die die Element Funktionen für die Klasse definiert, das `BEGIN_PROPPAGEIDS` Makro, die Makro Einträge für die einzelnen Eigenschaften Seiten des Steuer Elements und das `END_PROPPAGEIDS` Makro, um das Ende der Eigenschaften Seitenliste zu deklarieren.

Weitere Informationen zu Eigenschaften Seiten finden Sie im Artikel ActiveX-Steuer [Elemente: Eigenschaften Seiten](../mfc-activex-controls-property-pages.md).

### <a name="requirements"></a>Voraussetzungen

**Header:** afxctl. h

##  <a name="declare_serial"></a>DECLARE_SERIAL

Generiert den C++ Header Code, der für eine `CObject`abgeleitete Klasse erforderlich ist, die serialisiert werden kann.

```
DECLARE_SERIAL(class_name)
```

### <a name="parameters"></a>Parameter

*class_name*<br/>
Der tatsächliche Name der Klasse.

### <a name="remarks"></a>Hinweise

Serialisierung ist der Prozess, bei dem der Inhalt eines Objekts in eine und aus einer Datei geschrieben oder gelesen wird.

Verwenden Sie das DECLARE_SERIAL-Makro in einem. h-Modul, und schließen Sie dieses Modul in alle cpp-Module ein, die Zugriff auf Objekte dieser Klasse benötigen.

Wenn DECLARE_SERIAL in der Klassen Deklaration enthalten ist, müssen IMPLEMENT_SERIAL in die Klassen Implementierung eingeschlossen werden.

Das DECLARE_SERIAL-Makro umfasst sämtliche Funktionen von DECLARE_DYNAMIC und DECLARE_DYNCREATE.

Sie können das AFX_API-Makro verwenden, um automatisch den `CArchive` Extraktions Operator für Klassen zu exportieren, die die DECLARE_SERIAL-und IMPLEMENT_SERIAL-Makros verwenden. Klammern Sie die Klassen Deklarationen (die sich in der h-Datei befinden) mit dem folgenden Code:

[!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]

Weitere Informationen zum DECLARE_SERIAL-Makro finden Sie unter [CObject Class topics](../../mfc/using-cobject.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCObjectSample#21](../../mfc/codesnippet/cpp/run-time-object-model-services_2.h)]

### <a name="requirements"></a>Voraussetzungen

**Header:** afx.h

##  <a name="implement_dynamic"></a>IMPLEMENT_DYNAMIC

Generiert den C++ Code, der für eine dynamische `CObject`abgeleitete Klasse mit Lauf Zeit Zugriff auf den Klassennamen und die Position innerhalb der Hierarchie erforderlich ist.

```
IMPLEMENT_DYNAMIC(class_name, base_class_name)
```

### <a name="parameters"></a>Parameter

*class_name*<br/>
Der tatsächliche Name der Klasse.

*base_class_name*<br/>
Der Name der Basisklasse.

### <a name="remarks"></a>Hinweise

Verwenden Sie das IMPLEMENT_DYNAMIC-Makro in einem cpp-Modul, und verknüpfen Sie den resultierenden Objektcode nur einmal.

Weitere Informationen finden Sie unter [CObject Class topics](../../mfc/using-cobject.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCObjectSample#2](../../mfc/codesnippet/cpp/run-time-object-model-services_3.h)]

[!code-cpp[NVC_MFCCObjectSample#3](../../mfc/codesnippet/cpp/run-time-object-model-services_4.cpp)]

### <a name="requirements"></a>Voraussetzungen

**Header:** afx.h

##  <a name="implement_dyncreate"></a>IMPLEMENT_DYNCREATE

Ermöglicht die dynamische Erstellung von Objekten `CObject`abgeleiteter Klassen zur Laufzeit, wenn Sie mit dem DECLARE_DYNCREATE-Makro verwendet werden.

```
IMPLEMENT_DYNCREATE(class_name, base_class_name)
```

### <a name="parameters"></a>Parameter

*class_name*<br/>
Der tatsächliche Name der Klasse.

*base_class_name*<br/>
Der tatsächliche Name der Basisklasse.

### <a name="remarks"></a>Hinweise

Das Framework verwendet diese Möglichkeit, um neue Objekte dynamisch zu erstellen, z. b. Wenn ein Objekt während der Serialisierung von einem Datenträger gelesen wird. Fügen Sie das IMPLEMENT_DYNCREATE-Makro in der Klassen Implementierungs Datei hinzu. Weitere Informationen finden Sie unter [CObject Class topics](../../mfc/using-cobject.md).

Wenn Sie die Makros DECLARE_DYNCREATE und IMPLEMENT_DYNCREATE verwenden, können Sie das RUNTIME_CLASS-Makro und die `CObject::IsKindOf` Member-Funktion verwenden, um die Klasse der Objekte zur Laufzeit zu bestimmen.

Wenn DECLARE_DYNCREATE in der Klassen Deklaration enthalten ist, müssen IMPLEMENT_DYNCREATE in die Klassen Implementierung eingeschlossen werden.

Beachten Sie, dass diese Makro Definition den Standardkonstruktor für die Klasse aufruft. Wenn ein nicht trivialer Konstruktor explizit von der-Klasse implementiert wird, muss auch der Standardkonstruktor explizit implementiert werden. Der Standardkonstruktor kann den **privaten** oder **geschützten** Element Abschnitten der Klasse hinzugefügt werden, um zu verhindern, dass er von außerhalb der Klassen Implementierung aufgerufen wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCObjectSample#22](../../mfc/codesnippet/cpp/run-time-object-model-services_5.h)]

[!code-cpp[NVC_MFCCObjectSample#23](../../mfc/codesnippet/cpp/run-time-object-model-services_6.cpp)]

### <a name="requirements"></a>Voraussetzungen

**Header:** afx.h

## <a name="implement_olecreate_flags"></a>IMPLEMENT_OLECREATE_FLAGS

Entweder dieses Makro oder [IMPLEMENT_OLECREATE](#implement_olecreate) muss in der Implementierungs Datei für jede Klasse, die DECLARE_OLECREATE verwendet, angezeigt werden.

### <a name="syntax"></a>Syntax

```
IMPLEMENT_OLECREATE_FLAGS( class_name, external_name, nFlags,
    l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)
```

### <a name="parameters"></a>Parameter

*class_name*<br/>
Der tatsächliche Name der Klasse.

*external_name*<br/>
Der für andere Anwendungen verfügbar gemachte Objektname (in Anführungszeichen eingeschlossen).

*nFlags*<br/>
Enthält mindestens eines der folgenden Flags:

   - mit `afxRegInsertable` kann das Steuerelement im Dialogfeld Objekt einfügen für OLE-Objekte angezeigt werden.
   - `afxRegApartmentThreading` legt das Threading Modell in der Registrierung auf ThreadingModel = Apartment fest.
   - `afxRegFreeThreading` legt das Threading Modell in der Registrierung auf ThreadingModel = Free fest.

         You can combine the two flags `afxRegApartmentThreading` and `afxRegFreeThreading` to set ThreadingModel=Both. See [InprocServer32](/windows/win32/com/inprocserver32) in the Windows SDK for more information on threading model registration.

die Komponenten *l*, *W1*, *W2*, *B1*, *B2*, *B3*, *B4*, *B5*, *B6*, *B7*, *B8* der CLSID der Klasse.

### <a name="remarks"></a>Hinweise

> [!NOTE]
>  Wenn Sie IMPLEMENT_OLECREATE_FLAGS verwenden, können Sie angeben, welches Threading Modell Ihr Objekt unterstützt, indem Sie den *nFlags* -Parameter verwenden. Wenn Sie nur das Single-Treading-Modell unterstützen möchten, verwenden Sie IMPLEMENT_OLECREATE.

Der externe Name ist der Bezeichner, der für andere Anwendungen verfügbar gemacht wird. Client Anwendungen verwenden den externen Namen, um ein Objekt dieser Klasse von einem Automatisierungsserver anzufordern.

Die OLE-Klassen-ID ist ein eindeutiger 128-Bit-Bezeichner für das Objekt. Sie besteht aus einem **langen**, zwei **Wort**s und acht **Byte**s, wie durch *l*, *W1*, *W2*und *B1* bis *B8* in der Syntax Beschreibung dargestellt. Der Anwendungs-Assistent und die Code-Assistenten erstellen eindeutige OLE-Klassen-IDs für Sie nach Bedarf.

### <a name="requirements"></a>Voraussetzungen

**Header:** afxdisp.h

## <a name="implement_olectltype"></a>IMPLEMENT_OLECTLTYPE

Implementiert die Funktionen `GetUserTypeNameID` und `GetMiscStatus` Member der Steuerelement Klasse.

### <a name="syntax"></a>Syntax

```
DECLARE_OLECTLTYPE( class_name, idsUserTypeName, dwOleMisc )
```

### <a name="parameters"></a>Parameter

*class_name*<br/>
Der Name der Steuerelement Klasse.

*idsusertypname*<br/>
Die Ressourcen-ID einer Zeichenfolge, die den externen Namen des Steuer Elements enthält.

*dwolemisc*<br/>
Eine Enumeration, die ein oder mehrere Flags enthält. Weitere Informationen zu dieser Enumeration finden Sie unter [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) in der Windows SDK.

### <a name="remarks"></a>Hinweise

Zusätzlich zu IMPLEMENT_OLECTLTYPE müssen Sie das DECLARE_OLECTLTYPE-Makro der Deklaration der Steuerelement Klasse hinzufügen.

Die `GetUserTypeNameID` Member-Funktion gibt die Ressourcen Zeichenfolge zurück, die die Steuerelement Klasse identifiziert. `GetMiscStatus` gibt die OLEMISC-Bits für das Steuerelement zurück. Diese Enumeration gibt eine Sammlung von Einstellungen an, die verschiedene Eigenschaften Ihres Steuer Elements beschreiben. Eine vollständige Beschreibung der OLEMISC-Einstellungen finden Sie unter [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) in der Windows SDK.

> [!NOTE]
>  Die Standardeinstellungen, die vom ActiveX-controlwizard verwendet werden, sind: OLEMISC_ACTIVATEWHENVISIBLE, OLEMISC_SETCLIENTSITEFIRST, OLEMISC_INSIDEOUT, OLEMISC_CANTLINKINSIDE und OLEMISC_RECOMPOSEONRESIZE.

### <a name="requirements"></a>Voraussetzungen

**Header:** afxctl. h

##  <a name="implement_serial"></a>IMPLEMENT_SERIAL

Generiert den C++ Code, der für eine dynamische `CObject`abgeleitete Klasse mit Lauf Zeit Zugriff auf den Klassennamen und die Position innerhalb der Hierarchie erforderlich ist.

```
IMPLEMENT_SERIAL(class_name, base_class_name, wSchema)
```

### <a name="parameters"></a>Parameter

*class_name*<br/>
Der tatsächliche Name der Klasse.

*base_class_name*<br/>
Der Name der Basisklasse.

*wschema*<br/>
Eine uint-"Versionsnummer", die im Archiv codiert wird, um ein Deserialisierungsprogramm zum Identifizieren und behandeln von Daten zu ermöglichen, die von früheren Programmversionen erstellt wurden. Die Klassen Schema Nummer darf nicht-1 sein.

### <a name="remarks"></a>Hinweise

Verwenden Sie das IMPLEMENT_SERIAL-Makro in einem. cpp-Modul. Verknüpfen Sie dann den resultierenden Objektcode nur einmal.

Sie können das AFX_API-Makro verwenden, um automatisch den `CArchive` Extraktions Operator für Klassen zu exportieren, die die DECLARE_SERIAL-und IMPLEMENT_SERIAL-Makros verwenden. Klammern Sie die Klassen Deklarationen (die sich in der h-Datei befinden) mit dem folgenden Code:

[!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]

Weitere Informationen finden Sie in den [Themen der CObject-Klasse](../../mfc/using-cobject.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCObjectSample#24](../../mfc/codesnippet/cpp/run-time-object-model-services_7.cpp)]

### <a name="requirements"></a>Voraussetzungen

**Header:** afx.h

##  <a name="runtime_class"></a>RUNTIME_CLASS

Ruft die Lauf Zeit Klassenstruktur aus dem Namen einer C++ Klasse ab.

```
RUNTIME_CLASS(class_name)
```

### <a name="parameters"></a>Parameter

*class_name*<br/>
Der tatsächliche Name der Klasse (nicht in Anführungszeichen eingeschlossen).

### <a name="remarks"></a>Hinweise

RUNTIME_CLASS gibt einen Zeiger auf eine [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) -Struktur für die Klasse zurück, die durch *class_name*angegeben wird. Nur `CObject`von abgeleitete Klassen, die mit DECLARE_DYNAMIC, DECLARE_DYNCREATE oder DECLARE_SERIAL deklariert werden, geben Zeiger auf eine `CRuntimeClass` Struktur zurück.

Weitere Informationen finden Sie unter [CObject Class topics](../../mfc/using-cobject.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCObjectSample#25](../../mfc/codesnippet/cpp/run-time-object-model-services_8.cpp)]

### <a name="requirements"></a>Voraussetzungen

**Header:** afx.h

##  <a name="declare_olecreate"></a>DECLARE_OLECREATE

Ermöglicht das Erstellen von Objekten `CCmdTarget`abgeleiteter Klassen mithilfe der OLE-Automatisierung.

```
DECLARE_OLECREATE(class_name)
```

### <a name="parameters"></a>Parameter

*class_name*<br/>
Der tatsächliche Name der Klasse.

### <a name="remarks"></a>Hinweise

Dieses Makro ermöglicht es anderen OLE-fähigen Anwendungen, Objekte dieses Typs zu erstellen.

Fügen Sie das DECLARE_OLECREATE-Makro im. h-Modul für die-Klasse hinzu, und schließen Sie dann dieses Modul in alle cpp-Module ein, die Zugriff auf Objekte dieser Klasse benötigen.

Wenn DECLARE_OLECREATE in der Klassen Deklaration enthalten ist, müssen IMPLEMENT_OLECREATE in die Klassen Implementierung eingeschlossen werden. Eine Klassen Deklaration, die DECLARE_OLECREATE verwendet, muss auch DECLARE_DYNCREATE oder DECLARE_SERIAL verwenden.

### <a name="requirements"></a>Voraussetzungen

**Header**: afxdisp. h

##  <a name="implement_olecreate"></a>IMPLEMENT_OLECREATE

Entweder dieses Makro oder [IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags) muss in der Implementierungs Datei für jede Klasse, die `DECLARE_OLECREATE`verwendet, angezeigt werden.

```
IMPLEMENT_OLECREATE(class_name, external_name, l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)
```

### <a name="parameters"></a>Parameter

*class_name*<br/>
Der tatsächliche Name der Klasse.

*external_name*<br/>
Der für andere Anwendungen verfügbar gemachte Objektname (in Anführungszeichen eingeschlossen).

die Komponenten *l*, *W1*, *W2*, *B1*, *B2*, *B3*, *B4*, *B5*, *B6*, *B7*, *B8* der CLSID der Klasse.

### <a name="remarks"></a>Hinweise

> [!NOTE]
>  Wenn Sie IMPLEMENT_OLECREATE verwenden, unterstützen Sie standardmäßig nur das einzelne Threading Modell. Wenn Sie IMPLEMENT_OLECREATE_FLAGS verwenden, können Sie angeben, welches Threading Modell Ihr Objekt unterstützt, indem Sie den *nFlags* -Parameter verwenden.

Der externe Name ist der Bezeichner, der für andere Anwendungen verfügbar gemacht wird. Client Anwendungen verwenden den externen Namen, um ein Objekt dieser Klasse von einem Automatisierungsserver anzufordern.

Die OLE-Klassen-ID ist ein eindeutiger 128-Bit-Bezeichner für das Objekt. Sie besteht aus einem **langen**, zwei **Wort**s und acht **Byte**s, wie durch *l*, *W1*, *W2*und *B1* bis *B8* in der Syntax Beschreibung dargestellt. Der Anwendungs-Assistent und die Code-Assistenten erstellen eindeutige OLE-Klassen-IDs für Sie nach Bedarf.

### <a name="requirements"></a>Voraussetzungen

**Header**: afxdisp. h

## <a name="see-also"></a>Siehe auch

[Makros und Globals](mfc-macros-and-globals.md)<br/>
[Isolierung der MFC-Bibliothek für Standardsteuerelemente](../isolation-of-the-mfc-common-controls-library.md)<br/>
[CLSID-Schlüssel](/windows/win32/com/clsid-key-hklm)
