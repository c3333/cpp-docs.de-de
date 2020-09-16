---
title: Hinzufügen einer Memberfunktion
ms.date: 11/09/2018
f1_keywords:
- vc.codewiz.classes.member.function
- vc.codewiz.function.overview
helpviewer_keywords:
- member functions, adding to classes
- classes [C++], adding members
- add member function wizard [C++]
ms.assetid: 55b25ddb-541d-44ed-957c-974ef91cfc85
ms.openlocfilehash: 0e63771e3e01c3829e20d2fe62fa2caf0f8b26f5
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040781"
---
# <a name="add-a-member-function"></a>Hinzufügen einer Memberfunktion

In der **Klassenansicht** können Sie einer beliebigen Klasse eine Memberfunktion hinzufügen. Dabei wird der Headerdatei eine Deklaration und der Implementierungsdatei der Klasse ein Stub-Memberfunktionsrumpf hinzugefügt. Die hinzugefügten Elemente können anschließend bearbeitet werden.

**So fügen Sie einer Klasse eine Memberfunktion hinzu:**

1. Erweitern Sie in der **Klassenansicht** den Projektknoten, um die Projektklassen anzuzeigen. (Öffnen Sie die **Klassenansicht**, indem Sie in der Menüleiste auf **Ansicht** und **Klassenansicht** klicken.)

1. Öffnen Sie das Kontextmenü für die Klasse, der eine Memberfunktion hinzugefügt werden soll, und klicken Sie dann auf **Hinzufügen** und **Funktion hinzufügen**.

1. Geben Sie die entsprechenden Informationen zur Memberfunktion an. Weitere Informationen finden Sie unter [Assistent zum Hinzufügen von Memberfunktionen](#add-member-function-wizard).

1. Klicken Sie auf die Schaltfläche **Fertigstellen**, um den Code der Memberfunktion zu erstellen.

## <a name="in-this-section"></a>In diesem Abschnitt

- [Assistent zum Hinzufügen von Memberfunktionen](#add-member-function-wizard)

## <a name="add-member-function-wizard"></a>Assistent zum Hinzufügen von Memberfunktionen

Dieser Assistent fügt der Headerdatei eine Memberfunktionsdeklaration hinzu. Außerdem fügt er der Implementierungsdatei für die ausgewählte Klasse eine Stubmemberfunktion für die Implementierung hinzu.

Sobald Sie mithilfe des Assistenten eine Memberfunktion hinzugefügt haben, können Sie den Code in der Entwicklungsumgebung bearbeiten.

- **Rückgabetyp**

  Legt den Rückgabetyp für die hinzugefügte Memberfunktion fest. Sie können einen eigenen Rückgabetyp bereitstellen oder einen aus der Liste der verfügbaren Typen auswählen. Weitere Informationen zu Typen finden Sie unter [Grundlegende Typen](../cpp/fundamental-types-cpp.md).

:::row:::
   :::column span="":::
      **`char`**\
      **`double`**\
      **`float`**\
      **`int`**
   :::column-end:::
   :::column span="":::
      **`long`**\
      **`short`**\
      **`unsigned char`**\
      **`unsigned int`**
   :::column-end:::
   :::column span="":::
      **`unsigned long`**\
      **`void`**\
      `HRESULT`
   :::column-end:::
:::row-end:::

- **Funktionsname**

  Legt den Namen der hinzugefügten Memberfunktion fest.

- **Parametertyp**

  Legt den Parametertyp fest, den Sie für die Memberfunktion hinzufügen, falls diese über Parameter verfügt. Sie können einen eigenen Parametertyp bereitstellen oder einen aus der Liste der verfügbaren Typen auswählen.

:::row:::
   :::column span="":::
      **`char`**\
      **`double`**\
      **`float`**
   :::column-end:::
   :::column span="":::
      **`int`**\
      **`long`**\
      **`short`**
   :::column-end:::
   :::column span="":::
      **`unsigned char`**\
      **`unsigned int`**\
      **`unsigned long`**
   :::column-end:::
:::row-end:::

- **Parametername**

  Legt die Parameternamen fest, die Sie für die Memberfunktion hinzufügen, falls diese über Parameter verfügt.

- **Parameterliste**

  Zeigt eine Liste der Parameter an, die Sie zur Memberfunktion hinzugefügt haben. Wenn Sie einen Parameter zur Liste hinzufügen möchten, geben Sie einen Typ und einen Namen in die Felder **Parametertyp** und **Parametername** ein, und klicken Sie auf **Hinzufügen**. Wenn Sie einen Parameter aus der Liste entfernen möchten, wählen Sie diesen aus, und klicken Sie auf **Entfernen**.

- **Zugriff**

  Legt den Zugriff auf die Memberfunktion fest. Bei Zugriffsmodifizierern handelt es sich um Schlüsselwörter, die den Zugriff festlegen, den andere Klassen auf die Memberfunktion haben. Weitere Informationen zum Festlegen des Zugriffs finden Sie unter [Memberzugriffssteuerung](../cpp/member-access-control-cpp.md). Standardmäßig ist die Zugriffsebene von Memberfunktionen auf **`public`** festgelegt.

  - [public](../cpp/public-cpp.md)
  - [protected](../cpp/protected-cpp.md)
  - [private](../cpp/private-cpp.md)

  Überprüfen Sie, ob die neue Memberfunktion „static“ oder „virtual“ ist und ob diese „inline“ oder „pure“ ist. Wenn Sie die Memberfunktion auf „pure“ festlegen, wird das Kontrollkästchen **Virtual** aktiviert, und das Kontrollkästchen **Inline** wird deaktiviert. Standardmäßig sind Memberfunktionen nicht „static“ und nicht „virtual“.

  | Option | Beschreibung |
  |--------|-------------|
  | [Static](../cpp/storage-classes-cpp.md) |  Gibt an, dass die Funktion sich wie eine globale Funktion verhält und außerhalb der Klasse aufgerufen werden kann, auch wenn die Klasse nicht instanziiert wird. Die Memberfunktion hat keinen Zugriff auf nicht statische Members. Eine Memberfunktion, die als `Static` angegeben ist, kann nicht „virtual“ sein. |
  | [Virtual](../cpp/virtual-cpp.md) | Stellt sicher, dass die richtige Memberfunktion für ein Objekt aufgerufen wird, und zwar unabhängig von dem Ausdruck, mit dem der Aufruf der Memberfunktion erfolgt. Eine Memberfunktion, die als `Virtual` angegeben ist, kann nicht „static“ sein. |
  | **Pure** | Gibt an, dass für die deklarierte virtuelle Memberfunktion keine Implementierung bereitgestellt wird. **Pure** kann nur für die virtuellen Memberfunktionen angegeben werden. Eine Klasse, die mindestens eine rein virtuelle Memberfunktion enthält, wird als abstrakte Klasse angesehen. Klassen, die von der abstrakten Klasse abgeleitet sind, müssen die rein virtuelle Memberfunktion implementieren, um nicht selbst als abstrakte Klasse angesehen zu werden. |
  | [Inline](../cpp/inline-functions-cpp.md) | Weist den Compiler an, eine Kopie des Memberfunktionstexts an jeder Stelle einzufügen, an der die Memberfunktion aufgerufen wird. Eine Memberfunktion, die als **Inline** angegeben ist, kann nicht „pure“ sein. |

- **CPP-Datei**

  Legt den Speicherort der Datei fest, in die die Implementierung der Stub-Memberfunktion geschrieben wird. Standardmäßig wird diese in die CPP-Datei der Klasse geschrieben, zu der die Memberfunktion hinzugefügt wird. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten, um den Dateinamen zu ändern. Die Implementierung der Memberfunktion wird den Inhalten der ausgewählten Datei hinzugefügt.

- **Kommentar**

  Fügt einen Kommentar zur Headerdatei der Memberfunktion hinzu.

- **Funktionssignatur**

  Zeigt die Memberfunktion aus dem Code unverändert an, wenn Sie auf **Fertig stellen** klicken. Sie können den Text in diesem Feld nicht bearbeiten. Ändern Sie die entsprechenden Felder im Assistenten, wenn Sie die Memberfunktion ändern möchten.
