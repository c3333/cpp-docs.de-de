---
title: type_info-Klasse
ms.date: 11/04/2016
f1_keywords:
- type_info
helpviewer_keywords:
- class type_info
- type_info class
ms.assetid: 894ddda2-7de4-4da3-9404-d2c74e356c16
ms.openlocfilehash: 7a016fe8fee4e5765e6172184bfa9c90eecbc687
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160670"
---
# <a name="type_info-class"></a>type_info-Klasse

Die **Type_info** -Klasse beschreibt Typinformationen, die vom Compiler innerhalb des Programms generiert werden. Objekte dieser Klasse speichern effektiv einen Zeiger auf einen Namen für den Typ. Die **Type_info** -Klasse speichert außerdem einen codierten Wert, der für den Vergleich von zwei Typen auf Gleichheit oder Sortierreihenfolge geeignet ist. Die Codierungsregeln und die Sortierreihenfolge für Typen sind nicht spezifiziert und können je nach Programm unterschiedlich sein.

Die `<typeinfo>` Header Datei muss eingeschlossen werden, damit die **Type_info** -Klasse verwendet werden können. Die Schnittstelle für die **Type_info** -Klasse lautet wie folgt:

```cpp
class type_info {
public:
    type_info(const type_info& rhs) = delete; // cannot be copied
    virtual ~type_info();
    size_t hash_code() const;
    _CRTIMP_PURE bool operator==(const type_info& rhs) const;
    type_info& operator=(const type_info& rhs) = delete; // cannot be copied
    _CRTIMP_PURE bool operator!=(const type_info& rhs) const;
    _CRTIMP_PURE int before(const type_info& rhs) const;
    size_t hash_code() const noexcept;
    _CRTIMP_PURE const char* name() const;
    _CRTIMP_PURE const char* raw_name() const;
};
```

Objekte der **Type_info** -Klasse können nicht direkt instanziiert werden, da die-Klasse nur über einen privaten Kopierkonstruktor verfügt. Die einzige Möglichkeit zum Erstellen eines (temporären) **Type_info** Objekts ist die Verwendung des [typeid](../cpp/typeid-operator.md) -Operators. Da der Zuweisungs Operator auch privat ist, können Sie keine Objekte der Klasse **Type_info**kopieren oder zuweisen.

`type_info::hash_code` definiert eine Hash Funktion, die für die Zuordnung von Werten vom Typ **TypeInfo** zu einer Verteilung von Indexwerten geeignet ist.

Die Operatoren `==` und `!=` können verwendet werden, um auf Gleichheit und Ungleichheit mit anderen **Type_info** Objekten zu vergleichen.

Es gibt keine Verbindung zwischen der Sortierreihenfolge von Typen und Vererbungsbeziehungen. Verwenden Sie die `type_info::before` Member-Funktion, um die Sortierreihenfolge von Typen zu bestimmen. Es gibt keine Garantie, dass `type_info::before` in verschiedenen Programmen oder sogar unterschiedlichen Ausführungen desselben Programms dasselbe Ergebnis liefert. Auf diese Weise ähnelt `type_info::before` dem address-of `(&)`-Operator.

Die `type_info::name` Member-Funktion gibt eine `const char*` an eine NULL-terminierte Zeichenfolge zurück, die den lesbaren Namen des Typs darstellt. Der Speicher, auf den gezeigt wird, wird zwischengespeichert und sollte nie direkt freigegeben werden.

Die `type_info::raw_name` Member-Funktion gibt eine `const char*` an eine NULL-terminierte Zeichenfolge zurück, die den ergänzten Namen des Objekt Typs darstellt. Der Name wird tatsächlich in seiner ergänzten Form gespeichert, um Platz zu sparen. Folglich ist diese Funktion schneller als `type_info::name`, da Sie nicht den Namen entzieren muss. Die von der `type_info::raw_name`-Funktion zurückgegebene Zeichenfolge ist in Vergleichs Vorgängen nützlich, aber nicht lesbar. Wenn Sie eine lesbare Zeichenfolge benötigen, verwenden Sie stattdessen die `type_info::name`-Funktion.

Typinformationen werden nur für polymorphe Klassen generiert, wenn die [/gr-Compileroption (Lauf Zeittyp Informationen aktivieren)](../build/reference/gr-enable-run-time-type-information.md) angegeben wird.

## <a name="see-also"></a>Weitere Informationen

[Laufzeit-Typinformationen](../cpp/run-time-type-information.md)
