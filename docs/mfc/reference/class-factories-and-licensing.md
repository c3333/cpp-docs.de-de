---
title: Klassenfabriken und Lizenzierung
ms.date: 11/04/2016
helpviewer_keywords:
- class factories [MFC], and licensing
ms.assetid: 53c4856a-4062-46db-9f69-dd4339f746b3
ms.openlocfilehash: e3fed6520cdbe0fd964e4e80e7c9ed9b78296d16
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372310"
---
# <a name="class-factories-and-licensing"></a>Klassenfabriken und Lizenzierung

Um eine Instanz Ihres OLE-Steuerelements zu erstellen, ruft eine Containeranwendung eine Memberfunktion der Klassenfactory des Steuerelements auf. Da es sich bei dem Steuerelement um ein tatsächliches OLE-Objekt handelt, ist die Klassenfactory für das Erstellen von Instanzen des Steuerelements verantwortlich. Jede OLE-Steuerelementklasse muss über eine Klassenfactory verfügen.

Ein weiteres wichtiges Merkmal von OLE-Steuerelementen ist ihre Fähigkeit, eine Lizenz zu erzwingen. Mit ControlWizard können Sie die Lizenzierung während der Erstellung Ihres Steuerungsprojekts integrieren. Weitere Informationen zur Steuerelementlizenzierung finden Sie im Artikel [ActiveX Controls: Licensing An ActiveX Control](../../mfc/mfc-activex-controls-licensing-an-activex-control.md).

In der folgenden Tabelle sind mehrere Makros und Funktionen aufgeführt, die zum Deklarieren und Implementieren der Klassenfactory des Steuerelements und zur Lizenzierung des Steuerelements verwendet werden.

### <a name="class-factories-and-licensing"></a>Klassenfabriken und Lizenzierung

|||
|-|-|
|[DECLARE_OLECREATE_EX](#declare_olecreate_ex)|Deklariert die Klassenfactory für ein OLE-Steuerelement oder eine Eigenschaftenseite.|
|[IMPLEMENT_OLECREATE_EX](#implement_olecreate_ex)|Implementiert die Funktion `GetClassID` des Steuerelements und deklariert eine Instanz der Klassenfactory.|
|[BEGIN_OLEFACTORY](#begin_olefactory)|Beginnt die Deklaration aller Lizenzierungsfunktionen.|
|[END_OLEFACTORY](#end_olefactory)|Beendet die Deklaration aller Lizenzierungsfunktionen.|
|[AfxVerifyLicFile](#afxverifylicfile)|Überprüft, ob ein Steuerelement für die Verwendung auf einem bestimmten Computer lizenziert ist.|

## <a name="declare_olecreate_ex"></a><a name="declare_olecreate_ex"></a>DECLARE_OLECREATE_EX

Deklariert eine Klassenfactory `GetClassID` und die Memberfunktion Ihrer Steuerelementklasse.

```
DECLARE_OLECREATE_EX(class_name)
```

### <a name="parameters"></a>Parameter

*Class_name*<br/>
Der Name der Steuerelementklasse.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro in der Steuerelementklassenheaderdatei für ein Steuerelement, das keine Lizenzierung unterstützt.

Beachten Sie, dass dieses Makro dem gleichen Zweck wie das folgende Codebeispiel dient:

[!code-cpp[NVC_MFCAxCtl#14](../../mfc/reference/codesnippet/cpp/class-factories-and-licensing_1.h)]

### <a name="requirements"></a>Anforderungen

  **Header** afxctl.h

## <a name="implement_olecreate_ex"></a><a name="implement_olecreate_ex"></a>IMPLEMENT_OLECREATE_EX

Implementiert die Klassenfactory des Steuerelements und die [GetClassID-Memberfunktion](../../mfc/reference/colecontrol-class.md#getclassid) Ihrer Steuerelementklasse.

```
IMPLEMENT_OLECREATE_EX(
   class_name,
    external_name,
    l,
    w1,
    w2,
    b1,
    b2,
    b3,
    b4,
    b5,
    b6,
    b7,
    b8)
```

### <a name="parameters"></a>Parameter

*Class_name*<br/>
Der Name der Steuerelementeigenschaftsseitenklasse.

*external_name*<br/>
Der Objektname, der für Anwendungen verfügbar gemacht wird.

*l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8*<br/>
Komponenten der CLSID der Klasse. Weitere Informationen zu diesen Parametern finden Sie unter Hinweise [zu IMPLEMENT_OLECREATE](run-time-object-model-services.md#implement_olecreate).

### <a name="remarks"></a>Bemerkungen

Dieses Makro muss in der Implementierungsdatei für jede Steuerelementklasse angezeigt werden, die das DECLARE_OLECREATE_EX-Makro oder die BEGIN_OLEFACTORY- und END_OLEFACTORY-Makros verwendet. Der externe Name ist der Bezeichner des OLE-Steuerelements, das für andere Anwendungen verfügbar gemacht wird. Container verwenden diesen Namen, um ein Objekt dieser Steuerelementklasse anzufordern.

### <a name="requirements"></a>Anforderungen

  **Header** afxctl.h

## <a name="begin_olefactory"></a><a name="begin_olefactory"></a>BEGIN_OLEFACTORY

Beginnt die Deklaration Ihrer Klassenfactory in der Headerdatei der Steuerelementklasse.

```
BEGIN_OLEFACTORY(class_name)
```

### <a name="parameters"></a>Parameter

*Class_name*<br/>
Gibt den Namen der Steuerelementklasse an, deren Klassenfactory dies ist.

### <a name="remarks"></a>Bemerkungen

Deklarationen von Klassenfactory-Lizenzierungsfunktionen sollten unmittelbar nach BEGIN_OLEFACTORY beginnen.

### <a name="requirements"></a>Anforderungen

  **Header** afxctl.h

## <a name="end_olefactory"></a><a name="end_olefactory"></a>END_OLEFACTORY

Beendet die Deklaration der Klassenfactory des Steuerelements.

```
END_OLEFACTORY(class_name)
```

### <a name="parameters"></a>Parameter

*Class_name*<br/>
Der Name der Steuerelementklasse, deren Klassenfactory dies ist.

### <a name="requirements"></a>Anforderungen

  **Header** afxctl.h

## <a name="afxverifylicfile"></a><a name="afxverifylicfile"></a>AfxVerifyLicFile

Rufen Sie diese Funktion auf, `pszLicFileName` um zu überprüfen, ob die nach benannte Lizenzdatei für das OLE-Steuerelement gültig ist.

```
BOOL AFXAPI AfxVerifyLicFile(
    HINSTANCE  hInstance,
    LPCTSTR  pszLicFileName,
    LPOLESTR  pszLicFileContents,
    UINT cch = -1);
```

### <a name="parameters"></a>Parameter

*hInstance*<br/>
Das Instanzhandle der DLL, die dem lizenzierten Steuerelement zugeordnet ist.

*pszLicFileName*<br/>
Verweist auf eine null-beendete Zeichenfolge, die den Lizenzdateinamen enthält.

*pszLicFileContents*<br/>
Zeigt auf eine Bytesequenz, die mit der Sequenz übereinstimmen muss, die am Anfang der Lizenzdatei gefunden wurde.

*Cch*<br/>
Anzahl der Zeichen in *pszLicFileContents*.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Lizenzdatei vorhanden ist und mit der Zeichensequenz in *pszLicFileContents*beginnt. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Wenn *cch* -1 ist, verwendet diese Funktion:

[!code-cpp[NVC_MFC_Utilities#36](../../mfc/codesnippet/cpp/class-factories-and-licensing_2.cpp)]

### <a name="requirements"></a>Anforderungen

  **Header** afxctl.h

## <a name="see-also"></a>Siehe auch

[MFC-Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md)
