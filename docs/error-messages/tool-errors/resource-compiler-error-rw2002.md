---
title: 'Ressourcencompiler: Fehler RW2002'
ms.date: 11/04/2016
f1_keywords:
- RW2002
helpviewer_keywords:
- RW2002
ms.assetid: b1d1a49b-b50b-4b0b-9f09-c7762e2dbe8f
ms.openlocfilehash: 9c5c2824778a679627bd3008276849890f43ac7e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190689"
---
# <a name="resource-compiler-error-rw2002"></a>Ressourcencompiler: Fehler RW2002

Parsingfehler

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Dieser Fehler kann eine der folgenden Ursachen haben:

1. **Accelerator-Typ erforderlich (ASCII oder VIRTKEY)**

   Das `type` -Feld der **ACCELERATORS** -Anweisung muss entweder den ASCII- oder den VIRTKEY-Wert enthalten.

1. **BEGIN in Zugriffstasten Tabelle erwartet**

   Das **BEGIN** -Schlüsselwort muss direkt auf das **ACCELERATORS** -Schlüsselwort folgen.

1. **BEGIN in Dialogfeld erwartet**

   Das **Begin** -Schlüsselwort muss direkt auf das **Dialog** Schlüsselwort folgen.

1. **BEGIN in Menü erwartet**

   Das **BEGIN** -Schlüsselwort muss direkt auf das **MENU** -Schlüsselwort folgen.

1. **BEGIN in RCData erwartet**

   Das **BEGIN** -Schlüsselwort muss direkt auf das **RCDATA** -Schlüsselwort folgen.

1. **BEGIN-Schlüsselwort in Zeichen folgen Tabelle erwartet**

   Das **Begin** -Schlüsselwort muss direkt auf das **STRINGTABLE** -Schlüsselwort folgen.

1. **Zeichen folgen Konstanten können nicht wieder verwendet werden.**

   Der gleiche Wert wird in einer **STRINGTABLE** -Anweisung zweimal verwendet. Stellen Sie sicher, dass überlappende Dezimal-und hexadezimale Werte nicht gemischt werden. Jede ID in einer **STRINGTABLE** muss eindeutig sein. Verwenden Sie für maximale Effizienz zusammenhängende Konstanten, die auf einem Vielfachen von 16 starten.

1. **Steuerzeichen außerhalb des gültigen Bereichs [^ A-^ Z]**

   Ein Steuerzeichen in der **ACCELERATORS** -Anweisung ist ungültig. Das auf das Caretzeichen ( **^** ) folgende Zeichen muss zwischen A und Z (einschl.) liegen.

1. **Leere Menüs sind nicht zulässig.**

   Ein **End** -Schlüsselwort wird angezeigt, bevor beliebige Menü Elemente in der **Menü** Anweisung definiert werden. Der Ressourcen Compiler lässt keine leeren Menüs zu. Stellen Sie sicher, dass in der **Menü** Anweisung keine öffnenden Anführungszeichen vorhanden sind.

1. **Ende erwartet in Dialogfeld**

   Das **End** -Schlüsselwort muss am Ende einer **Dialog** Feld Anweisung auftreten. Stellen Sie sicher, dass keine offenen Anführungszeichen von der vorangehenden Anweisung übrig sind.

1. **Ende im Menü erwartet**

   Das **END** -Schlüsselwort muss am Ende einer **MENU** -Anweisung stehen. Stellen Sie sicher, dass keine öffnenden Anführungszeichen oder nicht übereinstimmende Paare von **BEGIN** - und **END** -Anweisungen vorhanden sind.

1. **Komma in Zugriffstasten Tabelle erwartet**

   Der Ressourcencompiler erfordert ein Komma zwischen dem Feld `event` und dem Feld *idvalue* in der **ACCELERATORS** -Anweisung.

1. **Name der Steuerelement Klasse erwartet**

   Das `class`-Feld einer **Steuer** Element Anweisung in der **Dialog** -Anweisung muss einen der folgenden Typen aufweisen: Button, ComboBox, Edit, ListBox, ScrollBar, static oder User-Defined. Stellen Sie sicher, dass die Klasse richtig geschrieben ist.

1. **Der Name der Schriftart wurde erwartet.**

   Das Feld *typeface* der FONT-Option in der **DIALOG** -Anweisung muss eine ASCII-Zeichenfolge in doppelten Anführungszeichen sein. Dieses Feld gibt den Namen einer Schriftart an.

1. **Erwarteter ID-Wert für MenuItem.**

   Die **MENU** -Anweisung muss ein *menuID* -Feld aufweisen, in dem der Name oder die Nummer angegeben ist, der bzw. die die Menüressource identifiziert.

1. **Erwartete Menü Zeichenfolge**

   Jede **MENUITEM** - und **POPUP** -Anweisung muss ein *Text* -Feld enthalten. Hierbei handelt es sich um eine Zeichenfolge in doppelten Anführungszeichen, die den Namen des Menüelements oder Popupmenüs angibt. Eine **MENUITEM SEPARATOR** -Anweisung erfordert keine Zeichenfolge in Anführungszeichen.

1. **Numerischer Befehls Wert erwartet.**

   Der Ressourcen Compiler hat ein numerisches *idValue* -Feld in der **Accelerators** -Anweisung erwartet. Stellen Sie sicher, dass Sie eine `#define` Konstante verwendet haben, um den Wert anzugeben, und dass die Konstante richtig geschrieben ist.

1. **Numerische Konstante in Zeichen folgen Tabelle erwartet**

   Eine in einer `#define` -Anweisung definierte numerische Konstante muss direkt auf das **BEGIN** -Schlüsselwort in einer **STRINGTABLE** -Anweisung folgen.

1. **Erwartete numerische Punktgröße**

   Das Feld *pointsize* der Option FONT in der Anweisung **DIALOG** muss ein ganzzahliger Punktgrößenwert sein.

1. **Numerische Dialog Konstante erwartet**

   Eine **Dialog** Feld Anweisung erfordert ganzzahlige Werte für die Felder *x, y, Width*und *height* . Stellen Sie sicher, dass diese Werte nach dem Schlüsselwort " **Dialog** " eingefügt werden und dass Sie nicht negativ sind.

1. **Erwartete Zeichenfolge in STRINGTABLE**

   Nach jedem *stringid* -Wert in einer **STRINGTABLE** -Anweisung wird eine Zeichenfolge erwartet.

1. **Erwarteter String-oder Constant Accelerator-Befehl**

   Der Ressourcencompiler konnte nicht bestimmen, welche Art von Schlüssel für die Zugriffstaste eingerichtet wurde. Das `event` -Feld in der **ACCELERATORS** -Anweisung ist möglicherweise ungültig.

1. **Anzahl für ID wird erwartet.**

   Es wird eine Zahl für das `id`-Feld einer Steuerelement Anweisung in der **Dialog** -Anweisung erwartet. Stellen Sie sicher, dass Sie über eine Zahl oder `#define`-Anweisung für die Steuerelement-ID verfügen

1. **Zeichenfolge in Anführungszeichen in Dialog Klasse erwartet**

   Das `class` -Feld der CLASS-Option in der **DIALOG** -Anweisung muss eine ganze Zahl oder eine Zeichenfolge, die in doppelte Anführungszeichen eingeschlossen ist, enthalten.

1. **Zeichenfolge in Anführungszeichen in Dialogfeld Titel erwartet**

   Das `captiontext` -Feld der CAPTION-Option in der **DIALOG** -Anweisung muss eine ASCII-Zeichenfolge in doppelten Anführungszeichen sein.

1. **Datei nicht gefunden: Dateiname**

   Die in der Befehlszeile des Ressourcencompilers angegebene Datei wurde nicht gefunden. Überprüfen Sie, ob die Datei in ein anderes Verzeichnis verschoben wurde und ob der Dateiname und der Pfad korrekt eingegeben wurden. Dateien werden mithilfe der **include** -Umgebungsvariablen oder der Visual Studio-Einstellung, falls verfügbar, gesucht.

1. **Schriftart Namen müssen Ordnungszahlen sein.**

   Das *pointsize* -Feld in der Font-Anweisung muss eine ganze Zahl und keine Zeichenfolge sein.

1. **Ungültige Zugriffstaste**

   Ein `event` -Feld in der **ACCELERATORS** -Anweisung wurde nicht erkannt oder ist mehr als zwei Zeichen lang.

1. **Ungültiger Accelerator-Typ (ASCII oder VIRTKEY)**

   Das `type` -Feld der **ACCELERATORS** -Anweisung muss entweder den ASCII- oder den VIRTKEY-Wert enthalten.

1. **Ungültiges Steuerzeichen**

   Ein Steuerzeichen in der **ACCELERATORS** -Anweisung ist ungültig. Ein gültiges Steuerzeichen besteht aus einem Buchstaben (nur), der einem Caretzeichen (^) folgt.

1. **Ungültiger Steuerungstyp**

   Jede Steuerelement Anweisung in einer **Dialog** Feld Anweisung muss eines der folgenden sein: CheckBox, ComboBox, Control, CTEXT, DEFPUSHBUTTON, EDITTEXT, GroupBox, Symbol, ListBox, LTEXT, PUSHBUTTON, RadioButton, rtext, ScrollBar. Stellen Sie sicher, dass diese Steuerungs Anweisungen richtig geschrieben sind.

1. **Ungültiger Typ**

   Der Ressourcentyp gehörte nicht zu den Typen, die in der Datei "Windows. h" definiert sind.

1. **Text Zeichenfolge oder Ordnungszahl im Steuerelement erwartet**

   Das *Textfeld* einer **Control** -Anweisung in der **Dialog** -Anweisung muss entweder eine Text Zeichenfolge oder ein Ordinalverweis auf den Typ des Steuer Elements sein. Wenn Sie eine Ordnungszahl verwenden, achten Sie darauf, eine `#define` -Anweisung für das Steuerelement zu verwenden.

1. **Klammern stimmen nicht überein.**

   Stellen Sie sicher, dass Sie alle geöffneten Klammern in der **Dialog** Feld Anweisung geschlossen haben.

1. **Unerwarteter Wert in RCDATA.**

   Die *raw-data* -Werte in der **RCDATA** -Anweisung müssen ganze Zahlen oder Zeichenfolgen und jeweils durch ein Komma voneinander getrennt sein. Stellen Sie sicher, dass Sie kein Komma oder Anführungszeichen um eine Zeichenfolge vergessen haben.

1. **Unbekannter Menü Untertyp.**

   Das Feld " *Element Definition* " der **Menü** Anweisung kann nur **MenuItem** -und **Popup** -Anweisungen enthalten.
