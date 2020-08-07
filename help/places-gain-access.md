---
title: 'Zugriff auf den Places Service '
description: In diesem Abschnitt erfahren Sie, wie Sie einen Benutzer zu "Orte-Dienst"und "Experience Platform Launch"hinzufügen, damit der Benutzer auf den Orte-Dienst zugreifen kann.
translation-type: tm+mt
source-git-commit: 26538602a73e806a4822705c7a3aa44d76351030
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 7%

---

# Zugriff auf den Places Service {#adding-user-launch-places}

Sie können den Orte-Dienst über das Schnellzugriffsmenü auf [Adobe Experience Cloud zu Hause](https://experience.adobe.com)aufrufen.
Wenn Ihre Benutzer-ID Zugriff hat, wird das Symbol &quot;Orte-Dienst&quot;wie unten beschrieben angezeigt:

![Schnellzugriffsmenü](/help/assets/quickaccess.png)

Sie können auch über das Menü Adobe Experience Platform auf den Ortsdienst zugreifen:

![Menü &quot;Experience Platform&quot;](/help/assets/solutionaccessmenu.png)

Wenn Sie den Orte-Dienst in keinem dieser Menüs sehen, wenden Sie sich an einen Administrator in Ihrem Unternehmen, um Ihre Benutzer-ID dem Orts-Core-Service in der Admin Console hinzuzufügen.

## Adding a user to Places Service and Experience Platform Launch

To allow users to access the [Experience Platform Launch UI](https://launch.adobe.com), they need to be added to Places Core Service in the Admin Console as a user. Damit Benutzer Zugriff auf Experience Platform Launch haben, mobile Eigenschaften konfigurieren und Orte mit dem Adobe Experience Platform SDK verwenden können, müssen sie dem Experience Platform Launch in der Admin Console hinzugefügt und die folgenden Berechtigungen für den Experience Platform Launch erhalten:

* All Property Rights:
   * Entwickeln
   * Genehmigen
   * Veröffentlichen Sie
   * Manage extensions
   * Manage environments
* Manage Properties permission under Company Rights

If this is the first time you are adding a user, complete the following steps to add users to Experience Platform Launch and Places Service. If you have added users before, multiple profiles might be displayed, so ensure that you select the correct profile.

>[!IMPORTANT]
>
>Only org administrators can access the Admin Console and add the users.

### 1. Verify that Places Service and Experience Platform Launch are provisioned

1. Log in to your Experience Cloud organization.
1. In the top-right side, click the Experience Cloud shell switcher.

   ![shell switcher](/help/assets/places_shell_switcher1.png)

1. Unter **[!UICONTROL Platform]** klicken Sie auf **[!UICONTROL Administration]**.

   If you do not see **Administration** in the list, you are not an admin. You must contact your org admin to complete this procedure.

1. Klicken Sie auf der Seite &quot;Experience Cloud-Verwaltung&quot;auf der **[!UICONTROL Admin Console]** Karte auf **[!UICONTROL Take me there]**.

1. Wenn Sie in der Admin Console Zugriff auf mehrere Organisationen haben, überprüfen Sie, ob rechts oben auf der Seite das richtige Unternehmen ausgewählt ist.

   Dies ist die Organisation, der Sie Ihre Benutzer hinzufügen werden. Wenn die richtige Reihenfolge nicht ausgewählt wurde, klicken Sie auf das Org und wählen Sie das Org aus der Dropdown-Liste aus.

   >[!IMPORTANT]
   >
   >Wenn Sie keinen Zugriff auf eine Organisation haben, haben Sie keinen Administratorzugriff auf diese Organisation.

1. Überprüfen Sie, ob die Karten für **[!UICONTROL Adobe Experience Platform Launch]** und angezeigt **[!UICONTROL Places Core Services]** werden.

   ![](/help/assets/places_provisioned1.png)

   Wenn sie angezeigt werden, wurden Orte-Dienst und Experience Platform Launch für Ihr Unternehmen bereitgestellt. Wenn sie nicht angezeigt werden, müssen sie für Ihr Unternehmen bereitgestellt werden.


### 2. Einrichten des Profils und Hinzufügen der Berechtigungen

1. Richten Sie ein Experience Platform Launch-Profil ein, das Benutzern, die dem Profil hinzugefügt wurden, die Verwendung von Experience Platform Launch und seinen mobilen Eigenschaften mit dem Experience Platform SDK ermöglicht.

   a. Klicken Sie in der Menüleiste auf **[!UICONTROL Product]**.

   b. Klicken Sie im linken Bereich in der Liste der Produkte auf **[!UICONTROL Adobe Experience Platform Launch]**.

   * Die Profile des Experience Platform Launchs werden rechts angezeigt.
   * Experience Platform Launch hat ein standardmäßiges Profil namens *Launch - (Organisationsname)* .

      Wenn Sie zuvor Benutzer zu Experience Platform Launch hinzugefügt haben, werden möglicherweise mehrere Profil aufgelistet.

1. Wählen Sie das richtige Profil aus:

   a. Klicken Sie auf den Namen des Standard-Profils.

   b. Click the **[!UICONTROL Permissions]** tab.

   c. Klicken Sie **[!UICONTROL Edit]** neben **[!UICONTROL Property Rights]**.

   d. Klicken Sie im linken Fensterbereich auf **[!UICONTROL + Add all]**.

   Durch diesen Schritt werden alle verfügbaren Berechtigungen auf die enthaltene Liste für Berechtigungen verschoben.

   e. Klicken Sie auf **[!UICONTROL Company Rights]**.

   f. Klicken Sie im linken Fensterbereich auf **[!UICONTROL + Manage Properties]**.

   g. Klicken Sie auf **[!UICONTROL Save]**.

>[!IMPORTANT]
>
>Für den Orte-Dienst gibt es ein Standard-Profil, Sie müssen jedoch keine Berechtigungen hinzufügen.

Sie haben dem erstellten Profil erfolgreich Berechtigungen hinzugefügt.

### 3. hinzufügen eines Benutzers oder Entwicklers für die Profil &quot;Orte-Dienst&quot;und &quot;Experience Platform Launch&quot;

Sie können einen Benutzer und/oder einen Entwickler zu Ihren Profilen für den Places Service und den Experience Platform Launch hinzufügen.

### Hinzufügen von Benutzern

So fügen Sie Ihren Profilen &quot;Orte-Dienst&quot;und &quot;Experience Platform Launch&quot;einen Benutzer hinzu:

1. hinzufügen Sie einen Benutzer zum Experience Platform Launch-Profil.

   a. Klicken Sie in der Menüleiste auf **[!UICONTROL Overview]**.

   b. Überprüfen Sie auf der **[!UICONTROL Adobe Experience Platform Launch]** Karte Folgendes:

   * Am unteren Rand der Karte werden zwei Punkte angezeigt.
   * Der Punkt links ist schwarz.

      Wenn der Punkt auf der rechten Seite schwarz ist, können Sie nur Entwickler hinzufügen. Um einen Benutzer hinzuzufügen, klicken Sie auf den Punkt links.
   c. Klicken Sie auf **[!UICONTROL + Add Users]**.

   d. Geben Sie das Adobe ID des Benutzers ein.

   e. Führen Sie einen der folgenden Schritte aus:

   * Wenn Sie einen neuen Benutzer hinzufügen, klicken Sie auf **[!UICONTROL New user]** und geben Sie den Vor- und Nachnamen des Benutzers ein.
   * Wenn Sie einen vorhandenen Benutzer hinzufügen, klicken Sie auf den Namen des Benutzers, der angezeigt wird.

   f. Wählen Sie in der **[!UICONTROL Please select a profile for this product]** Dropdown-Liste das Profil aus, das Sie zuvor bearbeitet haben.

   g. Klicken Sie auf **[!UICONTROL Save]**.

1. Add a user to **[!UICONTROL Places Core Services]**.

   >[!TIP]
   >
   >Derzeit haben alle Benutzer des Places-Dienstes dieselben Berechtigungen, sodass Sie die Berechtigungen nicht bearbeiten müssen.

   a. Überprüfen Sie auf der **[!UICONTROL Places Core Services]** Karte Folgendes:

   * Am unteren Rand der Karte werden zwei Punkte angezeigt.
   * Der Punkt links ist schwarz.

   b. Click **[!UICONTROL + Assign Users]**.

   c. Geben Sie das Adobe ID des Benutzers ein.

   d. Führen Sie einen der folgenden Schritte aus:

   * If you are adding a new user, click **[!UICONTROL New user]**, and enter the user’s first and last name.
   * Wenn Sie einen vorhandenen Benutzer hinzufügen, klicken Sie auf den Namen des Benutzers, der angezeigt wird.

   e. In the **[!UICONTROL Please select a profile for this product]** drop-down list, select the Places profile.

   f. Click **[!UICONTROL Save]**.

### Add a developer

For users who also need access to the Web Service API, you need to add them as a Developer.

So fügen Sie einen Entwickler hinzu:

1. On the **[!UICONTROL Places Core Services]** card, verify the following:

   * Two dots are displayed at the bottom of the card.
   * Click the dot on the right so **[!UICONTROL Assign Developers]** appears at the bottom of the card.

1. Klicken Sie auf **[!UICONTROL + Assign Developers]**.

1. Geben Sie die Adobe ID des Benutzers ein.

1. Führen Sie einen der folgenden Schritte aus:

   * If you are adding a new user, click **[!UICONTROL New user]** and enter the user’s first and last name.
   * If you are adding an existing user, click the user’s name that is displayed.

1. In the **[!UICONTROL Please select a profile for this product]** drop-down list, select the Places Service profile.

1. Klicken Sie auf **Speichern**.

Benutzer erhalten eine E-Mail, in der sie darauf hingewiesen werden, dass sie Zugriff auf Experience Platform Launch haben. They can can log in to the [Experience Platform Launch](https://launch.adobe.com) or the [Places Service](https://places.adobe.com) UIs for this organization. Wenn Sie Schritt 4 im Prozess **Entwickler hinzufügen** abgeschlossen haben, kann sich der Benutzer auch bei der [Adobe I/O-Konsole](https://console.adobe.io) anmelden, um eine Places-Integration zu erstellen und die Places-REST-API zu verwenden.
