# Laboratorio 3 - Gestión de Trainable Classifiers

## Objetivo:

El tenant Contoso Ltd. contiene una colección de sitios de SharePoint
con el nombre "Ventas y marketing" que se utilizará en el futuro para
almacenar varios documentos e informes relacionados con las finanzas.
Debido a la naturaleza de estos documentos, necesita crear un
clasificador entrenable para reconocer y etiquetar estos archivos. Para
ello, activará los Trainable Classifiers personalizados y creará uno
nuevo en este laboratorio.

**Importante** Después de activar los Trainable Classifiers en un
tenant, pasarán entre 7 y 14 días antes de que se puedan crear
clasificadores personalizados entrenables. El botón para crear un nuevo
clasificador entrenable no estará disponible hasta que se haya
completado todo el proceso de activación. Por lo tanto, ahora sólo podrá
realizar la tarea 1. Si desea completar las tareas 2 y 3, deberá esperar
hasta que finalice el procesamiento de la configuración del clasificador
entrenable. El tenant de Microsoft 365 que está utilizando para realizar
la tarea 1 debería seguir activo durante 30 días junto con su entorno.

## Ejercicio 1 - Activación de los Trainable Classifiers

Antes de poder crear Trainable Classifiers personalizados, es necesario
activar la función en un tenant. Para activar los permisos de
administrador global son necesarios, se cerrará la sesión de cuenta de
Patti Fernández y utilizar el administrador de MOD para activar la
función en primer lugar.

1.  En **Microsoft Edge**, vaya a **https://compliance.microsoft.com.**

2.  Inicie sesión en el portal como **Administrador MOD** utilizando las
    credenciales proporcionadas en la pestaña de recursos de su entorno
    de laboratorio.

![A screenshot of a computer Description automatically
generated](./media/image1.png)

3.  Vaya a **Classifiers** en **Data Classification** en el panel de
    navegación izquierdo y seleccione **Trainable Classifiers** en el
    panel superior.

4.  Cuando aparezca la ventana **Get started with trainable
    classifiers**, seleccione **Start scanning process**.

![BrokenImage](./media/image2.png)

5.  Actualice la ventana del navegador.

6.  Lea el banner de información en la parte superior de la ventana con
    el mensaje **To set you up for creating trainable classifiers, we're
    currently scanning your content locations to generate analytics that
    will help us learn what type of content is in your organization.
    This process will take 7 to 14 days to complete**.

7.  Deje el cliente abierto.

Ha activado correctamente los Trainable Classifiers en su inquilino.
Ahora deberá esperar entre 7 y 14 días hasta que el botón **Crear
Trainable Classifiers** esté disponible. Si se encuentra en un entorno
de aula y no dispone de 7 a 14 días para esperar a que Trainable
Classifiers complete el procesamiento, puede realizar el resto de las
tareas de este ejercicio iniciando sesión en el tenant que se le
proporcionó más tarde, cuando el procesamiento de Trainable Classifiers
haya finalizado. Su tenant debería seguir activo.

**Nota**:

Los siguientes ejercicios requerirán que los Trainable Classifiers
creados estén activos. Puede realizar estos ejercicios después como
tarea para casa.

## Ejercicio 1 - Creación de un clasificador entrenable 

En esta tarea, Patti creará un nuevo clasificador entrenable y
seleccionará diferentes sitios de SharePoint para identificar datos
típicos creados y almacenados por Contoso Ltd.

1.  En **Microsoft Edge**, abra una **nueva ventana privada**, vaya a
    **+++https://purview.microsoft.com+++** e inicie sesión como **Patti
    Fernandez** utilizando el nombre de usuario
    **PattiF@WWLxXXXXXX.onmicrosoft.com** y la contraseña de usuario que
    aparece en la pestaña de recursos.

2.  En el menú de navegación de la izquierda, seleccione **Solutions**
    \> **Data Loss Prevention**.

![A screenshot of a computer Description automatically
generated](./media/image3.png)

3.  

4.  

5.  

6.  

7.  

8.  

9.  

10. Expanda **Classifiers** desde el panel izquierdo. Seleccione
    **Trainable** **Classifiers** en el panel de subnavegación.
    Seleccione **+ Create trainable classifier** para crear un nuevo
    clasificador.

![](./media/image4.png)

11. Introduzca la siguiente información en la página **Name and describe
    your trainable classifier**:

12. Name: **+++Contoso Company Data+++**

13. Description: **+++Trainable classifier for company data produced and
    stored by Contoso Ltd.+++**

14. Seleccione **Next**.

![A screenshot of a computer Description automatically
generated](./media/image5.png)

15. Seleccione **Choose sites** para abrir el panel lateral derecho.

![A screenshot of a computer Description automatically
generated](./media/image6.png)

16. Seleccione los siguientes sitios de SharePoint y seleccione **Add**.

    - 

    - 

    - 

    - Brand

    - Digital Initiative Public Relations

    - Work

    - Sales and Marketing

    - 

    - Mark 8 Project Team

    - 

    - 

    - 

    - 

    - 

![](./media/image7.png)

- 
- 
- 
- 
- 

17. Espere hasta que el sitio elegido aparezca en la lista y seleccione
    **Next**.

![A screenshot of a computer Description automatically
generated](./media/image8.png)

18. En la **página Source of the negative sample content**, seleccione
    el sitio **Learn** y, a continuación, **Next**.

19. Revise la configuración y seleccione **Create trainable
    classifier**.

![A screenshot of a computer Description automatically
generated](./media/image9.png)

20. Cuando aparezca el mensaje Your trainable classifier was created,
    seleccione **Done**.

21. 

Ahora se analizan los documentos y archivos del sitio SharePoint
elegido, lo que puede tardar hasta 24 horas.

Puede explorar los clasificadores ya existentes para revisarlos.

## 

1.  
2.  
3.  
4.  
5.  
6.  
7.  - 
    - 
    - 
    - 
    - 
    - 
    - 
    - 
    - 
    - 
    - 
    - 
    - 
    - 
    - 
    - 
    - 
    - 
    - 
    - 
8.  
9.  
10. 
11. 
12. 
13. 
14. 
15. 
16. 
17. 
18. 
19. 
20. 
21. 
22. 
23. 

## Resumen:

Ha creado con éxito un clasificador entrenable personalizado que
coincide con los archivos almacenados en los sitios SharePoint
existentes de Contoso Ltd.
