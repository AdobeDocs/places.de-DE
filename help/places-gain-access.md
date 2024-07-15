---
title: Zugriff auf Places Service erhalten
description: In diesem Abschnitt finden Sie Informationen zum Hinzufügen eines Benutzers zum Places-Dienst und zum Experience Platform Launch, sodass der Benutzer auf den Places-Dienst zugreifen kann.
exl-id: f388945e-cf26-4694-9697-9fe564ae4b69
source-git-commit: c9058e9b70c2ef97151078f43913963471730bd2
workflow-type: tm+mt
source-wordcount: '907'
ht-degree: 1%

---

# Zugriff auf Places Service erhalten {#adding-user-launch-places}

Der Places-Dienst ist jetzt in der Datenerfassungs-Benutzeroberfläche verfügbar. Sie können über das Schnellzugriffsmenü auf der [Adobe Experience Cloud-Startseite](https://experience.adobe.com) auf die Datenerfassung zugreifen.

![Schnellzugriffsmenü](/help/assets/quickaccess.png)

Sie können auch über das Menü Adobe Experience Platform auf die Datenerfassung zugreifen:

![Experience Platform menu](/help/assets/solutionaccessmenu.png)

Wenn Ihre Benutzer-ID Zugriff hat, wird das Symbol Places Service im linken Bereich unter Data Management in der Datenerfassung wie unten angegeben angezeigt:

![Datenerfassung, linker Bereich](/help/assets/places_in_data_collection.png)

Wenn der Places-Dienst nicht an dieser Stelle angezeigt wird, wenden Sie sich an einen Administrator in Ihrem Unternehmen, um Ihre Benutzer-ID zu Adobe Experience Platform in der Admin Console hinzuzufügen.

## Hinzufügen eines Benutzers für den Zugriff auf den Places-Dienst und die Experience Adobe Experience Platform-Datenerfassung

Places ist jetzt in Adobe Experience Platform enthalten. Damit Benutzer auf den [Places-Dienst](https://experience.adobe.com/#/data-collection/places) zugreifen können, müssen sie als Benutzer in der Admin Console Adobe Experience Platform hinzugefügt werden. Damit Benutzer Zugriff auf die Experience Platform-Datenerfassung mit den erforderlichen Berechtigungen zum Konfigurieren mobiler Eigenschaften und zum Verwenden von Places mit dem Adobe Experience Platform-SDK haben, müssen sie auch zur Adobe Experience Platform-Datenerfassung in der Admin Console hinzugefügt werden und über die folgenden Berechtigungen für die Adobe Experience Platform-Datenerfassung verfügen:

* Alle Berechtigungen unter Eigenschaftsrechte:
   * Genehmigen
   * Entwickeln
   * Eigenschaft bearbeiten
   * Umgebungen verwalten
   * Erweiterungen verwalten
   * Veröffentlichen Sie
* Berechtigung &quot;Eigenschaften verwalten&quot;unter &quot;Unternehmensrechte&quot;

Wenn Sie zum ersten Mal einen Benutzer hinzufügen, führen Sie die folgenden Schritte aus, um Benutzer zur Adobe Experience Platform-Datenerfassung und zu Adobe Experience Platform hinzuzufügen. Wenn Sie bereits Benutzer hinzugefügt haben, werden möglicherweise mehrere Profile angezeigt. Stellen Sie daher sicher, dass Sie das richtige Profil auswählen.

>[!IMPORTANT]
>
>Nur Organisationsadministratoren können auf die Admin Console zugreifen und die Benutzer hinzufügen.

### 1. Stellen Sie sicher, dass die Datenerfassung von Adobe Experience Platform und Adobe Experience Platform bereitgestellt wurde.

1. Melden Sie sich bei Ihrer Experience Cloud-Organisation an, [Adobe Experience Cloud-Startseite](https://experience.adobe.com).
1. Klicken Sie oben rechts auf den Experience Cloud Shell-Umschalter, um ein Dropdown-Menü anzuzeigen.

   ![Shell-Umschalter](/help/assets/places_shell_switcher1.png)

1. Klicken Sie unten in der Liste auf **[!UICONTROL Admin Console]**. (Ein Link zur **[!UICONTROL Admin Console]** finden Sie auch im Abschnitt Schnellzugriff .)

   Wenn **[!UICONTROL Admin Console]** nicht in der Liste angezeigt wird, sind Sie kein Administrator. Wenden Sie sich an Ihren Organisationsadministrator, um dieses Verfahren abzuschließen.

1. Wenn Sie in der Admin Console Zugriff auf mehrere Organisationen haben, überprüfen Sie, ob rechts oben auf der Seite die richtige Organisation ausgewählt ist.

   Dies ist die Organisation, zu der Sie Ihre Benutzer hinzufügen werden. Wenn die richtige Organisation nicht ausgewählt wurde, klicken Sie auf die Organisation und wählen Sie die richtige Organisation aus der Dropdownliste aus.

   >[!IMPORTANT]
   >
   >Wenn die gewünschte Organisation nicht in der Dropdownliste enthalten ist, bedeutet dies, dass Sie keinen Administratorzugriff auf diese Organisation haben.

1. Klicken Sie in der Admin Console auf die Registerkarte &quot;Produkte&quot;und stellen Sie sicher, dass die Karten für **[!UICONTROL Adobe Experience Platform Data Collection]** und **[!UICONTROL Adobe Experience Platform]** angezeigt werden.

   ![](/help/assets/places_provisioned1.png)

   Diese beiden Produkte werden automatisch für alle Organisationen bereitgestellt, sodass sie vorhanden sein sollten.


### 2. Benutzer zu diesen Produkten hinzufügen

#### Benutzer hinzufügen, um Zugriff auf die Benutzeroberfläche des Places Service zu gewähren

1. Klicken Sie auf der Registerkarte &quot;Products&quot;auf die Karte **[!UICONTROL Adobe Experience Platform]** .
2. Ein Benutzer kann einem beliebigen Profil in **[!UICONTROL Adobe Experience Platform]** hinzugefügt werden, um Zugriff auf Places zu erhalten. Es müssen keine spezifischen Berechtigungen festgelegt werden.
3. Wählen Sie ein Profil aus (wenn mehrere Profile vorhanden sind) und klicken Sie darauf, um es zu öffnen.
4. Klicken Sie auf die blaue Schaltfläche **Benutzer hinzufügen** , geben Sie dem Benutzer seine Adobe ID und seinen Namen ein und klicken Sie dann auf Speichern , um das Hinzufügen abzuschließen.

#### Benutzer zur Datenerfassung hinzufügen

1. Klicken Sie auf der Registerkarte &quot;Products&quot;auf die Karte **[!UICONTROL Adobe Experience Platform-Datenerfassung]** .
2. Standardmäßig wurde ein Profil mit dem Namen &quot;**Standardmäßiger Zugriff auf alle Daten&quot;** erstellt. Durch Hinzufügen eines Benutzers zu diesem Profil wird sichergestellt, dass er über die entsprechenden Berechtigungen für die Arbeit mit dem Places-Dienst und der Datenerfassung verfügt. Wenn ein anderes Profil ausgewählt wird, stellen Sie sicher, dass die oben genannten Berechtigungen enthalten sind.
3. Wählen Sie ein Profil aus (wenn mehrere Profile vorhanden sind) und klicken Sie darauf, um es zu öffnen.
4. Klicken Sie auf die blaue Schaltfläche **Benutzer hinzufügen** , geben Sie dem Benutzer seine Adobe ID und seinen Namen ein und klicken Sie dann auf Speichern , um das Hinzufügen abzuschließen.

#### Fügen Sie einen Benutzer als Entwickler für den Places-Dienst hinzu.

Für Benutzer, die auch Zugriff auf die Places Service REST API benötigen, müssen Sie sie als Entwickler hinzufügen.
1. Klicken Sie auf der Registerkarte &quot;Products&quot;auf die Karte **[!UICONTROL Adobe Experience Platform]** .
2. Wenn der Benutzer bereits über die oben stehenden Anweisungen zur Karte **[!UICONTROL Adobe Experience Platform]** hinzugefügt wurde, wählen Sie dasselbe zuvor verwendete Profil aus und klicken Sie darauf.
3. Klicken Sie im Profil auf die Registerkarte **Entwickler** .
4. Klicken Sie auf die blaue Schaltfläche **Entwickler hinzufügen** , geben Sie dem Benutzer seine Adobe ID und seinen Namen ein und klicken Sie dann auf Speichern , um das Hinzufügen abzuschließen.

Nach Abschluss der oben genannten Schritte erhält der Benutzer eine E-Mail, in der er darüber informiert wird, dass er Zugriff auf die **[!UICONTROL Adobe Experience Platform]**- und die **[!UICONTROL Adobe Experience Platform-Datenerfassung]** hat. Sie können sich dann bei [Adobe Experience Cloud](https://experience.adobe.com) für diese Organisation anmelden und auf den Places-Dienst und die Datenerfassung zugreifen. Wenn Sie auch die Schritte **[!UICONTROL Entwickler hinzufügen]** ausführen, kann sich der Benutzer auch bei [Adobe Developer Console](https://developer.adobe.com/console/home) anmelden, um ein Projekt zu erstellen, das Zugriff auf die Places Service-REST-API bietet.
