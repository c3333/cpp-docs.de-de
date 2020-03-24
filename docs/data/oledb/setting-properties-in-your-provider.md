---
title: Festlegen von Eigenschaften im Anbieter
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB providers, properties
- properties [C++], OLE DB provider
ms.assetid: 26a8b493-7ec4-4686-96d0-9ad5d2bca5ac
ms.openlocfilehash: 905a9bb32544dbd7453d46362e100047516d22a8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209572"
---
# <a name="setting-properties-in-your-provider"></a>Festlegen von Eigenschaften im Anbieter

Suchen Sie die Eigenschaften Gruppe und die Eigenschaften-ID für die gewünschte Eigenschaft. Weitere Informationen finden Sie unter [OLE DB Eigenschaften](/previous-versions/windows/desktop/ms722734(v=vs.85)) in der **OLE DB Programmierer-Referenz**.

Suchen Sie in dem vom Assistenten generierten Anbieter Code die Eigenschaften Zuordnung, die der Eigenschaften Gruppe entspricht. Der Name der Eigenschaften Gruppe entspricht in der Regel dem Namen des Objekts. Befehls-und Rowseteigenschaften können im Befehl oder Rowset gefunden werden. Datenquellen-und Initialisierungs Eigenschaften finden Sie im Datenquellen Objekt.

Fügen Sie in der Eigenschaften Zuordnung ein [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md) Makro hinzu. PROPERTY_INFO_ENTRY_EX benötigt vier Parameter:

- Die eigen schafts-ID, die ihrer Eigenschaft entspricht. Entfernen Sie die ersten sieben Zeichen ("DBPROP_") von der Vorderseite des Eigenschaften namens. Wenn Sie z. b. `DBPROP_MAXROWS`hinzufügen möchten, übergeben Sie `MAXROWS` als erstes Element. Wenn dies eine benutzerdefinierte Eigenschaft ist, übergeben Sie den vollständigen GUID-Namen (z. b. `DBMYPROP_MYPROPERTY`).

- Der Varianttyp der Eigenschaft (in [OLE DB Eigenschaften](/previous-versions/windows/desktop/ms722734(v=vs.85)) in der **OLE DB Programmierer-Referenz**). Geben Sie den VT_ Typ (z. b. VT_BOOL oder VT_I2) ein, der dem Datentyp entspricht.

- Flags, die angeben, ob die Eigenschaft lesbar und beschreibbar ist, und die Gruppe, zu der Sie gehört. Der folgende Code zeigt z. b. eine Lese-/Schreibeigenschaft an, die der Rowsetgruppe angehört:

    ```cpp
    DBPROPFLAGS_ROWSET | DBPROPFLAGS_READ | DBPROPFLAGS_WRITE
    ```

- Der Basiswert der Eigenschaft. Dies kann z. b. `VARIANT_FALSE` für einen booleschen Typ oder NULL für einen ganzzahligen Typ sein. Die-Eigenschaft hat diesen Wert, es sei denn, Sie wird geändert.

    > [!NOTE]
    > Einige Eigenschaften sind mit anderen Eigenschaften verknüpft oder verkettet, z. b. Lesezeichen oder Aktualisierungen. Wenn ein Consumer eine Eigenschaft auf true festlegt, kann auch eine andere Eigenschaft festgelegt werden. Die OLE DB Anbieter Vorlagen unterstützen dies über die Methode " [cutlpropertychanged](../../data/oledb/cutlprops-onpropertychanged.md)".

## <a name="properties-ignored-by-microsoft-ole-db-providers"></a>Eigenschaften, die von Microsoft OLE DB-Anbietern ignoriert werden

Die Microsoft OLE DB-Anbieter ignorieren die folgenden OLE DB Eigenschaften:

- `DBPROP_MAXROWS` funktioniert nur für schreibgeschützte Anbieter (d. h., wenn `DBPROP_IRowsetChange` und `DBPROP_IRowsetUpdate` **false**sind). Andernfalls wird diese Eigenschaft nicht unterstützt.

- `DBPROP_MAXPENDINGROWS` wird ignoriert. der Anbieter gibt seinen eigenen Grenzwert an.

- `DBPROP_MAXOPENROWS` wird ignoriert. der Anbieter gibt seinen eigenen Grenzwert an.

- `DBPROP_CANHOLDROWS` wird ignoriert. der Anbieter gibt seinen eigenen Grenzwert an.

## <a name="see-also"></a>Weitere Informationen

[Arbeiten mit OLE DB-Anbietervorlagen](../../data/oledb/working-with-ole-db-provider-templates.md)
