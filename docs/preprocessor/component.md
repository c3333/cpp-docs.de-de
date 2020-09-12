---
title: component-Pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.component
- component_CPP
helpviewer_keywords:
- component pragma
- pragmas, component
ms.assetid: 7b66355e-3201-4c14-8190-f4a2a81a604a
ms.openlocfilehash: 73b308fdc426be9b403b808d4e638b4f5c1e9149
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040729"
---
# <a name="component-pragma"></a>component-Pragma

Steuert die Auflistung von Browseinformationen oder Abhängigkeitsinformationen in Quelldateien.

## <a name="syntax"></a>Syntax

> **#pragma Komponente (Browser,** { **on** \| **Off** } \[ **,** **Verweise** \[ **,** *Name* ]] **)** \
> **#pragma Komponente (minrebuild,** { **on** \| **Off** } **)** \
> **#pragma Komponente (mintypeingefo,** { **on** \| **Off** } **)**

## <a name="remarks"></a>Bemerkungen

### <a name="browser"></a>Browser

Sie können das Sammeln aktivieren oder deaktivieren, und Sie können angeben, dass bestimmte Namen beim Sammeln von Informationen ignoriert werden.

Die Aktivierung oder Deaktivierung steuert das Sammeln von Browserinformationen ab dem nächsten Pragma. Beispiel:

```cpp
#pragma component(browser, off)
```

Dieser Code stoppt das Sammeln von Browserinformationen durch den Compiler.

> [!NOTE]
> Um die Erfassung von Browseinformationen mit diesem Pragma zu [aktivieren, müssen zuerst die Informationen zum Durchsuchen aktiviert werden](../build/reference/building-browse-information-files-overview.md).

Die **References** -Option kann mit oder ohne das *Name* -Argument verwendet werden. Durch die Verwendung von **verweisen** ohne *Name* wird das Sammeln von verweisen ein-oder ausgeschaltet (Weitere Informationen zum Durchsuchen werden jedoch weiterhin gesammelt). Beispiel:

```cpp
#pragma component(browser, off, references)
```

Dieser Code stoppt das Sammeln von Verweisinformationen durch den Compiler.

Durch die Verwendung von **verweisen** mit *Name* und **Off** wird verhindert, dass Verweise auf den *Namen* im Fenster zum Durchsuchen von Informationen angezeigt Verwenden Sie die folgende Syntax, um Namen und Typen zu ignorieren, die für Sie nicht relevant sind, und die Größe von Browserinformationsdateien zu reduzieren. Beispiel:

```cpp
#pragma component(browser, off, references, DWORD)
```

ignoriert Verweise auf DWORD ab diesem Punkt. Sie können das Sammeln von Verweisen auf DWORD mithilfe von **auf**wieder aktivieren:

```cpp
#pragma component(browser, on, references, DWORD)
```

Dies ist die einzige Möglichkeit, das Sammeln von Verweisen auf den *Namen*fortzusetzen. Sie müssen den *Namen* , den Sie deaktiviert haben, explizit aktivieren.

Um zu verhindern, dass der Präprozessor den *Namen* erweitert (z. b. das Erweitern von NULL auf 0), müssen Sie die Anführungszeichen einfügen

```cpp
#pragma component(browser, off, references, "NULL")
```

### <a name="minimal-rebuild"></a>Minimale Neuerstellung

Das Feature veraltet [/GM (minimale Neuerstellung aktivieren)](../build/reference/gm-enable-minimal-rebuild.md) erfordert, dass der Compiler C++-Klassen Abhängigkeitsinformationen erstellt und speichert, die Speicherplatz benötigen. Um Speicherplatz zu sparen, können Sie `#pragma component( minrebuild, off )` immer dann verwenden, wenn Sie keine Abhängigkeitsinformationen erfassen müssen, beispielsweise in nicht ändernden Header Dateien. Fügen `#pragma component( minrebuild, on )` Sie nach der nicht ändernden Klasse ein, um die Abhängigkeits Sammlung wieder zu aktivieren.

### <a name="reduce-type-information"></a>Typinformationen verringern

Die- `mintypeinfo` Option reduziert die Debuginformationen für den angegebenen Bereich. Diese Informationen haben einen beträchtlichen Umfang und wirken sich auf PDB- und OBJ-Dateien aus. Sie können Klassen und Strukturen im mintypeinfo-Bereich nicht debuggen. Die Verwendung der mintypeinfo-Option kann hilfreich sein, um die folgende Warnung zu vermeiden:

```cmd
LINK : warning LNK4018: too many type indexes in PDB "filename", discarding subsequent type information
```

Weitere Informationen finden Sie in der Compileroption [/GM (minimale Neuerstellung aktivieren)](../build/reference/gm-enable-minimal-rebuild.md)  .

## <a name="see-also"></a>Weitere Informationen

[Pragma-Anweisungen und das __pragma-Schlüsselwort](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
