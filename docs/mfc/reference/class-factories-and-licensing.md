---
title: Klassenfabriken und Lizenzierung
ms.date: 11/04/2016
helpviewer_keywords:
- class factories [MFC], and licensing
ms.assetid: 53c4856a-4062-46db-9f69-dd4339f746b3
ms.openlocfilehash: 18d86122e57af056a50a4d94bac89d65a7b71c7d
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425928"
---
# <a name="class-factories-and-licensing"></a>Klassenfabriken und Lizenzierung

Um eine Instanz des OLE-Steuer Elements zu erstellen, ruft eine Containeranwendung eine Member-Funktion der Klassenfactory des Steuer Elements auf. Da Ihr Steuerelement ein tatsächliches OLE-Objekt ist, ist die Klassenfactory für das Erstellen von Instanzen Ihres Steuer Elements verantwortlich. Jede OLE-Steuerelement Klasse muss über eine Klassenfactory verfügen.

Ein weiteres wichtiges Feature von OLE-Steuerelementen ist die Möglichkeit, eine Lizenz zu erzwingen. Mit dem controlwizard können Sie die Lizenzierung während der Erstellung des Steuerelement Projekts integrieren. Weitere Informationen zur Steuerelement Lizenzierung finden Sie im Artikel [ActiveX-Steuerelemente: lizenzieren eines ActiveX-Steuer](../../mfc/mfc-activex-controls-licensing-an-activex-control.md)Elements.

In der folgenden Tabelle werden mehrere Makros und Funktionen aufgelistet, die zum Deklarieren und Implementieren der Klassenfactory Ihres Steuer Elements und zum Lizenzieren Ihres Steuer Elements verwendet werden.

### <a name="class-factories-and-licensing"></a>Klassenfabriken und Lizenzierung

|||
|-|-|
|[DECLARE_OLECREATE_EX](#declare_olecreate_ex)|Deklariert die Klassenfactory für ein OLE-Steuerelement oder eine Eigenschaften Seite.|
|[IMPLEMENT_OLECREATE_EX](#implement_olecreate_ex)|Implementiert die `GetClassID` Funktion des Steuer Elements und deklariert eine Instanz der Klassenfactory.|
|[BEGIN_OLEFACTORY](#begin_olefactory)|Beginnt die Deklaration von Lizenzierungs Funktionen.|
|[END_OLEFACTORY](#end_olefactory)|Beendet die Deklaration von Lizenzierungs Funktionen.|
|[Afxverifylicfile](#afxverifylicfile)|Überprüft, ob ein-Steuerelement für die Verwendung auf einem bestimmten Computer lizenziert ist.|

##  <a name="declare_olecreate_ex"></a>DECLARE_OLECREATE_EX

Deklariert eine Klassenfactory und die `GetClassID` Member-Funktion Ihrer Steuerelement Klasse.

```
DECLARE_OLECREATE_EX(class_name)
```

### <a name="parameters"></a>Parameter

*class_name*<br/>
Der Name der Steuerelement Klasse.

### <a name="remarks"></a>Hinweise

Verwenden Sie dieses Makro in der Header Datei der Control-Klasse für ein Steuerelement, das keine Lizenzierung unterstützt.

Beachten Sie, dass dieses Makro denselben Zweck erfüllt wie das folgende Codebeispiel:

[!code-cpp[NVC_MFCAxCtl#14](../../mfc/reference/codesnippet/cpp/class-factories-and-licensing_1.h)]

### <a name="requirements"></a>Voraussetzungen

  **Header** afxctl. h

##  <a name="implement_olecreate_ex"></a>IMPLEMENT_OLECREATE_EX

Implementiert die Klassenfactory Ihres Steuer Elements und die [GetClassID-](../../mfc/reference/colecontrol-class.md#getclassid) Member-Funktion Ihrer Steuerelement Klasse.

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

*class_name*<br/>
Der Name der Steuerelement-Eigenschaften Seiten Klasse.

*external_name*<br/>
Der für Anwendungen verfügbar gemachte Objektname.

*l, W1, W2, B1, B2, B3, B4, B5, B6, B7, B8*<br/>
Komponenten der CLSID der Klasse. Weitere Informationen zu diesen Parametern finden Sie in den Hinweisen zum [IMPLEMENT_OLECREATE](run-time-object-model-services.md#implement_olecreate).

### <a name="remarks"></a>Hinweise

Dieses Makro muss in der Implementierungs Datei für jede Steuerelement Klasse angezeigt werden, die das DECLARE_OLECREATE_EX-Makro oder das BEGIN_OLEFACTORY-und END_OLEFACTORY-Makros verwendet. Der externe Name ist der Bezeichner des OLE-Steuer Elements, das für andere Anwendungen verfügbar gemacht wird. Container verwenden diesen Namen, um ein Objekt dieser Steuerelement Klasse anzufordern.

### <a name="requirements"></a>Voraussetzungen

  **Header** afxctl. h

##  <a name="begin_olefactory"></a>BEGIN_OLEFACTORY

Beginnt die Deklaration ihrer Klassenfactory in der Header Datei Ihrer Steuerelement Klasse.

```
BEGIN_OLEFACTORY(class_name)
```

### <a name="parameters"></a>Parameter

*class_name*<br/>
Gibt den Namen der Steuerelement Klasse an, deren Klassenfactory ist.

### <a name="remarks"></a>Hinweise

Deklarationen von klassenfactorylizenzierungs Funktionen sollten unmittelbar nach BEGIN_OLEFACTORY beginnen.

### <a name="requirements"></a>Voraussetzungen

  **Header** afxctl. h

##  <a name="end_olefactory"></a>END_OLEFACTORY

Beendet die Deklaration der Klassenfactory Ihres Steuer Elements.

```
END_OLEFACTORY(class_name)
```

### <a name="parameters"></a>Parameter

*class_name*<br/>
Der Name der Steuerelement Klasse, deren Klassenfactory ist.

### <a name="requirements"></a>Voraussetzungen

  **Header** afxctl. h

##  <a name="afxverifylicfile"></a>Afxverifylicfile

Mit dieser Funktion können Sie überprüfen, ob die von `pszLicFileName` benannte Lizenzdatei für das OLE-Steuerelement gültig ist.

```
BOOL AFXAPI AfxVerifyLicFile(
    HINSTANCE  hInstance,
    LPCTSTR  pszLicFileName,
    LPOLESTR  pszLicFileContents,
    UINT cch = -1);
```

### <a name="parameters"></a>Parameter

*HINSTANCE*<br/>
Der Instanzhandle der dll, die dem lizenzierten Steuerelement zugeordnet ist.

*pszlicdateiname*<br/>
Verweist auf eine mit NULL endenden Zeichenfolge, die den Lizenz Dateinamen enthält.

*pszlicfilecontent*<br/>
Verweist auf eine Byte Sequenz, die der Sequenz am Anfang der Lizenzdatei entsprechen muss.

*CCH*<br/>
Anzahl der Zeichen in *pszlicfilecontent*.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Lizenzdatei vorhanden ist und mit der Zeichenfolge in *pszlicfilecontent*beginnt. andernfalls 0.

### <a name="remarks"></a>Hinweise

Wenn *CCH* den Wert-1 hat, verwendet diese Funktion Folgendes:

[!code-cpp[NVC_MFC_Utilities#36](../../mfc/codesnippet/cpp/class-factories-and-licensing_2.cpp)]

### <a name="requirements"></a>Voraussetzungen

  **Header** afxctl. h

## <a name="see-also"></a>Siehe auch

[Makros und Globals](../../mfc/reference/mfc-macros-and-globals.md)
