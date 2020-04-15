---
title: Zugreifen auf die Typbibliothek
ms.date: 11/04/2016
helpviewer_keywords:
- type libraries [MFC], accessing
ms.assetid: a03fa7f0-86c2-4119-bf81-202916fb74b3
ms.openlocfilehash: 1794e16489ab48d919bbd4116588fba4b74b88d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372873"
---
# <a name="type-library-access"></a>Zugreifen auf die Typbibliothek

Typbibliotheken machen die Schnittstellen eines OLE-Steuerelements für andere OLE-fähige Anwendungen verfügbar. Jedes OLE-Steuerelement muss über eine Typbibliothek verfügen, wenn eine oder mehrere Schnittstellen verfügbar gemacht werden sollen.

Die folgenden Makros ermöglichen es einem OLE-Steuerelement, Zugriff auf seine eigene Typbibliothek zu gewähren:

### <a name="type-library-access"></a>Zugreifen auf die Typbibliothek

|||
|-|-|
|[DECLARE_OLETYPELIB](#declare_oletypelib)|Deklariert `GetTypeLib` eine Memberfunktion eines OLE-Steuerelements (muss in der Klassendeklaration verwendet werden).|
|[IMPLEMENT_OLETYPELIB](#implement_oletypelib)|Implementiert eine `GetTypeLib` Memberfunktion eines OLE-Steuerelements (muss in der Klassenimplementierung verwendet werden).|

## <a name="declare_oletypelib"></a><a name="declare_oletypelib"></a>DECLARE_OLETYPELIB

Deklariert `GetTypeLib` die Memberfunktion Ihrer Steuerelementklasse.

```
DECLARE_OLETYPELIB(class_name)
```

### <a name="parameters"></a>Parameter

*Class_name*<br/>
Der Name der Steuerelementklasse, die sich auf die Typbibliothek bezieht.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro in der Headerdatei der Steuerklassen.

### <a name="requirements"></a>Anforderungen

**Header:** afxdisp.h

## <a name="implement_oletypelib"></a><a name="implement_oletypelib"></a>IMPLEMENT_OLETYPELIB

Implementiert die Memberfunktion `GetTypeLib` des Steuerelements.

```
IMPLEMENT_OLETYPELIB(class_name, tlid, wVerMajor,  wVerMinor)
```

### <a name="parameters"></a>Parameter

*Class_name*<br/>
Der Name der Steuerelementklasse, die sich auf die Typbibliothek bezieht.

*tlid*<br/>
Die ID-Nummer der Typbibliothek.

*wVerMajor*<br/>
Die Hauptversionsnummer der Typbibliothek.

*wVerMinor*<br/>
Die Typbibliothek Nebenversionsnummer.

### <a name="remarks"></a>Bemerkungen

Dieses Makro muss in der Implementierungsdatei für jede Steuerelementklasse angezeigt werden, die das DECLARE_OLETYPELIB-Makro verwendet.

### <a name="requirements"></a>Anforderungen

**Header:** afxdisp.h

## <a name="see-also"></a>Siehe auch

[MFC-Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md)
