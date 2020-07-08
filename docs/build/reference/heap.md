---
title: /HEAP
description: Die Option MSVC linker oder EDITBIN/Heap legt die gesamte Heap Größe und optional die Größe zusätzlicher Heap Blöcke fest.
ms.date: 07/07/2020
f1_keywords:
- /heap
helpviewer_keywords:
- heap allocation, setting heap size
- HEAP editbin option
- -HEAP editbin option
- /HEAP editbin option
ms.assetid: 6ce759b5-75b7-44ff-a5fd-3a83a0ba9a48
ms.openlocfilehash: 7976ae2927ca731c83fa42e87da182fee4df3d7c
ms.sourcegitcommit: e17cc8a478b51739d67304d7d82422967b35f716
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/08/2020
ms.locfileid: "86127834"
---
# `/HEAP`

Legt die Größe des Heaps in Bytes fest. Diese Option gilt nur für ausführbare Dateien.

## <a name="syntax"></a>Syntax

> **`/HEAP:`**_`reserve`_\[**`,`**_`commit`_]

## <a name="remarks"></a>Bemerkungen

Das- *`reserve`* Argument gibt die gesamte anfängliche Heap Zuordnung im virtuellen Speicher an. Die **`/HEAP`** Linkeroption oder die [EDITBIN](editbin-reference.md) -Option rundet den angegebenen Wert auf das nächste Vielfache von 4 Bytes auf. Standardmäßig beträgt die Heapgröße 1 MB.

Das optionale *`commit`* Argument unterliegt der Interpretation durch das Betriebssystem. Unter einem Windows-Betriebssystem gibt es die anfängliche Menge an physischem Speicher an, die belegt werden soll. Außerdem wird angegeben, wie viel Arbeitsspeicher beim Erweitern des Heaps belegt werden soll. Die Zusicherung von virtuellem Speicher bewirkt die Belegung von Speicher in der Auslagerungsdatei. Ein höherer *`commit`* Wert ermöglicht dem System, Arbeitsspeicher seltener zuzuweisen, wenn die APP mehr Heap Speicher benötigt, aber die Speicheranforderungen und möglicherweise die Startzeit der APP erhöht. Der *`commit`* Wert muss kleiner oder gleich dem *`reserve`* Wert sein. Der Standardwert ist 4 KB.

Geben Sie den *`reserve`* -Wert und den- *`commit`* Wert in der hexadezimalen oder oktalen Schreibweise Dezimaltrennzeichen, C-Sprache Beispielsweise kann ein Wert von 1 MB als 1048576 in Dezimal oder als 0x100000 im Hexadezimal Format oder als 04000000 im Oktal angegeben werden. Die Standardwerte sind gleichwertig mit der-Option **`/HEAP:1048576,4096`** .

### <a name="example"></a>Beispiel

Mit diesem Beispiel Link Befehl wird eine ausführbare *main.exe* erstellt, die über eine Heap Reserve von 2 MB verfügt. Der anfängliche Heap und spätere Heap Erweiterungen werden in Blöcken von 64 KB angezeigt:

**`link /heap:0x200000,0x10000 main.obj`**

### <a name="to-set-this-linker-option-in-visual-studio"></a>So legen Sie diese Linkeroption in Visual Studio fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften**Seite für das  >  **Linker**  >  **System** der Konfigurations Eigenschaften aus.

1. Legen Sie die Eigenschaften **Heap Reserve Größe** und **Heap-Commitgröße** fest, und wählen Sie dann **OK** oder **anwenden** aus, um die Änderungen zu speichern.

## <a name="see-also"></a>Weitere Informationen

[EDITBIN-Optionen](editbin-options.md)\
[Linkeroptionen](linker-options.md)
