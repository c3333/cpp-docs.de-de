---
title: _U_STRINGorID-Klasse
ms.date: 11/04/2016
f1_keywords:
- ATL._U_STRINGorID
- ATL::_U_STRINGorID
- _U_STRINGorID
helpviewer_keywords:
- _U_STRINGorID class
- U_STRINGorID class
ms.assetid: 443cdc00-d265-4b27-8ef3-2feb95f3e5e3
ms.openlocfilehash: 4e46ceec077b8daf8ef2a76110d2fc19dd39ae26
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325823"
---
# <a name="_u_stringorid-class"></a>_U_STRINGorID-Klasse

Mit dieser Argumentadapterklasse können entweder Ressourcennamen (LPCTSTRs) oder Ressourcen-IDs (UINTs) an eine Funktion übergeben werden, ohne dass der Aufrufer die ID mithilfe des MAKEINTRESOURCE-Makros in eine Zeichenfolge konvertieren muss.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
class _U_STRINGorID
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[_U_STRINGorID::_U_STRINGorID](#_u_stringorid___u_stringorid)|Der Konstruktor.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[_U_STRINGorID::m_lpstr](#_u_stringorid__m_lpstr)|Der Ressourcenbezeichner.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse wurde für die Implementierung von Wrappern für die Windows-Ressourcenverwaltungs-API entwickelt, z. B. die Funktionen [FindResource](/windows/win32/api/winbase/nf-winbase-findresourcea), [LoadIcon](/windows/win32/api/winuser/nf-winuser-loadiconw)und [LoadMenu,](/windows/win32/api/winuser/nf-winuser-loadmenuw) die ein LPCTSTR-Argument akzeptieren, das entweder der Name einer Ressource oder ihre ID sein kann.

Die Klasse definiert zwei Konstruktorüberladungen: eine akzeptiert ein LPCTSTR-Argument und die andere ein UINT-Argument. Das UINT-Argument wird mithilfe des MAKEINTRESOURCE-Makros und des im einzelnen Datenmember der Klasse, [m_lpstr,](#_u_stringorid__m_lpstr)gespeicherten Ergebnisses in einen Ressourcentyp konvertiert, der mit Windows-Ressourcenverwaltungsfunktionen kompatibel ist. Das Argument für den LPCTSTR-Konstruktor wird direkt ohne Konvertierung gespeichert.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="_u_stringoridm_lpstr"></a><a name="_u_stringorid__m_lpstr"></a>_U_STRINGorID::m_lpstr

Die Klasse enthält den Wert, der an einen ihrer Konstruktoren übergeben wird, als öffentliches LPCTSTR-Datenmember.

```
LPCTSTR m_lpstr;
```

## <a name="_u_stringorid_u_stringorid"></a><a name="_u_stringorid___u_stringorid"></a>_U_STRINGorID::_U_STRINGorID

Der UINT-Konstruktor konvertiert sein Argument mithilfe des MAKEINTRESOURCE-Makros in einen Ressourcentyp, der mit Windows-Ressourcenverwaltungsfunktionen kompatibel ist, und das Ergebnis wird im einzelnen Datenmember der [Klasse, m_lpstr](#_u_stringorid__m_lpstr)gespeichert.

```
_U_STRINGorID(UINT nID);
_U_STRINGorID(LPCTSTR lpString);
```

### <a name="parameters"></a>Parameter

*nID*<br/>
Eine Ressourcen-ID.

*lpString*<br/>
Ein Ressourcenname.

### <a name="remarks"></a>Bemerkungen

Das Argument für den LPCTSTR-Konstruktor wird direkt ohne Konvertierung gespeichert.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)
