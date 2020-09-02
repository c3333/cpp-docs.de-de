---
title: /CETCOMPAT (mit Stapel Schatten Stapel kompatibel)
ms.date: 09/01/2020
f1_keywords:
- /CETCOMPAT
helpviewer_keywords:
- /CETCOMPAT linker option
- /CETCOMPAT
ms.openlocfilehash: 7de7c2007c29769cb3ac8f89d07de8b00bf44c26
ms.sourcegitcommit: e58918c45316d799c1952ca7797a85adbcd0c472
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/01/2020
ms.locfileid: "89281825"
---
# <a name="cetcompat-cet-shadow-stack-compatible"></a>/CETCOMPAT (mit Stapel Schatten Stapel kompatibel)

Gibt an, ob ein ausführbares Bild als kompatibel mit dem Schattenstapel (Control-Flow Enforcement Technology) markiert werden soll.

## <a name="syntax"></a>Syntax

> **`/CETCOMPAT`**\
> **`/CETCOMPAT:NO`**

## <a name="arguments"></a>Argumente

**`NO`**<br/>
Gibt an, dass die ausführbare Datei nicht mit dem Stapel Schatten Stapel kompatibel sein soll.

## <a name="remarks"></a>Bemerkungen

Der Schatten Stapel für die Steuerung des Steuerungs Flusses (CET) ist eine Funktion des Computer Prozessors, die Funktionen zur Abwehr von auf der Basis von auf der Rückgabe orientierten Programmierung (auf der Grundlage von auf der Basis von Weitere Informationen finden Sie unter [Intel Control Flow Enforcement Technology Preview](https://software.intel.com/sites/default/files/managed/4d/2a/control-flow-enforcement-technology-preview.pdf).

Die **`/CETCOMPAT`** Linkeroption weist den Linker an, die Binärdatei als "für den Stapel Schatten Stapel kompatibel" zu markieren. **`/CETCOMPAT:NO`** markiert die Binärdatei als nicht kompatibel mit dem Stapel Schatten Stapel. Wenn beide Optionen in der Befehlszeile angegeben werden, wird der letzte angegebene verwendet. Dieser Switch ist zurzeit nur auf x86-und x64-Architekturen anwendbar.

Die **`/CETCOMPAT`** Option ist ab Visual Studio 2019 verfügbar.

### <a name="to-set-the-cetcompat-linker-option-in-visual-studio"></a>So legen Sie die `/CETCOMPAT` Linkeroption in Visual Studio fest

Ab Visual Studio 2019 Version 16,7:

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** für das Projekt. Weitere Informationen finden Sie unter [Working with Project Properties (Arbeiten mit Projekteigenschaften)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften**  >  **Linker**  >  Seite**Erweiterte** Eigenschaft Linker Linker aus.

1. Wählen Sie die Eigenschaft "für den **Stapel Schatten Stapel kompatibel** "

1. Wählen Sie im Dropdown-Steuerelement aus, ob **`Yes (/CETCOMPAT)`** die Binärdatei als "Stapel-Schatten Stapel kompatibel" markiert werden soll, oder **`No (/CETCOMPAT:NO)`** Markieren Sie Sie als nicht kompatibel.

In früheren Versionen von Visual Studio 2019:

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** für das Projekt. Weitere Informationen finden Sie unter [Working with Project Properties (Arbeiten mit Projekteigenschaften)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften**Seite für die  >  **Linker**  >  **Linkerbefehlszeile** der Configuration Properties

1. Fügen Sie im Bearbeitungs Steuerelement **zusätzliche Optionen** hinzu, *`/CETCOMPAT`* um die Binärdatei als "Stapel-Schatten Stapel kompatibel" zu markieren, oder, *`/CETCOMPAT:NO`* um Sie explizit als nicht kompatibel zu markieren.

### <a name="to-set-this-linker-option-programmatically"></a>So legen Sie diese Linkeroption programmgesteuert fest

Diese Option hat keine programmgesteuerte Entsprechung.

## <a name="see-also"></a>Weitere Informationen

[Linker-Optionen](linker-options.md)
