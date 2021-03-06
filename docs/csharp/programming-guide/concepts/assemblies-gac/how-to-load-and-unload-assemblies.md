---
title: 'Cómo: Cargar y descargar ensamblados (C#)'
ms.date: 07/20/2015
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
ms.openlocfilehash: fe9f78e145e6b7bc8ef138ff5cdb98aa345b90c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-load-and-unload-assemblies-c"></a>Cómo: Cargar y descargar ensamblados (C#)
Los ensamblados a los que hace referencia el programa se cargarán automáticamente en tiempo de compilación, pero también es posible cargar ensamblados específicos en el dominio de aplicación actual en tiempo de ejecución. Para obtener más información, vea [Cómo: Cargar ensamblados en un dominio de aplicación](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).  
  
 No existe ninguna forma de descargar un ensamblado individual sin descargar todos los dominios de aplicación que lo contienen. Aunque el ensamblado esté fuera de ámbito, el archivo de ensamblado actual permanecerá cargado hasta que se descarguen todos los dominios de aplicación que lo contienen.  
  
 Si desea descargar algunos ensamblados pero no otros, considere la posibilidad de crear un nuevo dominio de aplicación, ejecutar el código en el dominio y, a continuación, descargar ese dominio de aplicación. Para obtener más información, vea [Cómo: Descargar un dominio de aplicación](../../../../framework/app-domains/how-to-unload-an-application-domain.md).  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a>Para cargar un ensamblado en un dominio de aplicación  
  
1.  Utilice uno de los diversos métodos de carga de las clases <xref:System.AppDomain> y <xref:System.Reflection>. Para obtener más información, vea [Cómo: Cargar ensamblados en un dominio de aplicación](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).  
  
### <a name="to-unload-an-application-domain"></a>Para descargar un dominio de aplicación  
  
1.  No existe ninguna forma de descargar un ensamblado individual sin descargar todos los dominios de aplicación que lo contienen. Utilice el método `Unload` de <xref:System.AppDomain> para descargar los dominios de aplicación. Para obtener más información, vea [Cómo: Descargar un dominio de aplicación](../../../../framework/app-domains/how-to-unload-an-application-domain.md).  
  
## <a name="see-also"></a>Vea también  
 [Guía de programación de C#](../../../../csharp/programming-guide/index.md)  
 [Assemblies and the Global Assembly Cache (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md) (Ensamblados y caché global de ensamblados [C#])  
 [Cómo: Cargar ensamblados en un dominio de aplicación](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
