---
title: Zugreifen auf die Typbibliothek
ms.date: 11/04/2016
helpviewer_keywords:
- type libraries [MFC], accessing
ms.assetid: a03fa7f0-86c2-4119-bf81-202916fb74b3
ms.openlocfilehash: 23d4675bd3638d2effd1b967f0729f9e70dac6de
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426192"
---
# <a name="type-library-access"></a>Zugreifen auf die Typbibliothek

Typbibliotheken machen die Schnittstellen eines OLE-Steuer Elements für andere OLE-fähige Anwendungen verfügbar. Jedes OLE-Steuerelement muss eine Typbibliothek aufweisen, wenn eine oder mehrere Schnittstellen verfügbar gemacht werden sollen.

Mit den folgenden Makros kann ein OLE-Steuerelement Zugriff auf seine eigene Typbibliothek bereitstellen:

### <a name="type-library-access"></a>Zugreifen auf die Typbibliothek

|||
|-|-|
|[DECLARE_OLETYPELIB](#declare_oletypelib)|Deklariert eine `GetTypeLib` Member-Funktion eines OLE-Steuer Elements (muss in der Klassen Deklaration verwendet werden).|
|[IMPLEMENT_OLETYPELIB](#implement_oletypelib)|Implementiert eine `GetTypeLib` Member-Funktion eines OLE-Steuer Elements (muss in der Klassen Implementierung verwendet werden).|

##  <a name="declare_oletypelib"></a>DECLARE_OLETYPELIB

Deklariert die `GetTypeLib` Member-Funktion der Steuerelement Klasse.

```
DECLARE_OLETYPELIB(class_name)
```

### <a name="parameters"></a>Parameter

*class_name*<br/>
Der Name der Steuerelement Klasse, die mit der Typbibliothek verknüpft ist.

### <a name="remarks"></a>Hinweise

Verwenden Sie dieses Makro in der Header Datei der Steuerelement Klasse.

### <a name="requirements"></a>Voraussetzungen

**Header:** afxdisp.h

##  <a name="implement_oletypelib"></a>IMPLEMENT_OLETYPELIB

Implementiert die `GetTypeLib` Member-Funktion des Steuer Elements.

```
IMPLEMENT_OLETYPELIB(class_name, tlid, wVerMajor,  wVerMinor)
```

### <a name="parameters"></a>Parameter

*class_name*<br/>
Der Name der Steuerelement Klasse, die mit der Typbibliothek verknüpft ist.

*tlid*<br/>
Die ID-Nummer der Typbibliothek.

*wvermajor*<br/>
Die Hauptversionsnummer der Typbibliothek.

*wverminor*<br/>
Die neben Versionsnummer der Typbibliothek.

### <a name="remarks"></a>Hinweise

Dieses Makro muss in der Implementierungs Datei für jede Steuerelement Klasse, die das DECLARE_OLETYPELIB-Makro verwendet, angezeigt werden.

### <a name="requirements"></a>Voraussetzungen

**Header:** afxdisp.h

## <a name="see-also"></a>Siehe auch

[Makros und Globals](../../mfc/reference/mfc-macros-and-globals.md)
