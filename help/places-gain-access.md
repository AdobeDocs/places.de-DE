---
title: Zugriff auf Places Service erhalten
description: In diesem Abschnitt finden Sie Informationen darüber, wie Sie einen Benutzer zu Places Service und Experience Platform Launch hinzufügen, damit der Benutzer auf Places Service zugreifen kann.
exl-id: f388945e-cf26-4694-9697-9fe564ae4b69
source-git-commit: c9058e9b70c2ef97151078f43913963471730bd2
workflow-type: tm+mt
source-wordcount: '907'
ht-degree: 1%

---

# Zugriff auf Places Service erhalten {#adding-user-launch-places}

Places Service ist jetzt in der Datenerfassungs-Benutzeroberfläche verfügbar. Der Zugriff auf die Datenerfassung erfolgt über das Schnellzugriffsmenü auf der [Adobe Experience Cloud-Startseite](https://experience.adobe.com).

![Schnellzugriffsmenü](/help/assets/quickaccess.png)

Sie können auf die Datenerfassung auch über das Menü &quot;Adobe Experience Platform&quot; zugreifen:

Menü ![Experience Platform](/help/assets/solutionaccessmenu.png)

Wenn Ihre Benutzer-ID Zugriff hat, wird das Symbol Places Service im linken Bereich unter Daten-Management in der Datenerfassung angezeigt, wie unten angegeben:

![Linkes Bedienfeld „Datenerfassung“](/help/assets/places_in_data_collection.png)

Wenn der Places Service nicht an diesem Ort angezeigt wird, wenden Sie sich an einen Administrator in Ihrem Unternehmen, um Ihre Benutzer-ID zu Adobe Experience Platform in der Admin Console hinzuzufügen.

## Hinzufügen von Benutzenden für den Zugriff auf Places Service und die Datenerfassung in Experience Adobe Experience Platform

Places ist jetzt in Adobe Experience Platform enthalten. Damit Benutzerinnen und Benutzer auf den [Places-Service](https://experience.adobe.com/#/data-collection/places) zugreifen können, müssen sie in der Admin Console als Benutzerin bzw. Benutzer zu Adobe Experience Platform hinzugefügt werden. Damit Benutzerinnen und Benutzer auf die Experience Platform-Datenerfassung zugreifen können, die über die erforderlichen Berechtigungen zum Konfigurieren von Mobile-Eigenschaften und zum Verwenden von Places mit Adobe Experience Platform SDK verfügt, müssen sie auch zur Adobe Experience Platform-Datenerfassung in der Admin Console hinzugefügt werden und die folgenden Berechtigungen für die Adobe Experience Platform-Datenerfassung erhalten:

* Alle Berechtigungen unter Eigenschaftsrechten:
   * Genehmigen
   * Entwickeln
   * Eigenschaft bearbeiten
   * Umgebungen verwalten
   * Erweiterungen verwalten
   * Veröffentlichen Sie
* Berechtigung zum Verwalten von Eigenschaften unter Unternehmensrechten

Wenn Sie zum ersten Mal einen Benutzer hinzufügen, führen Sie die folgenden Schritte aus, um Benutzer zur Adobe Experience Platform-Datenerfassung und Adobe Experience Platform hinzuzufügen. Wenn Sie bereits Benutzer hinzugefügt haben, werden möglicherweise mehrere Profile angezeigt. Stellen Sie daher sicher, dass Sie das richtige Profil auswählen.

>[!IMPORTANT]
>
>Nur Organisationsadministratoren können auf die Admin Console zugreifen und Benutzende hinzufügen.

### 1. Überprüfen, ob die Datenerfassung von Adobe Experience Platform und Adobe Experience Platform bereitgestellt wird

1. Melden Sie sich bei Ihrem Experience Cloud-Unternehmen an, [Adobe Experience Cloud-Startseite](https://experience.adobe.com).
1. Klicken Sie oben rechts auf den Experience Cloud-Shell-Umschalter, um ein Dropdown-Menü anzuzeigen.

   ![Shell-Umschalter](/help/assets/places_shell_switcher1.png)

1. Klicken Sie unten in der Liste auf **[!UICONTROL Admin Console]**. (Ein Link zur Admin Console **&#x200B;**&#x200B;finden Sie auch im Abschnitt Schnellzugriff .)

   Wenn **[!UICONTROL Admin Console]** in der Liste nicht angezeigt wird, sind Sie kein Administrator. Sie müssen sich an den Administrator Ihrer Organisation wenden, um dieses Verfahren abzuschließen.

1. Wenn Sie in der Admin Console Zugriff auf mehrere Organisationen haben, überprüfen Sie, ob oben rechts auf der Seite die richtige Organisation ausgewählt ist.

   Dies ist die Organisation, der Sie Ihre Benutzer hinzufügen. Wenn die richtige Organisation nicht ausgewählt wurde, klicken Sie auf die Organisation und wählen Sie die richtige Organisation aus der Dropdown-Liste aus.

   >[!IMPORTANT]
   >
   >Wenn sich die gewünschte Organisation nicht in der Dropdown-Liste befindet, bedeutet dies, dass Sie keinen Administratorzugriff auf diese Organisation haben.

1. Klicken Sie in der Admin Console auf die Registerkarte Produkte und vergewissern Sie sich, dass die Karten für die **[!UICONTROL Adobe Experience Platform]** Datenerfassung und **[!UICONTROL Adobe Experience Platform]** angezeigt werden.

   ![](/help/assets/places_provisioned1.png)

   Diese beiden Produkte werden automatisch allen Organisationen bereitgestellt. Daher sollten sie vorhanden sein.


### 2. Benutzer zu diesen Produkten hinzufügen

#### Benutzer hinzufügen, um Zugriff auf die Places Service-Benutzeroberfläche zu gewähren

1. Klicken Sie auf der Registerkarte Produkte auf die Karte **[!UICONTROL Adobe Experience Platform]**.
2. Ein Benutzer kann zu einem beliebigen Profil innerhalb von **[!UICONTROL Adobe Experience Platform hinzugefügt werden]** Um Zugriff auf Places zu erhalten, müssen keine spezifischen Berechtigungen festgelegt werden.
3. Wählen Sie ein Profil aus (wenn mehrere Profile vorhanden sind) und klicken Sie darauf, um es zu öffnen.
4. Klicken Sie auf die blaue **Benutzer hinzufügen**-Schaltfläche, geben Sie die Adobe ID und den Namen der Benutzerin bzw. des Benutzers ein und klicken Sie dann auf Speichern , um das Hinzufügen abzuschließen.

#### Benutzer zur Datenerfassung hinzufügen

1. Klicken Sie auf der Registerkarte Produkte auf die Karte **[!UICONTROL Adobe Experience Platform-]**.
2. Standardmäßig wird ein Profil mit **Namen „Standardmäßige Datenerfassung -**&quot; erstellt. Durch das Hinzufügen eines Benutzers zu diesem Profil wird sichergestellt, dass er über die erforderlichen Berechtigungen zum Arbeiten mit dem Places Service und der Datenerfassung verfügt. Wenn ein anderes Profil ausgewählt wird, stellen Sie sicher, dass die oben genannten Berechtigungen enthalten sind.
3. Wählen Sie ein Profil aus (wenn mehrere Profile vorhanden sind) und klicken Sie darauf, um es zu öffnen.
4. Klicken Sie auf die blaue **Benutzer hinzufügen**-Schaltfläche, geben Sie die Adobe ID und den Namen der Benutzerin bzw. des Benutzers ein und klicken Sie dann auf Speichern , um das Hinzufügen abzuschließen.

#### Fügen Sie einen Benutzer als Entwickler für Places Service hinzu.

Für Benutzer, die auch Zugriff auf die Places Service-REST-API benötigen, müssen Sie sie als Entwickler hinzufügen.
1. Klicken Sie auf der Registerkarte Produkte auf die Karte **[!UICONTROL Adobe Experience Platform]**.
2. Wenn der/die Benutzende der **[!UICONTROL Adobe Experience Platform]**-Karte bereits über die obigen Anweisungen hinzugefügt wurde, wählen Sie dasselbe zuvor verwendete Profil aus und klicken Sie darauf.
3. Klicken Sie im Profil auf die Registerkarte **Entwickler**
4. Klicken Sie auf die blaue Schaltfläche **Entwickler hinzufügen**, geben Sie die Adobe ID und den Namen der Benutzenden ein und klicken Sie dann auf Speichern , um das Hinzufügen abzuschließen.

Nach Abschluss der oben genannten Schritte erhält der Benutzer eine E-Mail, in der er über den Zugriff auf die Datenerfassung von **[!UICONTROL Adobe Experience Platform]** und **[!UICONTROL Adobe Experience Platform informiert]**. Sie können sich dann bei der [Adobe Experience Cloud](https://experience.adobe.com) für dieses Unternehmen anmelden und auf den Places-Service und die Datenerfassung zugreifen. Wenn Sie auch die Schritte **[!UICONTROL Entwickler hinzufügen]** ausführen, können sich Benutzende auch bei der [Adobe Developer Console anmelden, &#x200B;](https://developer.adobe.com/console/home) ein Projekt zu erstellen, das Zugriff auf die Places Service-REST-API bietet.
