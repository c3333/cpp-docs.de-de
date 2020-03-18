---
title: /SECTION (EDITBIN)
ms.date: 11/04/2016
f1_keywords:
- /section_editbin
helpviewer_keywords:
- -SECTION editbin option
- SECTION editbin option
- alignment characters in sections
- /SECTION editbin option
ms.assetid: 4680ab4e-c984-4251-8241-93440cad7615
ms.openlocfilehash: 770e1d1c1cf288a7fe68f5bd076791d43f5b8572
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438913"
---
# <a name="section-editbin"></a>/SECTION (EDITBIN)

```
/SECTION:name[=newname][,attributes][alignment]
```

## <a name="remarks"></a>Bemerkungen

Mit dieser Option werden die Attribute eines Abschnitts geändert, wobei die Attribute überschrieben werden, die festgelegt wurden, als die Objektdatei für den Abschnitt kompiliert oder verknüpft wurde.

Geben Sie nach dem Doppelpunkt ( **:** ) den *Namen* des Abschnitts an. Um den Abschnittsnamen zu ändern, befolgen Sie den *Namen* mit einem Gleichheitszeichen (=) und einem *NewName* -Wert für den Abschnitt.

Um den `attributes`des Abschnitts festzulegen oder zu ändern, geben Sie ein Komma ( **,** ) gefolgt von einem oder mehreren Attribut Zeichen an. Um ein Attribut zu negieren, stellen Sie dem Zeichen ein Ausrufezeichen (!) voran. Die folgenden Zeichen geben Speicher Attribute an:

|attribute|Einstellung|
|---------------|-------------|
|c|code|
|d|entfernbare|
|e|Ausführbare Datei (executable)|
|i|initialisierte Daten|
|k|zwischen gespeicherter virtueller Speicher|
|m|Link entfernen|
|o|Link Informationen|
|p|ausgehter virtueller Arbeitsspeicher|
|r|Lesen|
|s|shared|
|u|nicht initialisierte Daten|
|w|Schreiben|

Geben Sie zum Steuern der *Ausrichtung*das Zeichen **A** gefolgt von einem der folgenden Zeichen an, um die Größe der Ausrichtung in Byte festzulegen, wie im folgenden dargestellt:

|Zeichen|Ausrichtungs Größe in Bytes|
|---------------|-----------------------------|
|1|1|
|2|2|
|4|4|
|8|8|
|p|16|
|t|32|
|s|64|
|x|keine Ausrichtung|

Geben Sie die `attributes` und die *Ausrichtungs* Zeichen als Zeichenfolge ohne Leerzeichen an. Bei den Zeichen wird Groß-/Kleinschreibung nicht beachtet.

## <a name="see-also"></a>Weitere Informationen

[EDITBIN-Optionen](editbin-options.md)
