---
title: ATL-Registrar und BNF-Syntax (Backus-Naur-Form)
ms.date: 05/14/2019
helpviewer_keywords:
- BNF notation
- Backus-Naur form (BNF) syntax
ms.assetid: 994bbef0-9077-4aa8-bdfe-b7e830af9acc
ms.openlocfilehash: 0f07a39863b586d524d060dc3df7117e2c930b3e
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168708"
---
# <a name="understanding-backus-naur-form-bnf-syntax"></a>Einführung in die BNF-Syntax (Backus-Naur-Form)

Die vom ATL-Registrar verwendeten Skripts sind in diesem Thema mit der BNF-Syntax beschrieben, für die die in der folgenden Tabelle aufgeführte Notation verwendet wird.

|Konvention/Symbol|Bedeutung|
|------------------------|-------------|
|::=|Entsprechung|
|&#124;|oder|
|X+|Mindestens ein X.|
|\[X]|X ist optional. Optionale Trennzeichen sind durch \[] gekennzeichnet.|
|Jeglicher **fett** ausgezeichnete Text|Ein Zeichenfolgenliteral.|
|Jeglicher *kursiv* ausgezeichnete Text|Art und Weise, wie das Zeichenfolgenliteral erstellt wird.|

Wie in der obigen Tabelle angegeben ist, werden für Registrar-Skripts Zeichenfolgenliterale verwendet. Diese Werte sind tatsächlich Text, der in Ihrem Skript vorhanden muss. In der folgende Tabelle sind die Zeichenfolgenliterale beschrieben, die in einem ATL-Registrar-Skript verwendet werden.

|Zeichenfolgenliteral|Aktion|
|--------------------|------------|
|**"ForceRemove"**|Entfernt den nächsten Schlüssel (sofern vorhanden) vollständig und erstellt diesen dann neu.|
|**NoRemove**|Entfernt den nächsten Schlüssel beim Aufheben der Registrierung nicht.|
|**ster**|Gibt an, dass `<Key Name>` tatsächlich ein benannter Wert ist.|
|**Löschen**|Löscht den nächsten Schlüssel während der Registrierung.|
|**Hymnen**|Gibt an, dass der nächste Wert eine Zeichenfolge (REG_SZ) ist.|
|**d**|Gibt an, dass der nächste Wert ein DWORD-Wert (REG_DWORD) ist.|
|**800**|Gibt an, dass der nächste Wert eine mehrteilige Zeichenfolge (REG_MULTI_SZ) ist.|
|**b**|Gibt an, dass der nächste Wert ein Binärwert (REG_BINARY) ist.|

## <a name="bnf-syntax-examples"></a>Beispiele für die BNF-Syntax

Es folgen einige Syntaxbeispiele, die Ihnen verdeutlichen sollen, wie die Notation und die Zeichenfolgenliterale in einem ATL-Registrar-Skript funktionieren.

### <a name="syntax-example-1"></a>Syntaxbeispiel 1

> \<Registrierungs Ausdruck>:: = \<Schlüssel hinzufügen>

gibt an, dass `registry expression` mit `Add Key` identisch ist.

### <a name="syntax-example-2"></a>Syntaxbeispiel 2

> \<Registrierungs Ausdruck>:: = \<Key> hinzufügen | \<Schlüssel> löschen

gibt an, dass `registry expression` entweder mit `Add Key` oder mit `Delete Key` identisch ist.

### <a name="syntax-example-3"></a>Syntaxbeispiel 3

> \<Schlüssel Name>:: = '\<alphanumerisches>+ '

Gibt an `Key Name` , dass einem oder mehreren `AlphaNumeric` Werten entspricht.

### <a name="syntax-example-4"></a>Syntaxbeispiel 4

> \<Schlüssel hinzufügen>:: = [**ForceRemove** | **NoRemove** | **Val**]\<Schlüssel Name>

gibt an, dass `Add Key` mit `Key Name` identisch ist, und dass die Zeichenfolgenliterale `ForceRemove`, `NoRemove` und `val` optional sind.

### <a name="syntax-example-5"></a>Syntaxbeispiel 5

> \<Alphanumerisches>:: = *beliebiges Zeichen ungleich NULL,* d. h. ASCII 0

gibt an, dass `AlphaNumeric` mit jedem Nicht-NULL-Zeichen identisch ist.

### <a name="syntax-example-6"></a>Syntaxbeispiel 6

```rgs
val 'testmulti' = m 'String 1\0String 2\0'
```

gibt an, dass der Schlüsselname `testmulti` eine mehrteilige Zeichenfolge ist, die aus `String 1` und `String 2` besteht.

### <a name="syntax-example-7"></a>Syntaxbeispiel 7

```rgs
val 'testhex' = d '&H55'
```

gibt an, dass der Schlüsselname `testhex` ein DWORD-Wert ist, der auf hexadezimal 55 (dezimal 85) festgelegt ist. Beachten Sie, dass dieses Format der **&H**-Notation entspricht, wie sie in der Visual Basic-Spezifikation enthalten ist.

## <a name="see-also"></a>Weitere Informationen:

[Erstellen von Registrierungs Skripts](../atl/creating-registrar-scripts.md)
