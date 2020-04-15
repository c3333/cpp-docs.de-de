---
title: CHtmlEditDoc-Klasse
ms.date: 11/04/2016
f1_keywords:
- CHtmlEditDoc
- AFXHTML/CHtmlEditDoc
- AFXHTML/CHtmlEditDoc::CHtmlEditDoc
- AFXHTML/CHtmlEditDoc::GetView
- AFXHTML/CHtmlEditDoc::IsModified
- AFXHTML/CHtmlEditDoc::OpenURL
helpviewer_keywords:
- CHtmlEditDoc [MFC], CHtmlEditDoc
- CHtmlEditDoc [MFC], GetView
- CHtmlEditDoc [MFC], IsModified
- CHtmlEditDoc [MFC], OpenURL
ms.assetid: b2cca61f-e5d6-4099-b0d1-46bf85f0bd64
ms.openlocfilehash: 8b500f651da1a73040fdb0469f2f023babe25e85
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352174"
---
# <a name="chtmleditdoc-class"></a>CHtmlEditDoc-Klasse

Mit [CHtmlEditView](../../mfc/reference/chtmleditview-class.md)stellt die Funktionalität der WebBrowser-Bearbeitungsplattform im Kontext der MFC-Dokumentansichtsarchitektur zur Verfügung.

## <a name="syntax"></a>Syntax

```
class AFX_NOVTABLE CHtmlEditDoc : public CDocument
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CHtmlEditDoc::CHtmlEditDoc](#chtmleditdoc)|Erstellt ein `CHtmlEditDoc`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CHtmlEditDoc::GetView](#getview)|Ruft das `CHtmlEditView` diesem Dokument zugeordnete Objekt ab.|
|[CHtmlEditDoc::IsModified](#ismodified)|Gibt zurück, ob das WebBrowser-Steuerelement der zugeordneten Ansicht ein Dokument enthält, das vom Benutzer geändert wurde.|
|[CHtmlEditDoc::OpenURL](#openurl)|Öffnet eine URL.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

`CHtmlEditDoc`

## <a name="requirements"></a>Anforderungen

**Header:** afxhtml.h

## <a name="chtmleditdocchtmleditdoc"></a><a name="chtmleditdoc"></a>CHtmlEditDoc::CHtmlEditDoc

Erstellt ein `CHtmlEditDoc`-Objekt.

```
CHtmlEditDoc();
```

## <a name="chtmleditdocgetview"></a><a name="getview"></a>CHtmlEditDoc::GetView

Ruft das [CHtmlEditView-Objekt](../../mfc/reference/chtmleditview-class.md) ab, das diesem Dokument zugeordnet ist.

```
virtual CHtmlEditView* GetView() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf das `CHtmlEditView` Dokumentobjekt zurück.

## <a name="chtmleditdocismodified"></a><a name="ismodified"></a>CHtmlEditDoc::IsModified

Gibt zurück, ob das WebBrowser-Steuerelement der zugeordneten Ansicht ein Dokument enthält, das vom Benutzer geändert wurde.

```
virtual BOOL IsModified();
```

## <a name="chtmleditdocopenurl"></a><a name="openurl"></a>CHtmlEditDoc::OpenURL

Öffnet eine URL.

```
virtual BOOL OpenURL(LPCTSTR lpszURL);
```

### <a name="parameters"></a>Parameter

*lpszURL*<br/>
Die zu öffnende URL.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

## <a name="see-also"></a>Siehe auch

[HTMLEdit-Beispiel](../../overview/visual-cpp-samples.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
