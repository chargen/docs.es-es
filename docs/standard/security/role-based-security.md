---
title: Seguridad basada en roles
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- role-based security, about role-based security
- user authentication, principals
- principals [.NET Framework]
- security [.NET Framework], role-based
- permissions [.NET Framework], principals
- authentication [.NET Framework], principals
- role-based security, principals
ms.assetid: 578cc32b-5654-4d8b-9d8c-ebcbc5c75390
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 596165bfac9c65898448714a4477b7f045bd87d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="role-based-security"></a>Seguridad basada en roles
Suelen usarse roles en aplicaciones empresariales o financieras para aplicar la directiva. Por ejemplo, una aplicación puede imponer límites en el tamaño de la transacción que se va a procesar según si el usuario que realiza la solicitud es un miembro de rol especificado. Los empleados podrían tener autorización para procesar las transacciones que son inferiores a un umbral especificado, los supervisores podrían tener un límite mayor y los vicepresidentes podrían tener un límite aún mayor (o ningún límite). La seguridad basada en roles también se puede usar cuando una aplicación requiere varias aprobaciones para completar una acción. Este caso podría ser un sistema de compras en el que cualquier empleado puede generar una solicitud de compra, pero solo un agente de compras puede convertir la solicitud en un pedido de compras que se pueden enviar a un proveedor.  
  
 La seguridad basada en roles de .NET Framework admite la autorización haciendo que la información sobre el principal, que se construye a partir de una identidad asociada, esté disponible para el subproceso actual. La identidad (y la entidad de seguridad que ayuda a definir) puede estar basada en una cuenta de Windows o puede ser una identidad personalizada no relacionada con una cuenta de Windows. Las aplicaciones de .NET Framework pueden tomar decisiones sobre autorización basándose en la identidad de la entidad de seguridad, en su pertenencia a un rol o ambas. Un rol es un conjunto de entidades de seguridad que tienen los mismos privilegios de seguridad (como un tesorero o un administrador). Una entidad de seguridad puede ser miembro de uno o varios roles. Por lo tanto, las aplicaciones pueden usar la pertenencia a un rol para determinar si una entidad de seguridad está autorizada para realizar una acción solicitada.  
  
 Para facilitar el uso y mejorar la coherencia con la seguridad de acceso del código, la seguridad basada en roles de .NET Framework proporciona objetos <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType> que permiten a Common Language Runtime realizar la autorización de forma similar a las comprobaciones de seguridad de acceso del código. La clase <xref:System.Security.Permissions.PrincipalPermission> representa la identidad o el rol con los que la entidad de seguridad debe coincidir y es compatible con las comprobaciones de seguridad declarativa e imperativa. También puede acceder directamente a la información de identidad de una entidad de seguridad y realizar las comprobaciones de identidad y de rol en el código cuando sea necesario.  
  
 .NET Framework proporciona compatibilidad de seguridad basada en roles que es suficientemente flexible y ampliable para satisfacer las necesidades de una amplia variedad de aplicaciones. Puede elegir interoperar con infraestructuras de autenticación existentes, como los servicios COM+ 1.0, o crear un sistema de autenticación personalizado. La seguridad basada en roles está especialmente indicada para aplicaciones web de ASP.NET, que se procesan principalmente en el servidor. Sin embargo, la seguridad basada en roles de .NET Framework puede usarse en el cliente o en el servidor.  
  
 Antes de leer esta sección, asegúrese de que comprende el material presentado en [conceptos clave de seguridad](../../../docs/standard/security/key-security-concepts.md).  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Objetos Principal e Identity](../../../docs/standard/security/principal-and-identity-objects.md)|Explica cómo configurar y administrar identidades y entidades de seguridad de Windows y genéricas.|  
|[Conceptos clave de seguridad](../../../docs/standard/security/key-security-concepts.md)|Presenta los conceptos fundamentales que debe conocer antes de usar la seguridad de .NET Framework.|  
  
## <a name="reference"></a>Referencia  
 <xref:System.Security.Permissions.PrincipalPermission?displayProperty=nameWithType>
