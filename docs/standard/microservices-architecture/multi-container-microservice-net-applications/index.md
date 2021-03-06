---
title: Diseñar y desarrollar aplicaciones .NET basadas en varios contenedores y microservicios
description: Arquitectura de microservicios de .NET para aplicaciones .NET en contenedor | Diseñar y desarrollar aplicaciones .NET basadas en varios contenedores y microservicios
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 297a53d6d6d37b1fa4a0e021919c9df86edeca03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="designing-and-developing-multi-container-and-microservice-based-net-applications"></a>Diseñar y desarrollar aplicaciones .NET basadas en varios contenedores y microservicios

*Si desarrolla aplicaciones de microservicios en contenedor significa que está compilando aplicaciones de varios contenedores. Pero una aplicación de varios contenedores también podría ser más sencilla (por ejemplo, una aplicación de tres niveles) y podría no compilarse con una arquitectura de microservicios.*

Previamente planteamos la pregunta “¿Se necesita Docker para compilar una arquitectura de microservicios?”. La respuesta es un no rotundo. Docker es un habilitador y puede proporcionar grandes ventajas, pero los contenedores y Docker no son un requisito imprescindible para los microservicios. Por ejemplo, podría crear una aplicación basada en microservicios con o sin Docker al usar Azure Service Fabric, que es compatible con los microservicios que se ejecutan como procesos simples o como contenedores de Docker.

Pero si sabe cómo diseñar y desarrollar una aplicación basada en microservicios que también se base en contenedores de Docker, podrá diseñar y desarrollar cualquier modelo de aplicación más sencillo. Por ejemplo, podría diseñar una aplicación de tres niveles que también requiera un enfoque de varios contenedores. Debido a eso, y dado que las arquitecturas de microservicios son una tendencia importante en el mundo de los contenedores, esta sección se centra en la implementación de una arquitectura de microservicios con contenedores de Docker.


>[!div class="step-by-step"]
[Anterior] (../containerize-net-framework-applications/index.md) [Siguiente] (microservice-application-design.md)
