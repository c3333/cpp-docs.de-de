---
title: /CETCOMPAT (mit Stapel Schatten Stapel kompatibel)
ms.date: 02/19/2019
f1_keywords:
- /CETCOMPAT
helpviewer_keywords:
- /CETCOMPAT linker option
- /CETCOMPAT
ms.openlocfilehash: 2c807d91d69b967fd62e01a077711dede5f55c44
ms.sourcegitcommit: 7e011c68ca7547469544fac87001a33a37e1792e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2020
ms.locfileid: "84421299"
---
# <a name="cetcompat-cet-shadow-stack-compatible"></a>/CETCOMPAT (mit Stapel Schatten Stapel kompatibel)

Gibt an, ob ein ausführbares Bild als kompatibel mit dem Schattenstapel (Control-Flow Enforcement Technology) markiert werden soll.

## <a name="syntax"></a>Syntax

> **/CETCOMPAT** \[ **: Nein**]

## <a name="arguments"></a>Argumente

**Nein**<br/>
Gibt an, dass die ausführbare Datei nicht als kompatibel mit dem Stapel Schatten Stapel gekennzeichnet werden soll.

## <a name="remarks"></a>Bemerkungen

Der Schatten Stapel der Steuerungsdaten Fluss Erzwingung (CET) ist eine Funktion des Computer Prozessors, die Funktionen zur Abwehr von auf der Basis von auf der Rückgabe orientierten Programmierung (ROP) basierenden Schadsoftware Weitere Informationen finden Sie unter [Intel Control Flow Enforcement Technology Preview](https://software.intel.com/sites/default/files/managed/4d/2a/control-flow-enforcement-technology-preview.pdf).

Die **/CETCOMPAT** -Linkeroption weist den Linker an, die Binärdatei als "CET Shadow Stack-kompatibel" zu markieren. **/CETCOMPAT: Nein** kennzeichnet die Binärdatei nicht als nicht kompatibel mit dem Stapel Schatten Stapel. Wenn beide Optionen in der Befehlszeile angegeben werden, wird der letzte angegebene verwendet. Dieser Switch ist zurzeit nur auf x86-und x64-Architekturen anwendbar.

Die **/CETCOMPAT** -Option ist ab dem Visual Studio 2019 Preview 3-Toolset verfügbar.

### <a name="to-set-the-cetcompat-linker-option-in-visual-studio"></a>So legen Sie die Option "/CETCOMPAT Linker" in Visual Studio fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** für das Projekt. Weitere Informationen finden Sie unter [Working with Project Properties (Arbeiten mit Projekteigenschaften)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften**  >  **Linker**  >  Seite**Erweiterte** Eigenschaft Linker Linker aus.

1. Wählen Sie die Eigenschaft "für den **Stapel Schatten Stapel kompatibel** "

1. Wählen Sie im Dropdown-Steuerelement **Ja (/CETCOMPAT)** aus, um die eh-Fortsetzungs Metadaten zu aktivieren, oder **Nein (/CETCOMPAT: No)** , um es zu deaktivieren.


### <a name="to-set-this-linker-option-programmatically"></a>So legen Sie diese Linkeroption programmgesteuert fest

Diese Option hat keine programmgesteuerte Entsprechung.

## <a name="see-also"></a>Weitere Informationen

[Linker-Optionen](linker-options.md)
