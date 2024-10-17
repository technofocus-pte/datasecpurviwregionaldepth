# Laboratorio 6 - Configuración de Insider Risk Management

## Objetivo :

En este laboratorio aprenderemos a configurar Insider Risk Management
utilizando las políticas de Insider Risk Management. Utilizaremos los
Tipos de Información Sensible que creamos en el Laboratorio 2 y las
políticas DLP que creamos en el Laboratorio 4 para crear políticas que
protegerán a la organización contra el uso arriesgado de navegadores o
cualquier robo o filtración de datos.

Al iniciar sesión en los dispositivos VM, utilizará las credenciales de
Azure AD de los respectivos usuarios de las VM a lo largo de los
Ejercicios. Utilice las siguientes credenciales:

Pattis-Device

pattif@WWLxXXXXXX.onmicrosoft.com

User password

Adeles-Device

adelev@WWLxXXXXXX.onmicrosoft.com

User password

Christies-Device

christies@WWLxXXXXXX.onmicrosoft.com

User password

## Ejercicio 1: Crear políticas de Insider Risk Management .

### Requisitos previos

#### Paso 1 - Añadir usuarios al grupo de funciones Insider Risk Management

1.  Si el portal de Microsoft Purview está abierto, continúe con el paso
    2; de lo contrario, abra **+++https://purview.microsoft.com+++** e
    inicie sesión con las credenciales **de administrador de MOD**.

![](./media/image1.png)

2.  En la barra de navegación , seleccione **Settings** y, en **Role
    groups**, seleccione **Insider Risk Management** . A continuación,
    seleccione **Edit**. En el panel lateral, seleccione de nuevo
    **Edit**

3.  

4.  

5.  .

![](./media/image2.png)

6.  

7.  

8.  En la página **Edit Members of the role group**, seleccione **Choose
    users.**

![A screenshot of a computer Description automatically
generated](./media/image7.png)

9.  Seleccione la casilla situada cerca de **Megan** y **Alex**. A
    continuación, seleccione **Select**.

![](./media/image9.png)

10. A continuación, seleccione **Next**.

![A screenshot of a computer Description automatically
generated](./media/image11.png)

11. Seleccione **Save** para añadir los usuarios al grupo de funciones.

![A screenshot of a computer Description automatically
generated](./media/image13.png)

12. Seleccione **Done** para completar los pasos.

![A screenshot of a computer Description automatically
generated](./media/image15.png)

#### Paso 2 - Activar el análisis de riesgos internos insights

1.  

2.  

3.  En el portal Microsoft Purview . Vaya a **Settings**, vaya a
    **Insider Risk Management**. Vaya a **Analytics**, active el botón
    de opción y haga clic en **Save**.

![](./media/image17.png)

#### Paso 3 - Incorporar un dispositivo

En este escenario de Deployment, incorporará dispositivos que aún no han
sido incorporados y sólo desea detectar actividades de riesgo internas
en dispositivos Windows 10.

1.  Conéctese a **Pattis-Device** a través de RDP, haga clic en windows
    y busque **Windows Security**.

![A screenshot of a computer Description automatically
generated](./media/image19.png)

2.  Haga clic en el icono de **configuración** de la parte inferior
    izquierda.

![Graphical user interface, application, Teams Description automatically
generated](./media/image20.png)

3.  Haga clic en **About**.

![A screenshot of a computer Description automatically
generated](./media/image21.png)

4.  El número de versión aparece en Versión del cliente antimalware. El
    número de versión aparece en Versión del cliente antimalware.
    Compruebe que la versión del cliente Antimalware **es 4.18.2110** o
    posterior, si no es así continúe con el siguiente paso o si lo es
    continúe con el paso 9.

![A screenshot of a computer Description automatically
generated](./media/image22.png)

5.  En VM, haga clic en Windows y busque **Check for Updates**.

![A screenshot of a computer Description automatically
generated](./media/image23.png)

6.  Haga clic en **Download now**, o **Install now**.

![A screenshot of a computer Description automatically
generated](./media/image24.png)

7.  Una vez finalizada la instalación, vaya de nuevo a seguridad de
    windows y compruebe que la versión del cliente antimalware es
    **4.18.2110** o más reciente. Si no es así, repita los pasos 5 y 6,
    hasta que se actualice la VM.

![A screenshot of a computer Description automatically
generated](./media/image25.png)

8.  Cierre el centro de seguridad y el centro de actualización. Finalice
    la conexión RDP por ahora.

9.  Repita los pasos del 1 al 7 para actualizar **Adeles-Device** y
    **Christies-Device**.

10. 

11. Inicie sesión en **+++https://security.microsoft.com/+++**
    utilizando su cuenta de **administrador de MOD** en su VM de
    laboratorio .

12. Seleccione **Settings** \> **Device** **onboarding**.

![](./media/image27.png)

13. Haga clic en **Turn on Device onboarding**.

![A screenshot of a computer Description automatically
generated](./media/image29.png)

14. Desde los **settings** \> **Device onboarding** \> **Onboarding**.
    Haga clic en **Download** **package**.

![A screenshot of a computer Description automatically
generated](./media/image30.png)

15. 

16. 

17. Una vez descargado, conéctese a **Pattis-Device** mediante RDP y
    copie el archivo en el escritorio de **Pattis** -Device.

18. Haga clic con el botón derecho en el archivo y **Extract all**... .

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image33.png)

![A screenshot of a computer Description automatically
generated](./media/image34.png)

19. Una vez hecho esto, abra la carpeta y ejecute el archivo con
    derechos de **administrador**.

![A computer screen with a computer screen Description automatically
generated](./media/image35.png)

20. Haga clic en **More info**.

![Graphical user interface, application Description automatically
generated](./media/image36.png)

21. Haga clic en **Run anyway**.

![A screenshot of a computer error Description automatically
generated](./media/image37.png)

22. En el Command prompt, pulse **Y** y pulse Intro para confirmar y
    continuar cuando se le solicite.

![A screenshot of a computer error Description automatically
generated](./media/image38.png)

23. Recibirá un mensaje indicando que el dispositivo está integrado. En
    el Command Prompt una vez que reciba el mensaje, **Press any key to
    continue. . .**, pulse cualquier tecla.

24. Una vez cerrado el símbolo del sistema, abra Símbolo del sistema en
    modo de administrador para ejecutar una prueba de detección y, en el
    símbolo del sistema, copie y ejecute el siguiente comando. La
    ventana del símbolo del sistema se cerrará automáticamente.

**+++powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyleHidden
$ErrorActionPreference=
'silentlycontinue';(New-ObjectSystem.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe','C:\test-WDATP-test\invoice.exe');Start-Process
'C:\test-WDATP-test\invoice.exe'+++**

![Text Description automatically generated](./media/image39.png)

25. Cierre la conexión VM.

26. Si el onboarding del dispositivo se realiza correctamente, puede ir
    al portal de **Microsoft 365 Defender** que dejamos abierto en el
    navegador en la VM de Laboratorio y verás que la prueba de detección
    se marca como completada y aparece una nueva alerta en pocos
    minutos.

![A screenshot of a computer Description automatically
generated](./media/image40.png)

27. Ahora copie el archivo que descargamos en el paso 13, y repita los
    pasos 15 a 21 para las VMs - **Connies-Device** y **Chriss-Device**,
    respectivamente para incorporarlos como Devices en el portal de
    **Microsoft 365 Defender** .

28. 

29. 

30. 

31. Abra la página **+++https://** **purview.microsoft.com+++** e inicie
    sesión con el nombre de usuario
    **pattifpattif@WWWWLLxXXXXXX.onmicrosoft.com** y la contraseña de
    usuario . (sustituya WWL xXXXXXX por el prefijo de su tenant que
    aparece en la pestaña de recursos).

32. 

33. Abra la **configuración de** haciendo clic en la configuración en la
    navegación y seleccione **Devices Onboarding** \> **Devices**.

**Nota:** Aunque la incorporación del dispositivo suele tardar unos 60
segundos en activarse, espere hasta 30 minutos .

34. 

35. 

36. 

37. 

38. Podrá comprobar la lista de **Devices**. La lista estará vacía hasta
    que incorpore dispositivos, una vez hecho esto, podrá ver sus
    máquinas virtuales en la lista de dispositivos incorporados .

### Tarea 1: Creación de una política a nivel de toda la organización para detectar y puntuar el Uso Riesgoso del Navegador 

#### Paso 1 - Crear una nueva política

1.  Si ha cerrado la ventana del navegador en la tarea anterior, abra la
    **página** **+++https://** **purview.microsoft.com+++** e inicia
    sesión con el nombre de usuario
    **pattif@WWLxXXXXXX.onmicrosoft.com** y la contraseña de usuario .
    (sustituye WWL xXXXXXX por el prefijo de tu tenant que aparece en la
    pestaña de recursos).

2.  Vaya a **Insider Risk** **Management** y seleccione la pestaña
    **Policies**. Seleccione **Create policy** para abrir el asistente
    de políticas.

![](./media/image47.png)

3.  En la página **Choose a policy template**, seleccione **Risky
    browser usage (preview)**, en **Risky browser usage (preview).**

![A screenshot of a computer Description automatically
generated](./media/image49.png)

4.  Asegúrese de que se cumplen todos los requisitos previos.

![A screenshot of a computer Description automatically
generated](./media/image50.png)

5.  Seleccione **Next** para continuar.

![A screenshot of a computer Description automatically
generated](./media/image51.png)

6.  En la página **Name and description**, rellene los campos
    siguientes:

    - Name (required): Risky usage of browser

    - Description (optional): This is a test policy for the risky
      browser usage.

7.  Seleccione **Next** para continuar.

![Graphical user interface, text, application Description automatically
generated](./media/image52.png)

8.  En la página Choose users and groups, seleccione Include all users
    and groups. Seleccione Next para continuar.

![Graphical user interface, text, application Description automatically
generated](./media/image52.png)

![A screenshot of a computer Description automatically
generated](./media/image53.png)

9.  En la página **Decide whether to prioritize**, seleccione **I don't
    want to specify priority content right now** (you'll be able to do
    this after the policy is created). Seleccione **Next** para
    continuar.

![Graphical user interface, text, application Description automatically
generated](./media/image54.png)

10. En la página **Triggers** for this policy, seleccione **Turn on
    indicators**.

![A screenshot of a computer Description automatically
generated](./media/image55.png)

11. En **Choose indicators to turn on**, seleccione todo under **Risky
    browsing indicators (preview)** y desmarque el resto de casillas.

![A screenshot of a computer Description automatically
generated](./media/image56.png)

12. Desplácese hacia abajo y seleccione **Save**.

13. En Activadores para esta política, en **Select which activities will
    trigger this policy**. Seleccione todas las opciones y haga clic en
    **Next**.

![Graphical user interface, text, application Description automatically
generated](./media/image57.png)

14. En la página **Triggering thresholds for this policy page**,
    seleccione **Use custom thresholds (Recommended)**, cambie todos los
    umbrales a 1 por día y, a continuación, seleccione Next.

![Graphical user interface, application Description automatically
generated](./media/image58.png)

![A screenshot of a computer Description automatically
generated](./media/image59.png)

15. En la página **de indicators**, seleccione **Next**.

![A screenshot of a computer Description automatically
generated](./media/image60.png)

16. En **Decide whether to use default or custom indicator thresholds**,
    seleccione **Use default thresholds for all indicators**, a
    continuación, seleccione **Next**.

![Graphical user interface, text, application Description automatically
generated](./media/image61.png)

17. En **Review settings and finish**, seleccione **Submit**.

![Graphical user interface, text, application Description automatically
generated](./media/image62.png)

18. En **Your policy was created**, seleccione **Done**.

![A screenshot of a computer Description automatically
generated](./media/image63.png)

19. Mantenga la pestaña abierta y continúe con la siguiente tarea.

#### Paso 2 - Puntúe la política 

1.  Haga clic en la nueva política denominada **Risky usage of
    browser**. Seleccione **Start scoring activity for users**..

![A screenshot of a computer Description automatically
generated](./media/image64.png)

2.  En el campo **Reason** del panel **Add users to multiple
    policies** , escriba **Testing the policy**.

![A screenshot of a computer Description automatically
generated](./media/image65.png)

3.  En el campo **This should last for (choose between 5 and 30 days),**
    seleccione 10 days.

4.  Utilice el campo **Search user to add to policies**. Añada a Brooke,
    Connie y Chris. A continuación, haga clic en Start scoring activity.

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image66.png)

5.  Una vez que reciba la confirmación de que ha iniciado **Scoring
    activity for 3 users**, haga clic en **Close**.

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image67.png)

### Tarea 2: Robo de datos por usuarios que se marchan

#### Paso 1 - Crear una nueva política 

1.  Si ha cerrado la ventana del navegador en la tarea anterior, abra
    **+++https://purview.microsoft.com+++** e inicie sesión con el
    nombre de usuario **pattif@WWLxXXXXXX.onmicrosoft.com y la
    contraseña de usuario.** (sustituya WWLxXXXXXX por el prefijo de su
    tenant que aparece en la pestaña de recursos).

2.  Vaya a **Insider Risk Management** y seleccione la pestaña
    **Policies**. Seleccione **Create policy** para abrir el asistente
    de políticas.

![](./media/image47.png)

3.  

4.  

5.  

6.  En la página **Choose a policy template** , seleccione **Data theft
    by departing users**, en **Data theft**. Seleccione **Next** para
    continuar.

![A screenshot of a computer Description automatically
generated](./media/image68.png)

1.  En la página **Name and description**, rellene los campos
    siguientes:

    - Name (required): Data theft by a user

    - Description (optional): This is a test policy for the preventing
      data theft.

2.  Seleccione **Next** para continuar.

![A screenshot of a computer Description automatically
generated](./media/image69.png)

3.  En la página **Choose users and groups**, seleccione **Include all
    users and groups**. Seleccione **Next** para continuar.

![A screenshot of a computer Description automatically
generated](./media/image53.png)

4.  En la página **Decide whether to prioritize**, seleccione **I want
    to specify priority content**. Seleccione la casilla de verificación
    Sensitivity labels y Sensitive info types. Seleccione **Next** para
    continuar.

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image70.png)

5.  En la página **Sensitivity labels to prioritize**, seleccione **Add
    or edit sensitivity labels**. En el panel desplegable, seleccione
    Internal/Employee data (HR) y seleccione **Add**. A continuación,
    haga clic en **Next**.

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image71.png)

6.  En la página **Sensitive info types to prioritize page**,
    seleccione **Add or edit sensitive info types**. En el panel
    desplegable, busque y seleccione Credit Card Number, Contoso
    Employee ID and Contoso Employee EDM. Seleccione **Add**. A
    continuación, haga clic en **Next**.

![A screenshot of a computer Description automatically
generated](./media/image72.png)

7.  En **Decide whether to score only activity with priority content**,
    seleccione **Get alerts for all activity**. Seleccione **Next**.

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image73.png)

8.  En la página **triggers for this policy**, seleccione **default** y,
    a continuación, **next**.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image74.png)

9.  **En** la página **Indicators**, seleccione **Turn on indicators**.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image75.png)

10. Seleccione **Select all** en Office **indicators** y haga clic en
    **Save**.

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image76.png)

11. Seleccione todas las opciones y haga clic en **Next**.

![A screenshot of a computer Description automatically
generated](./media/image77.png)

12. En la página **Detection options**, seleccione la opción
    predeterminada y, a continuación, **Next**.

![A screenshot of a computer Description automatically
generated](./media/image78.png)

13. En la página **de indicators**, seleccione **Next**.

![A screenshot of a computer Description automatically
generated](./media/image60.png)

14. En **Decide whether to use default or custom indicator thresholds**,
    seleccione **Customise thresholds**, utilice 1, 2 y 3 eventos para
    cada etapa respectivamente y, a continuación, seleccione **Next**.

![A screenshot of a computer screen Description automatically
generated](./media/image79.png)

15. En Review settings and finish, seleccione **Submit**.

![A screenshot of a computer Description automatically
generated](./media/image80.png)

16. En Your policy was created, seleccione **Done**.

![A screenshot of a computer Description automatically
generated](./media/image81.png)

17. Mantenga la pestaña abierta y continúe con la siguiente tarea.

#### Paso 2 - Puntúe la política 

1.  Haga clic en la nueva política denominada **Data theft by a user**.
    Seleccione **Start scoring activity for users**.

![A screenshot of a computer Description automatically
generated](./media/image82.png)

2.  En el campo **Reason** del panel **Add users to multiple policies**,
    escriba **Testing the policy**.

![A screenshot of a computer Description automatically
generated](./media/image65.png)

3.  En el campo **This should last for (choose between 5 and 30 days)**,
    seleccione **10 Days**.

4.  Utilice el campo **Search User** para añadirlo a las políticas.
    Añada a Peter. A continuación, haga clic en **Start scoring
    activity**.

![A screenshot of a computer screen Description automatically
generated](./media/image83.png)

5.  Una vez que reciba la confirmación de que ha iniciado **Scoring
    activity for 1 users**, haga clic en **Close**.

![A screenshot of a computer Description automatically
generated](./media/image84.png)

### Tarea 3: Fuga de datos por parte de los usuarios

#### Paso 1 - Crear una nueva política 

1.  Si ha cerrado la ventana del navegador en la tarea anterior, abra
    **+++https://purview.microsoft.com+++** e inicie sesión con el
    nombre de usuario **pattif@WWLxXXXXXX.onmicrosoft.com y la
    contraseña de usuario.** (sustituya WWLxXXXXXX por el prefijo de su
    tenant que aparece en la pestaña de recursos).

2.  Vaya a **Insider Risk Management** y seleccione la pestaña
    **Policies**. Seleccione **Create policy** para abrir el asistente
    de políticas.

![A screenshot of a computer Description automatically
generated](./media/image47.png)

3.  En la página **Choose a policy template**, seleccione **Data
    leaks**, en **Data leaks**. Seleccione **Next** para continuar.

![A screenshot of a computer Description automatically
generated](./media/image85.png)

4.  En la página **Name and description**, rellene los campos
    siguientes:

    - Name (required): Data leaks by a user

    - Description (optional): This is a test policy for the preventing
      data leaks.

5.  Seleccione **Next** para continuar.

![A screenshot of a computer Description automatically
generated](./media/image86.png)

6.  En la página **Choose users and groups**, seleccione **Include all
    users and groups**. Seleccione **Next** para continuar.

![A screenshot of a computer Description automatically
generated](./media/image53.png)

7.  En la página **Decide whether to prioritize**, seleccione **I want
    to specify priority content**. Seleccione la casilla de verificación
    Sitios SharePoint, Sensitivity labels y Sensitive Info types.
    Seleccione **Next** para continuar.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image87.png)

8.  En la página **SharePoint sites to prioritize**, seleccione **Add or
    edit SharePoint sites**. En el panel desplegable, seleccione **https
    ://wwlxXXXXXX .sharepoint.com/sites /ContosoWeb1** y seleccione Add.
    A continuación, haga clic en **Next**.

9.  En la página **Sensitivity labels to prioritize**, seleccione **Add
    or edit sensitivity labels**. En el panel desplegable, seleccione
    Internal/Employee data (HR) y seleccione **Add**. A continuación,
    haga clic en **Next**.

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image71.png)

10. En la página **Sensitive info types to prioritize**, seleccione
    **Add or edit sensitive info types**. En el panel desplegable,
    busque y seleccione Credit Card Number, Contoso Employee
    ID y Contoso Employee EDM. Seleccione **Add**. A continuación, haga
    clic en **Next**.

![A screenshot of a computer Description automatically
generated](./media/image72.png)

11. En **Decide whether to score only activity with priority content,**
    seleccione **Get alerts for all activity**. Seleccione **Next**.

![A screenshot of a computer screen Description automatically generated
with medium confidence](./media/image73.png)

12. En la página **triggers for this policy**, seleccione el botón de
    opción situado cerca de **User performs an exfiltration**
    **activity**. En **select which activities will trigger this
    policy**, seleccione todas las opciones disponibles, especialmente
    **Download content from SharePoint** y, a continuación, **Next**.

![A screenshot of a computer Description automatically
generated](./media/image88.png)

13. En **Triggering thresholds for this policy**, seleccione **Use
    custom thresholds**. Establezca cada umbral en **1** y seleccione
    **Next**.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image89.png)

14. Seleccione la configuración predeterminada en la página
    **Indicators** y seleccione **Next**.

15. En **Decide whether to use default or custom indicator thresholds**,
    seleccione **Customise thresholds**, utilice 1, 2 y 3 eventos para
    cada etapa respectivamente y, a continuación, seleccione **Next**.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image90.png)

16. En Review settings and finish, seleccione **Submit**.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image91.png)

17. En Your policy was created, seleccione **Done**.

![A screenshot of a computer Description automatically
generated](./media/image92.png)

18. Mantenga la pestaña abierta y continúe con la siguiente tarea.

#### Paso 2 - Puntúe la política 

1.  Haga clic en la nueva política denominada Data leaks by a user.
    Seleccione **Start scoring activity for users**.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image93.png)

2.  En el campo **Reason** del panel **Add users to multiple policies**,
    escriba **Testing the policy**. En el campo **This should last for
    (choose between 5 and 30 days)**, seleccione **10 days**. Utilice el
    campo **Search user to add to policies**. Añada a Brooke, Connie y
    Chris. A continuación, haga clic en **Start scoring activity**.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image94.png)

3.  Una vez que reciba la confirmación de que ha iniciado **Scoring
    activity for 3 users**, haga clic en **Close**.

![A screenshot of a computer Description automatically generated with
medium confidence](./media/image95.png)

Ha creado correctamente las políticas de Insider Risk Management.

## Resumen:

En este laboratorio exploramos la configuración de Insider Risk
Management de principio a fin. Con su propia suscripción y licencias,
también puede utilizar esta guía de laboratorio para crear una
configuración de Azure que también se puede utilizar para crear varias
alertas (que incluye el envío de correos electrónicos con datos
restringidos, lo cual no es posible desde una suscripción de prueba)
para las políticas de gestión de Insider Risk que puede utilizar para
explorar la función de protección adaptable en Purview.
