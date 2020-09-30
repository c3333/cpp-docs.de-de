---
title: Festlegen von Eigenschaften im Anbieter
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB providers, properties
- properties [C++], OLE DB provider
ms.assetid: 26a8b493-7ec4-4686-96d0-9ad5d2bca5ac
ms.openlocfilehash: 3717282d284990b1b8038f6954ee971938cf7921
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509487"
---
# <a name="setting-properties-in-your-provider"></a>Festlegen von Eigenschaften im Anbieter

Suchen Sie die Eigenschaften Gruppe und die Eigenschaften-ID für die gewünschte Eigenschaft. Weitere Informationen finden Sie unter [OLE DB Eigenschaften](/previous-versions/windows/desktop/ms722734(v=vs.85)) in der **OLE DB Programmierer-Referenz**.

Suchen Sie in dem vom Assistenten generierten Anbieter Code die Eigenschaften Zuordnung, die der Eigenschaften Gruppe entspricht. Der Name der Eigenschaften Gruppe entspricht in der Regel dem Namen des Objekts. Befehls-und Rowseteigenschaften können im Befehl oder Rowset gefunden werden. Datenquellen-und Initialisierungs Eigenschaften finden Sie im Datenquellen Objekt.

Fügen Sie in der Eigenschaften Zuordnung ein [PROPERTY_INFO_ENTRY_EX](./macros-for-ole-db-provider-templates.md#property_info_entry_ex) Makro hinzu. PROPERTY_INFO_ENTRY_EX benötigt vier Parameter:

- Die eigen schafts-ID, die ihrer Eigenschaft entspricht. Entfernen Sie die ersten sieben Zeichen ("DBPROP_") von der Vorderseite des Eigenschaften namens. Wenn Sie z. b. hinzufügen möchten `DBPROP_MAXROWS` , übergeben Sie `MAXROWS` als erstes Element. Wenn dies eine benutzerdefinierte Eigenschaft ist, übergeben Sie den vollständigen GUID-Namen (z `DBMYPROP_MYPROPERTY` . b.).

- Der Varianttyp der Eigenschaft (in [OLE DB Eigenschaften](/previous-versions/windows/desktop/ms722734(v=vs.85)) in der **OLE DB Programmierer-Referenz**). Geben Sie den VT_ Typ (z. b. VT_BOOL oder VT_I2) ein, der dem Datentyp entspricht.

- Flags, die angeben, ob die Eigenschaft lesbar und beschreibbar ist, und die Gruppe, zu der Sie gehört. Der folgende Code zeigt z. b. eine Lese-/Schreibeigenschaft an, die der Rowsetgruppe angehört:

    ```cpp
    DBPROPFLAGS_ROWSET | DBPROPFLAGS_READ | DBPROPFLAGS_WRITE
    ```

- Der Basiswert der Eigenschaft. Dies kann für `VARIANT_FALSE` einen booleschen Typ oder NULL für einen ganzzahligen Typ sein, z. b.. Die-Eigenschaft hat diesen Wert, es sei denn, Sie wird geändert.

    > [!NOTE]
    > Einige Eigenschaften sind mit anderen Eigenschaften verknüpft oder verkettet, z. b. Lesezeichen oder Aktualisierungen. Wenn ein Consumer eine Eigenschaft auf true festlegt, kann auch eine andere Eigenschaft festgelegt werden. Die OLE DB Anbieter Vorlagen unterstützen dies über die Methode " [cutlpropertychanged](./cutlprops-class.md#onpropertychanged)".

## <a name="properties-ignored-by-microsoft-ole-db-providers"></a>Eigenschaften, die von Microsoft OLE DB-Anbietern ignoriert werden

Die Microsoft OLE DB-Anbieter ignorieren die folgenden OLE DB Eigenschaften:

- `DBPROP_MAXROWS` funktioniert nur für schreibgeschützte Anbieter (d. h. Where `DBPROP_IRowsetChange` und `DBPROP_IRowsetUpdate` sind **`false`** ); andernfalls wird diese Eigenschaft nicht unterstützt.

- `DBPROP_MAXPENDINGROWS` wird ignoriert. der Anbieter gibt seinen eigenen Grenzwert an.

- `DBPROP_MAXOPENROWS` wird ignoriert. der Anbieter gibt seinen eigenen Grenzwert an.

- `DBPROP_CANHOLDROWS` wird ignoriert. der Anbieter gibt seinen eigenen Grenzwert an.

## <a name="see-also"></a>Weitere Informationen

[Arbeiten mit OLE DB Anbieter Vorlagen](../../data/oledb/working-with-ole-db-provider-templates.md)
