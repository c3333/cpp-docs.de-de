---
title: Objektmodelldienste zur Laufzeit
ms.date: 03/27/2019
helpviewer_keywords:
- run-time object model services macros
ms.assetid: 4a3e79df-2ee3-43a4-8193-20298828de85
ms.openlocfilehash: f1cefdad368ebcd006dcb4ecf653247147f36d03
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372945"
---
# <a name="run-time-object-model-services"></a>Objektmodelldienste zur Laufzeit

Die Klassen [CObject](../../mfc/reference/cobject-class.md) und [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) kapseln mehrere Objektdienste, einschließlich Zugriff auf Laufzeitklasseninformationen, Serialisierung und dynamische Objekterstellung. Alle Klassen, `CObject` die von dieser Funktionalität abgeleitet sind, erben diese Funktionalität.

Mit dem Zugriff auf Laufzeitklasseninformationen können Sie Informationen über die Klasse eines Objekts zur Laufzeit ermitteln. Die Möglichkeit, die Klasse eines Objekts zur Laufzeit zu bestimmen, ist nützlich, wenn Sie zusätzliche Typprüfungen von Funktionsargumenten benötigen und wenn Sie zweckgebundenen Code basierend auf der Klasse eines Objekts schreiben müssen. Laufzeitklasseninformationen werden von der C++-Sprache nicht direkt unterstützt.

Serialisierung ist der Prozess des Schreibens oder Lesens des Inhalts eines Objekts in oder aus einer Datei. Sie können die Serialisierung verwenden, um den Inhalt eines Objekts auch nach dem Beenden der Anwendung zu speichern. Das Objekt kann dann aus der Datei gelesen werden, wenn die Anwendung neu gestartet wird. Solche Datenobjekte gelten als "persistent".

Mit der dynamischen Objekterstellung können Sie ein Objekt einer angegebenen Klasse zur Laufzeit erstellen. Beispielsweise müssen Dokument-, Ansichts- und Frameobjekte die dynamische Erstellung unterstützen, da das Framework sie dynamisch erstellen muss.

In der folgenden Tabelle sind die MFC-Makros aufgeführt, die Laufzeitklasseninformationen, Serialisierung und dynamische Erstellung unterstützen.

Weitere Informationen zu diesen Laufzeitobjektdiensten und serialisierung finden Sie im Artikel [CObject Class: Accessing Run-Time Class Information](../../mfc/accessing-run-time-class-information.md).

### <a name="run-time-object-model-services-macros"></a>Laufzeitobjektmodell-Dienste-Makros

|||
|-|-|
|[DECLARE_DYNAMIC](#declare_dynamic)|Ermöglicht den Zugriff auf Laufzeitklasseninformationen (muss in der Klassendeklaration verwendet werden).|
|[DECLARE_DYNCREATE](#declare_dyncreate)|Ermöglicht die dynamische Erstellung und den Zugriff auf Laufzeitklasseninformationen (muss in der Klassendeklaration verwendet werden).|
|[DECLARE_SERIAL](#declare_serial)|Ermöglicht die Serialisierung und den Zugriff auf Laufzeitklasseninformationen (muss in der Klassendeklaration verwendet werden).|
|[IMPLEMENT_DYNAMIC](#implement_dynamic)|Ermöglicht den Zugriff auf Laufzeitklasseninformationen (muss in der Klassenimplementierung verwendet werden).|
|[IMPLEMENT_DYNCREATE](#implement_dyncreate)|Ermöglicht die dynamische Erstellung und den Zugriff auf Laufzeitinformationen (muss in der Klassenimplementierung verwendet werden).|
|[IMPLEMENT_SERIAL](#implement_serial)|Ermöglicht die Serialisierung und den Zugriff auf Laufzeitklasseninformationen (muss in der Klassenimplementierung verwendet werden).|
|[RUNTIME_CLASS](#runtime_class)|Gibt `CRuntimeClass` die Struktur zurück, die der benannten Klasse entspricht.|

OLE erfordert häufig die dynamische Erstellung von Objekten zur Laufzeit. Beispielsweise muss eine OLE-Serveranwendung in der Lage sein, OLE-Elemente dynamisch als Reaktion auf eine Anforderung von einem Client zu erstellen. Ebenso muss ein Automatisierungsserver in der Lage sein, Elemente als Reaktion auf Anforderungen von Automatisierungsclients zu erstellen.

Die Microsoft Foundation-Klassenbibliothek stellt zwei OLE-spezifische Makros bereit.

### <a name="dynamic-creation-of-ole-objects"></a>Dynamische Erstellung von OLE-Objekten

|||
|-|-|
|[AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)|Bestimmt, ob die Common Controls-Bibliothek die angegebene API implementiert.|
|[AFX_COMCTL32_IF_EXISTS2](#afx_comctl32_if_exists2)|Bestimmt, ob die Common Controls-Bibliothek die angegebene API implementiert.|
|[DECLARE_OLECREATE](#declare_olecreate)|Ermöglicht die Erstellung von Objekten durch OLE-Automatisierung.|
|[DECLARE_OLECTLTYPE](#declare_olectltype)|Deklariert `GetUserTypeNameID` die `GetMiscStatus` und Memberfunktionen Ihrer Steuerelementklasse.|
|[DECLARE_PROPPAGEIDS](#declare_proppageids)|Deklariert, dass das OLE-Steuerelement eine Liste der Eigenschaftenseiten bereitstellt, um seine Eigenschaften anzuzeigen.|
|[IMPLEMENT_OLECREATE](#implement_olecreate)|Ermöglicht die Erstellung von Objekten durch das OLE-System.|
|[IMPLEMENT_OLECTLTYPE](#implement_olectltype)|Implementiert die `GetUserTypeNameID` `GetMiscStatus` und Memberfunktionen Ihrer Steuerelementklasse.|
|[IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags)|Entweder dieses Makro oder [IMPLEMENT_OLECREATE](#implement_olecreate) muss in der `DECLARE_OLECREATE`Implementierungsdatei für jede Klasse angezeigt werden, die verwendet. |

## <a name="afx_comctl32_if_exists"></a><a name="afx_comctl32_if_exists"></a>AFX_COMCTL32_IF_EXISTS

Bestimmt, ob die Common Controls-Bibliothek die angegebene API implementiert.

### <a name="syntax"></a>Syntax

```
AFX_COMCTL32_IF_EXISTS(  proc );
```

### <a name="parameters"></a>Parameter

*proc*<br/>
Zeiger auf eine null-terminierte Zeichenfolge, die den Funktionsnamen enthält, oder gibt den Ordinalwert der Funktion an. Wenn es sich bei diesem Parameter um einen Ordinalwert handelt, muss er sich im Wort niedriger Ordnung befindet. Das Wort hoher Ordnung muss Null sein. Dieser Parameter muss sich in Unicode begeben.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um zu bestimmen, ob die Common Controls die von *proc* angegebene Funktion (anstelle des Aufrufs von [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress).

### <a name="requirements"></a>Anforderungen

afxcomctl32.h, afxcomctl32.inl

## <a name="afx_comctl32_if_exists2"></a><a name="afx_comctl32_if_exists2"></a>AFX_COMCTL32_IF_EXISTS2

Bestimmt, ob die Common Controls-Bibliothek die angegebene API implementiert (dies ist die Unicode-Version von [AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)).

### <a name="syntax"></a>Syntax

```
AFX_COMCTL32_IF_EXISTS2( proc );
```

### <a name="parameters"></a>Parameter

*proc*<br/>
Zeiger auf eine null-terminierte Zeichenfolge, die den Funktionsnamen enthält, oder gibt den Ordinalwert der Funktion an. Wenn es sich bei diesem Parameter um einen Ordinalwert handelt, muss er sich im Wort niedriger Ordnung befindet. Das Wort hoher Ordnung muss Null sein. Dieser Parameter muss sich in Unicode begeben.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um zu bestimmen, ob die Common Controls die von *proc* angegebene Funktion (anstelle des Aufrufs von [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress). Dieses Makro ist die Unicode-Version von AFX_COMCTL32_IF_EXISTS.

### <a name="requirements"></a>Anforderungen

afxcomctl32.h, afxcomctl32.inl

## <a name="declare_dynamic"></a><a name="declare_dynamic"></a>DECLARE_DYNAMIC

Fügt die Möglichkeit hinzu, auf Laufzeitinformationen über die Klasse eines `CObject`Objekts zuzugreifen, wenn eine Klasse von ableitung.

```
DECLARE_DYNAMIC(class_name)
```

### <a name="parameters"></a>Parameter

*Class_name*<br/>
Der tatsächliche Name der Klasse.

### <a name="remarks"></a>Bemerkungen

Fügen Sie das DECLARE_DYNAMIC-Makro zum Headermodul (.h) für die Klasse hinzu, und fügen Sie dann dieses Modul in alle CPP-Module ein, die Zugriff auf Objekte dieser Klasse benötigen.

Wenn Sie die DECLARE_ DYNAMIC- und IMPLEMENT_DYNAMIC-Makros wie beschrieben `CObject::IsKindOf` verwenden, können Sie das RUNTIME_CLASS-Makro und die Funktion verwenden, um die Klasse Ihrer Objekte zur Laufzeit zu bestimmen.

Wenn DECLARE_DYNAMIC in der Klassendeklaration enthalten ist, muss IMPLEMENT_DYNAMIC in die Klassenimplementierung einbezogen werden.

Weitere Informationen zum DECLARE_DYNAMIC-Makro finden Sie unter [CObject-Klassenthemen](../../mfc/using-cobject.md).

### <a name="example"></a>Beispiel

Siehe Beispiel für [IMPLEMENT_DYNAMIC](#implement_dynamic).

### <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="declare_dyncreate"></a><a name="declare_dyncreate"></a>DECLARE_DYNCREATE

Ermöglicht, `CObject`dass Objekte von -abgeleiteten Klassen zur Laufzeit dynamisch erstellt werden.

```
DECLARE_DYNCREATE(class_name)
```

### <a name="parameters"></a>Parameter

*Class_name*<br/>
Der tatsächliche Name der Klasse.

### <a name="remarks"></a>Bemerkungen

Das Framework verwendet diese Möglichkeit, um neue Objekte dynamisch zu erstellen. Beispielsweise die neue Ansicht, die beim Öffnen eines neuen Dokuments erstellt wurde. Dokument-, Ansichts- und Rahmenklassen sollten die dynamische Erstellung unterstützen, da das Framework sie dynamisch erstellen muss.

Fügen Sie das DECLARE_DYNCREATE-Makro simto in das H-Modul für die Klasse hinzu, und fügen Sie dann dieses Modul in alle CPP-Module ein, die Zugriff auf Objekte dieser Klasse benötigen.

Wenn DECLARE_DYNCREATE in der Klassendeklaration enthalten ist, muss IMPLEMENT_DYNCREATE in die Klassenimplementierung einbezogen werden.

Weitere Informationen zum DECLARE_DYNCREATE-Makro finden Sie unter [CObject-Klassenthemen](../../mfc/using-cobject.md).

> [!NOTE]
> Das DECLARE_DYNCREATE-Makro enthält alle Funktionen von DECLARE_DYNAMIC.

### <a name="example"></a>Beispiel

Siehe Beispiel für [IMPLEMENT_DYNCREATE](#implement_dyncreate).

### <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="declare_olectltype"></a><a name="declare_olectltype"></a>DECLARE_OLECTLTYPE

Deklariert `GetUserTypeNameID` die `GetMiscStatus` und Memberfunktionen Ihrer Steuerelementklasse.

### <a name="syntax"></a>Syntax

```
DECLARE_OLECTLTYPE( class_name )
```

### <a name="parameters"></a>Parameter

*Class_name*<br/>
Der Name der Steuerelementklasse.

### <a name="remarks"></a>Bemerkungen

`GetUserTypeNameID`und `GetMiscStatus` sind reine virtuelle `COleControl`Funktionen, deklariert in . Da diese Funktionen rein virtuell sind, müssen sie in Ihrer Steuerelementklasse überschrieben werden. Zusätzlich zu DECLARE_OLECTLTYPE müssen Sie der Steuerelementklassendeklaration das IMPLEMENT_OLECTLTYPE-Makro hinzufügen.

### <a name="requirements"></a>Anforderungen

**Kopf:** afxctl.h

## <a name="declare_proppageids"></a><a name="declare_proppageids"></a>DECLARE_PROPPAGEIDS

Deklariert, dass das OLE-Steuerelement eine Liste der Eigenschaftenseiten bereitstellt, um seine Eigenschaften anzuzeigen.

### <a name="syntax"></a>Syntax

```
DECLARE_PROPPAGEIDS( class_name )
```

### <a name="parameters"></a>Parameter

*Class_name*<br/>
Der Name der Steuerelementklasse, die Eigentümer in den Eigenschaftenseiten ist.

### <a name="remarks"></a>Bemerkungen

Verwenden `DECLARE_PROPPAGEIDS` Sie das Makro am Ende der Klassendeklaration. Verwenden Sie dann in der CPP-Datei, die die `BEGIN_PROPPAGEIDS` Memberfunktionen für die Klasse definiert, das Makro, `END_PROPPAGEIDS` Makroeinträge für jede Eigenschaftenseite des Steuerelements und das Makro, um das Ende der Eigenschaftenseitenliste zu deklarieren.

Weitere Informationen zu Eigenschaftenseiten finden Sie im Artikel [ActiveX Controls: Property Pages](../mfc-activex-controls-property-pages.md).

### <a name="requirements"></a>Anforderungen

**Kopf:** afxctl.h

## <a name="declare_serial"></a><a name="declare_serial"></a>DECLARE_SERIAL

Generiert den C++-Headercode, der für eine `CObject`-abgeleitete Klasse erforderlich ist, die serialisiert werden kann.

```
DECLARE_SERIAL(class_name)
```

### <a name="parameters"></a>Parameter

*Class_name*<br/>
Der tatsächliche Name der Klasse.

### <a name="remarks"></a>Bemerkungen

Serialisierung ist der Prozess des Schreibens oder Lesens des Inhalts eines Objekts in und aus einer Datei.

Verwenden Sie das DECLARE_SERIAL-Makro in einem H-Modul, und schließen Sie dieses Modul dann in alle CPP-Module ein, die Zugriff auf Objekte dieser Klasse benötigen.

Wenn DECLARE_SERIAL in der Klassendeklaration enthalten ist, muss IMPLEMENT_SERIAL in die Klassenimplementierung einbezogen werden.

Das DECLARE_SERIAL-Makro enthält alle Funktionen von DECLARE_DYNAMIC und DECLARE_DYNCREATE.

Sie können das AFX_API-Makro `CArchive` verwenden, um den Extraktionsoperator automatisch für Klassen zu exportieren, die die DECLARE_SERIAL- und IMPLEMENT_SERIAL-Makros verwenden. Klammern Sie die Klassendeklarationen (in der H-Datei) mit dem folgenden Code:

[!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]

Weitere Informationen zum DECLARE_SERIAL-Makro finden Sie unter [CObject-Klassenthemen](../../mfc/using-cobject.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCObjectSample#21](../../mfc/codesnippet/cpp/run-time-object-model-services_2.h)]

### <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="implement_dynamic"></a><a name="implement_dynamic"></a>IMPLEMENT_DYNAMIC

Generiert den C++-Code, `CObject`der für eine dynamische -abgeleitete Klasse mit Laufzeitzugriff auf den Klassennamen und die Position innerhalb der Hierarchie erforderlich ist.

```
IMPLEMENT_DYNAMIC(class_name, base_class_name)
```

### <a name="parameters"></a>Parameter

*Class_name*<br/>
Der tatsächliche Name der Klasse.

*base_class_name*<br/>
Der Name der Basisklasse.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie das IMPLEMENT_DYNAMIC-Makro in einem CPP-Modul, und verknüpfen Sie den resultierenden Objektcode nur einmal.

Weitere Informationen finden Sie unter [CObject-Klassenthemen](../../mfc/using-cobject.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCObjectSample#2](../../mfc/codesnippet/cpp/run-time-object-model-services_3.h)]

[!code-cpp[NVC_MFCCObjectSample#3](../../mfc/codesnippet/cpp/run-time-object-model-services_4.cpp)]

### <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="implement_dyncreate"></a><a name="implement_dyncreate"></a>IMPLEMENT_DYNCREATE

Ermöglicht, `CObject`dass Objekte von -abgeleiteten Klassen dynamisch zur Laufzeit erstellt werden, wenn sie mit dem DECLARE_DYNCREATE-Makros verwendet werden.

```
IMPLEMENT_DYNCREATE(class_name, base_class_name)
```

### <a name="parameters"></a>Parameter

*Class_name*<br/>
Der tatsächliche Name der Klasse.

*base_class_name*<br/>
Der tatsächliche Name der Basisklasse.

### <a name="remarks"></a>Bemerkungen

Das Framework verwendet diese Möglichkeit, um neue Objekte dynamisch zu erstellen, z. B. wenn es ein Objekt während der Serialisierung vom Datenträger liest. Fügen Sie das IMPLEMENT_DYNCREATE-Makro in der Klassenimplementierungsdatei hinzu. Weitere Informationen finden Sie unter [CObject-Klassenthemen](../../mfc/using-cobject.md).

Wenn Sie die DECLARE_DYNCREATE- und IMPLEMENT_DYNCREATE-Makros verwenden, `CObject::IsKindOf` können Sie die RUNTIME_CLASS-Makros und die Memberfunktion verwenden, um die Klasse Ihrer Objekte zur Laufzeit zu bestimmen.

Wenn DECLARE_DYNCREATE in der Klassendeklaration enthalten ist, muss IMPLEMENT_DYNCREATE in die Klassenimplementierung einbezogen werden.

Beachten Sie, dass diese Makrodefinition den Standardkonstruktor für Ihre Klasse aufruft. Wenn ein nicht trivialer Konstruktor explizit von der Klasse implementiert wird, muss er auch explizit den Standardkonstruktor implementieren. Der Standardkonstruktor kann den **privaten** oder **geschützten** Memberabschnitten der Klasse hinzugefügt werden, um zu verhindern, dass er von außerhalb der Klassenimplementierung aufgerufen wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCObjectSample#22](../../mfc/codesnippet/cpp/run-time-object-model-services_5.h)]

[!code-cpp[NVC_MFCCObjectSample#23](../../mfc/codesnippet/cpp/run-time-object-model-services_6.cpp)]

### <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="implement_olecreate_flags"></a><a name="implement_olecreate_flags"></a>IMPLEMENT_OLECREATE_FLAGS

Entweder dieses Makro oder [IMPLEMENT_OLECREATE](#implement_olecreate) muss in der Implementierungsdatei für jede Klasse angezeigt werden, die DECLARE_OLECREATE verwendet.

### <a name="syntax"></a>Syntax

```
IMPLEMENT_OLECREATE_FLAGS( class_name, external_name, nFlags,
    l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)
```

### <a name="parameters"></a>Parameter

*Class_name*<br/>
Der tatsächliche Name der Klasse.

*external_name*<br/>
Der Objektname, der für andere Anwendungen verfügbar gemacht wird (in Anführungszeichen eingeschlossen).

*nFlags*<br/>
Enthält eines oder mehrere der folgenden Flags:

- `afxRegInsertable`Lässt das Steuerelement im Dialogfeld Objekt einfügen für OLE-Objekte angezeigt werden.
- `afxRegApartmentThreading`Legt das Threadingmodell in der Registrierung auf ThreadingModel=Apartment fest.
- `afxRegFreeThreading`Legt das Threadingmodell in der Registrierung auf ThreadingModel=Free fest.

Sie können die `afxRegApartmentThreading` beiden `afxRegFreeThreading` Flags kombinieren und ThreadingModel=Both festlegen. Weitere Informationen zur Threadingmodellregistrierung finden Sie unter [InprocServer32](/windows/win32/com/inprocserver32) im Windows SDK.

*l*, *w1*, *w2*, *b1*, *b2*, *b3*, *b4*, *b5*, *b6*, *b7*, *b8* Komponenten der CLSID der Klasse.

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Wenn Sie IMPLEMENT_OLECREATE_FLAGS verwenden, können Sie mithilfe des Parameters *nFlags* angeben, welches Threadingmodell das Objekt unterstützt. Wenn Sie nur das Einzel-Tretmodell unterstützen möchten, verwenden Sie IMPLEMENT_OLECREATE.

Der externe Name ist der Bezeichner, der für andere Anwendungen verfügbar gemacht wird. Clientanwendungen verwenden den externen Namen, um ein Objekt dieser Klasse von einem Automatisierungsserver anzufordern.

Die OLE-Klassen-ID ist ein eindeutiger 128-Bit-Bezeichner für das Objekt. Es besteht aus einem **langen**, zwei **WORD**s und acht **BYTE**s, wie in der Syntaxbeschreibung durch *l*, *w1*, *w2*und *b1* bis *b8* dargestellt. Der Anwendungs-Assistent und die Code-Assistenten erstellen bei Bedarf eindeutige OLE-Klassen-IDs für Sie.

### <a name="requirements"></a>Anforderungen

**Header:** afxdisp.h

## <a name="implement_olectltype"></a><a name="implement_olectltype"></a>IMPLEMENT_OLECTLTYPE

Implementiert die `GetUserTypeNameID` `GetMiscStatus` und Memberfunktionen Ihrer Steuerelementklasse.

### <a name="syntax"></a>Syntax

```
DECLARE_OLECTLTYPE( class_name, idsUserTypeName, dwOleMisc )
```

### <a name="parameters"></a>Parameter

*Class_name*<br/>
Der Name der Steuerelementklasse.

*idsUserTypeName*<br/>
Die Ressourcen-ID einer Zeichenfolge, die den externen Namen des Steuerelements enthält.

*dwOleMisc*<br/>
Eine Enumeration, die ein oder mehrere Flags enthält. Weitere Informationen zu dieser Enumeration finden Sie unter [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) im Windows SDK.

### <a name="remarks"></a>Bemerkungen

Zusätzlich zu IMPLEMENT_OLECTLTYPE müssen Sie der Steuerelementklassendeklaration das DECLARE_OLECTLTYPE-Makro hinzufügen.

Die `GetUserTypeNameID` Memberfunktion gibt die Ressourcenzeichenfolge zurück, die Ihre Steuerelementklasse identifiziert. `GetMiscStatus`gibt die OLEMISC-Bits für Ihr Steuerelement zurück. Diese Enumeration gibt eine Auflistung von Einstellungen an, die verschiedene Merkmale des Steuerelements beschreiben. Eine vollständige Beschreibung der OLEMISC-Einstellungen finden Sie unter [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) im Windows SDK.

> [!NOTE]
> Die vom ActiveX ControlWizard verwendeten Standardeinstellungen sind: OLEMISC_ACTIVATEWHENVISIBLE, OLEMISC_SETCLIENTSITEFIRST, OLEMISC_INSIDEOUT, OLEMISC_CANTLINKINSIDE und OLEMISC_RECOMPOSEONRESIZE.

### <a name="requirements"></a>Anforderungen

**Kopf:** afxctl.h

## <a name="implement_serial"></a><a name="implement_serial"></a>IMPLEMENT_SERIAL

Generiert den C++-Code, `CObject`der für eine dynamische -abgeleitete Klasse mit Laufzeitzugriff auf den Klassennamen und die Position innerhalb der Hierarchie erforderlich ist.

```
IMPLEMENT_SERIAL(class_name, base_class_name, wSchema)
```

### <a name="parameters"></a>Parameter

*Class_name*<br/>
Der tatsächliche Name der Klasse.

*base_class_name*<br/>
Der Name der Basisklasse.

*wSchema*<br/>
Eine UINT-"Versionsnummer", die im Archiv codiert wird, um ein Deserialisierungsprogramm zum Identifizieren und Verarbeiten von Daten zu ermöglichen, die von früheren Programmversionen erstellt wurden. Die Klassenschemanummer darf nicht -1 sein.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie das IMPLEMENT_SERIAL-Makro in einem .cpp-Modul; verknüpfen Sie dann den resultierenden Objektcode nur einmal.

Sie können das AFX_API-Makro `CArchive` verwenden, um den Extraktionsoperator automatisch für Klassen zu exportieren, die die DECLARE_SERIAL- und IMPLEMENT_SERIAL-Makros verwenden. Klammern Sie die Klassendeklarationen (in der H-Datei) mit dem folgenden Code:

[!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]

Weitere Informationen finden Sie in den [CObject-Klassenthemen](../../mfc/using-cobject.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCObjectSample#24](../../mfc/codesnippet/cpp/run-time-object-model-services_7.cpp)]

### <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="runtime_class"></a><a name="runtime_class"></a>RUNTIME_CLASS

Ruft die Laufzeitklassenstruktur aus dem Namen einer C++-Klasse ab.

```
RUNTIME_CLASS(class_name)
```

### <a name="parameters"></a>Parameter

*Class_name*<br/>
Der tatsächliche Name der Klasse (nicht in Anführungszeichen eingeschlossen).

### <a name="remarks"></a>Bemerkungen

RUNTIME_CLASS gibt einen Zeiger auf eine [CRuntimeClass-Struktur](../../mfc/reference/cruntimeclass-structure.md) für die von *class_name*angegebene Klasse zurück. Nur `CObject`-abgeleitete Klassen, die mit DECLARE_DYNAMIC, DECLARE_DYNCREATE oder `CRuntimeClass` DECLARE_SERIAL deklariert wurden, geben Zeiger an eine Struktur zurück.

Weitere Informationen finden Sie unter [CObject-Klassenthemen](../../mfc/using-cobject.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCObjectSample#25](../../mfc/codesnippet/cpp/run-time-object-model-services_8.cpp)]

### <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="declare_olecreate"></a><a name="declare_olecreate"></a>DECLARE_OLECREATE

Ermöglicht das `CCmdTarget`Erstellen von Objekten von -abgeleiteten Klassen durch DIE OLE-Automatisierung.

```
DECLARE_OLECREATE(class_name)
```

### <a name="parameters"></a>Parameter

*Class_name*<br/>
Der tatsächliche Name der Klasse.

### <a name="remarks"></a>Bemerkungen

Dieses Makro ermöglicht es anderen OLE-fähigen Anwendungen, Objekte dieses Typs zu erstellen.

Fügen Sie das DECLARE_OLECREATE-Makro simto in das H-Modul für die Klasse hinzu, und fügen Sie dieses Modul dann in alle CPP-Module ein, die Zugriff auf Objekte dieser Klasse benötigen.

Wenn DECLARE_OLECREATE in der Klassendeklaration enthalten ist, muss IMPLEMENT_OLECREATE in die Klassenimplementierung einbezogen werden. Eine Klassendeklaration, die DECLARE_OLECREATE verwendet, muss auch DECLARE_DYNCREATE oder DECLARE_SERIAL verwenden.

### <a name="requirements"></a>Anforderungen

**Kopfzeile**: afxdisp.h

## <a name="implement_olecreate"></a><a name="implement_olecreate"></a>IMPLEMENT_OLECREATE

Entweder dieses Makro oder [IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags) muss in der `DECLARE_OLECREATE`Implementierungsdatei für jede Klasse angezeigt werden, die verwendet.

```
IMPLEMENT_OLECREATE(class_name, external_name, l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)
```

### <a name="parameters"></a>Parameter

*Class_name*<br/>
Der tatsächliche Name der Klasse.

*external_name*<br/>
Der Objektname, der für andere Anwendungen verfügbar gemacht wird (in Anführungszeichen eingeschlossen).

*l*, *w1*, *w2*, *b1*, *b2*, *b3*, *b4*, *b5*, *b6*, *b7*, *b8* Komponenten der CLSID der Klasse.

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Wenn Sie IMPLEMENT_OLECREATE verwenden, unterstützen Sie standardmäßig nur das einzelne Threadingmodell. Wenn Sie IMPLEMENT_OLECREATE_FLAGS verwenden, können Sie mithilfe des Parameters *nFlags* angeben, welches Threadingmodell das Objekt unterstützt.

Der externe Name ist der Bezeichner, der für andere Anwendungen verfügbar gemacht wird. Clientanwendungen verwenden den externen Namen, um ein Objekt dieser Klasse von einem Automatisierungsserver anzufordern.

Die OLE-Klassen-ID ist ein eindeutiger 128-Bit-Bezeichner für das Objekt. Es besteht aus einem **langen**, zwei **WORD**s und acht **BYTE**s, wie in der Syntaxbeschreibung durch *l*, *w1*, *w2*und *b1* bis *b8* dargestellt. Der Anwendungs-Assistent und die Code-Assistenten erstellen bei Bedarf eindeutige OLE-Klassen-IDs für Sie.

### <a name="requirements"></a>Anforderungen

**Kopfzeile**: afxdisp.h

## <a name="see-also"></a>Siehe auch

[MFC-Makros, globale Funktionen und globale Variablen](mfc-macros-and-globals.md)<br/>
[Isolierung der MFC-Bibliothek für Standardsteuerelemente](../isolation-of-the-mfc-common-controls-library.md)<br/>
[CLSID-Schlüssel](/windows/win32/com/clsid-key-hklm)
