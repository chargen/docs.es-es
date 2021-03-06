---
title: Actividad Wait For Input
ms.date: 03/30/2017
ms.assetid: d58c344e-9ee8-4ce2-b199-75b3fe45237f
ms.openlocfilehash: 750a217699abe8b2eb2eaaa364002137d335a41a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="wait-for-input-activity"></a>Actividad Wait For Input
Este ejemplo muestra cómo crear marcadores con nombre en un flujo de trabajo. Windows Workflow Foundation (WF) no proporciona una actividad para la creación declarativa de marcadores. Por consiguiente, si desea crear un marcador en su flujo de trabajo, deberá escribir una actividad personalizada que lo cree. La actividad `WaitForInput` definida en este ejemplo proporciona esta funcionalidad, para que los usuarios puedan crear los marcadores mediante declaración dentro de un flujo de trabajo.  
  
## <a name="projects-in-this-sample"></a>Proyectos en este ejemplo  
  
|**Nombre del proyecto**|**Descripción**|**Archivos principales**|  
|-|-|-|  
|WaitForInput|Contiene la actividad `WaitForInput` y su diseñador.|WaitForInput.cs<br /><br /> Definición de la actividad `WaitForInput`.|  
|||WaitForInputDesigner.xaml<br /><br /> Diseñador personalizado para la actividad `WaitForInput`.|  
|||TypeToFirstGenericArgumentConverter.cs<br /><br /> Convertidor de tipos de WPF utilizado para actualizar el tipo genérico de la actividad en el diseñador.|  
|WaitForInputTestClient|Aplicación cliente de muestra que configura y ejecuta un flujo de trabajo mediante varias actividades WaitForInput con el diseñador de flujo de trabajo.|Sequence1.xaml<br /><br /> Flujo de trabajo secuencial que utiliza la actividad `WaitForInput`.|  
|||Program.cs<br /><br /> Ejecuta una instancia de flujo de trabajo definida en Sequence1.xaml.|  
  
## <a name="waitforinput-activity"></a>Actividad WaitForInput  
 La actividad `WaitForInput` crea un marcador con nombre en un flujo de trabajo. El marcador espera una señal y recibe datos de su tipo configurado. Una vez reanudado el marcador, los datos pasados al flujo de trabajo están disponibles a través de la propiedad `Result`.  
  
 La actividad `WaitForInput` se deriva de la clase <xref:System.Activities.NativeActivity> porque debe crear marcadores, que solo son accesibles a través de la clase <xref:System.Activities.NativeActivityContext>.  
  
 La actividad tiene tres atributos aplicados para enlazar un diseñador, agregando la característica de argumento genérico que se puede actualizar y estableciendo el tipo genérico predeterminado como cadena. La actividad también tiene los argumentos enumerados en la siguiente tabla.  
  
|**Name**|**Type**|**Descripción**|  
|-|-|-|  
|TResult|El argumento genérico (TResult)|El tipo del marcador. Este es el tipo de datos que se va a pasar al marcador cuando se reanude.|  
|BookmarkName|InArgument\<cadena >|Nombre del marcador.|  
|Resultado|InArgument\<TResult >|Los datos pasados a la actividad cuando se reanuda el marcador.|  
  
## <a name="waitforinput-activity-designer"></a>Diseñador de la actividad de WaitForInput  
 El diseñador de la actividad `WaitForInput` se implementa en el archivo WaitForInputDesigner.xaml. La actividad `WaitForInput` y su diseñador están incluidos en el mismo ensamblado. El siguiente gráfico muestra la actividad `WaitForInput` en el cuadro de herramientas dentro de una categoría que tiene el mismo nombre que el ensamblado.  
  
 ![Captura de pantalla de cuadro de herramientas de WaitForInput](../../../../docs/framework/windows-workflow-foundation/samples/media/waitforinputtoolbox.jpg "WaitForInputToolbox")  
  
 El siguiente gráfico muestra el diseñador de `WaitForInput`. Dado que la actividad `WaitForInput` es muy básica, el diseñador permite establecer el valor de todos sus argumentos directamente en la superficie del diseñador.  
  
 ![Diseñador de actividad de WaitForInput](../../../../docs/framework/windows-workflow-foundation/samples/media/waitforinputdesigner.jpg "WaitForInputDesigner")  
  
#### <a name="to-use-this-sample"></a>Para utilizar este ejemplo  
  
1.  Abra el archivo WaitForInput.sln con [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Para compilar la solución, presione Ctrl+MAYÚS+B.  
  
3.  Para iniciar el ejemplo sin depurar, presione CTRL+F5.  
  
> [!IMPORTANT]
>  Puede que los ejemplos ya estén instalados en su equipo. Compruebe el siguiente directorio (predeterminado) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si este directorio no existe, vaya a [Windows Communication Foundation (WCF) y ejemplos de Windows Workflow Foundation (WF) para .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para descargar todos los Windows Communication Foundation (WCF) y [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ejemplos. Este ejemplo se encuentra en el siguiente directorio.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\WaitForInput`