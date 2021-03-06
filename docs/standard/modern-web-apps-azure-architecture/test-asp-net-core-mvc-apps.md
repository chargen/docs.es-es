---
title: Prueba de aplicaciones ASP.NET Core MVC
description: Diseño de aplicaciones web modernas con ASP.NET Core y Azure | Prueba de aplicaciones ASP.NET Core MVC
author: ardalis
ms.author: wiwagn
ms.date: 10/08/2017
ms.openlocfilehash: 7b4bcb1c39ddbbc104820558532b03bc9341804e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="test-aspnet-core-mvc-apps"></a>Prueba de aplicaciones ASP.NET Core MVC

> _"Si no le gusta realizar pruebas unitarias de su producto, lo más probable es que a los clientes tampoco les guste probarlo"._
> - Anónimo

## <a name="summary"></a>Resumen

En el software de cualquier complejidad se pueden producir errores inesperados en respuesta a los cambios. Por tanto, es necesario realizar pruebas después de realizar cambios en todas las aplicaciones menos en las más triviales (o las menos críticas). Las pruebas manuales son la forma más lenta, menos confiable y más costosa de probar software. Desafortunadamente, si las aplicaciones no están diseñadas para que se puedan probar, puede ser el único medio disponible. Las aplicaciones escritas para seguir los principios arquitectónicos descritos en el capítulo X deben poder someterse a pruebas unitarias y las aplicaciones ASP.NET Core también admiten pruebas de integración y funcionales automatizadas.

## <a name="kinds-of-automated-tests"></a>Tipos de pruebas automatizadas

Hay muchos tipos de pruebas automatizadas para las aplicaciones de software. La prueba más sencilla y de nivel más bajo es la prueba unitaria. En un nivel ligeramente superior se encuentran las pruebas de integración y las pruebas funcionales. Otros tipos de pruebas, como las de interfaz de usuario, de carga, de esfuerzo y de humo, quedan fuera del ámbito de este documento.

### <a name="unit-tests"></a>Pruebas unitarias

Una prueba unitaria prueba un único elemento de la lógica de la aplicación. Se puede describir aún más enumerando algunas de las cosas que no hace. Una prueba unitaria no prueba el funcionamiento del código con dependencias o infraestructura; eso lo comprueban las pruebas de integración. Una prueba unitaria no prueba el marco para el que se escribe el código; se debe asumir que funciona o, si se detecta que no lo hace, registrar un error y codificar una solución alternativa. Una prueba unitaria se ejecuta completamente en memoria y en proceso. No se comunica con el sistema de archivos, la red o una base de datos. Las pruebas unitarias solo deben probar el código.

Las pruebas unitarias, como solo prueban una unidad del código, sin dependencias externas, se deben ejecutar muy rápidamente. Por tanto, debe ser capaz de ejecutar conjuntos de cientos de pruebas unitarias en unos segundos. Ejecute las pruebas con frecuencia, idealmente antes de cada inserción en un repositorio de control de código fuente compartido y, por supuesto, con cada compilación automatizada en el servidor de compilación.

### <a name="integration-tests"></a>Pruebas de integración

Aunque es una buena idea encapsular el código que interactúa con la infraestructura como bases de datos y sistemas de archivos, seguirá disponiendo de parte de ese código y, probablemente le interesará probarlo. Además, debe comprobar que las capas del código interactúan según lo esperado cuando se resuelvan completamente las dependencias de la aplicación. Esta es la responsabilidad de las pruebas de integración. Las pruebas de integración tienden a ser más lentas y más difíciles de configurar que las pruebas unitarias, porque a menudo dependen de la infraestructura y de dependencias externas. Por tanto, debe evitar realizar pruebas de cosas que podrían ser pruebas con pruebas unitarias en pruebas de integración. Si un escenario determinado se puede probar con una prueba unitaria, debe probarlo con una prueba unitaria. Si no es posible, considere la posibilidad de usar una prueba de integración.

Las pruebas de integración a menudo tendrán procedimientos más complejos de instalación y desmontaje que las pruebas unitarias. Por ejemplo, una prueba de integración dirigida a una base de datos real necesitará un modo de devolver la base de datos a un estado conocido antes de cada serie de pruebas. Cuando se agregan nuevas pruebas y el esquema de base de datos de producción evoluciona, estos scripts de prueba tienden a aumentar de tamaño y complejidad. En muchos sistemas de gran tamaño, no resulta práctico ejecutar conjuntos completos de pruebas de integración en las estaciones de trabajo de desarrollador antes de insertar en el repositorio los cambios en el control de código fuente compartido. En estos casos, las pruebas de integración se pueden ejecutar en un servidor de compilación.

La clase de implementación LocalFileImageService implementa la lógica para recuperar y devolver los bytes de un archivo de imagen de una carpeta concreta con un identificador dado:

```cs
public class LocalFileImageService : IImageService
{
    private readonly IHostingEnvironment _env;
    public LocalFileImageService(IHostingEnvironment env)
    {
        _env = env;
    }
    public byte[] GetImageBytesById(int id)
    {
        try
        {
            var contentRoot = _env.ContentRootPath + "//Pics";
            var path = Path.Combine(contentRoot, id + ".png");
            return File.ReadAllBytes(path);
```

### <a name="functional-tests"></a>Pruebas funcionales

Las pruebas de integración se escriben desde la perspectiva del desarrollador, para comprobar que algunos componentes del sistema funcionen correctamente entre sí. Las pruebas funcionales se escriben desde la perspectiva del usuario y comprueban la exactitud del sistema en función de sus requisitos. En el fragmento siguiente se ofrece una analogía útil para saber cómo pensar en las pruebas funcionales, en comparación con las pruebas unitarias:

> "En muchas ocasiones, el desarrollo de un sistema se asemeja a la construcción de una casa. Aunque esta analogía no es del todo correcta, podemos ampliarla para explicar la diferencia entre las pruebas unitarias y las funcionales. Las pruebas unitarias son similares a un inspector municipal que visita la obra de construcción de una casa. Se centra en los distintos sistemas internos de la casa, los cimientos, los muros, la instalación eléctrica, la fontanería y así sucesivamente. Se asegura (prueba) de que las partes de la casa funcionarán correctamente y de manera segura, es decir, cumplen el código de construcción. En este escenario, las pruebas funcionales son análogas al propietario que visita esta misma obra. Da por supuesto que los sistemas internos se comportarán de forma adecuada, que el inspector municipal está realizando su trabajo. El propietario se centra en cómo será vivir en esta casa. Le preocupa el aspecto de la casa, si las distintas habitaciones tienen un tamaño cómodo, si la casa se ajusta a las necesidades de la familia, si las ventanas están en una zona adecuada para captar el sol por la mañana. El propietario está realizando pruebas funcionales de la casa. Tiene la perspectiva del usuario. El inspector municipal está realizando pruebas unitarias en la casa. Tiene la perspectiva del constructor".

Fuente: [Unit Testing versus Functional Tests](http://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html) (Diferencias entre pruebas unitarias y pruebas funcionales)

Me gusta decir: "Como desarrolladores, fallamos de dos maneras: creamos algo de forma incorrecta o creamos algo incorrecto". Las pruebas unitarias aseguran que se cree algo de forma correcta y las pruebas funcionales que se cree algo correcto.

Como las pruebas funcionales operan en el nivel de sistema, pueden requerir cierto grado de automatización de la interfaz de usuario. Al igual que las pruebas de integración, también suelen funcionar con algún tipo de infraestructura de pruebas. Esto hace que sean más lentas y frágiles que las pruebas unitarias y las de integración. Solo se deben tener las pruebas funcionales necesarias para estar seguro de que el sistema se comporta tal y como esperan los usuarios.

### <a name="testing-pyramid"></a>Pirámide de pruebas

Martin Fowler escribió sobre la pirámide de pruebas, de la que se muestra un ejemplo en la figura 9-1.

![](./media/image9-1.png)

Figura 9-1 Pirámide de pruebas

Los diferentes niveles de la pirámide y sus tamaños relativos representan distintos tipos de pruebas y cuántas se deben escribir para la aplicación. Como se puede ver, la recomendación es tener una base grande de pruebas unitarias, respaldada por un nivel más pequeño de pruebas de integración, con un nivel incluso más pequeño de pruebas funcionales. Idealmente, cada nivel solo debería incluir las pruebas que no se puedan realizar de forma adecuada en un nivel inferior. Tenga presente la pirámide de pruebas al tratar de decidir qué tipo de prueba necesita para un escenario determinado.

### <a name="what-to-test"></a>Qué se va a probar

Un problema común para los desarrolladores sin experiencia con la escritura de pruebas automatizadas es determinar lo que se debe probar. Un buen punto de partida es probar la lógica condicional. Siempre que haya un método con un comportamiento que cambia en función de una instrucción condicional (if-else, switch, etc.), debería poder dar idear al menos un par de pruebas que confirmen el comportamiento correcto para determinadas condiciones. Si el código tiene condiciones de error, es conveniente escribir al menos una prueba para la "ruta feliz" a través del código (sin errores) y al menos una prueba para la "ruta triste" (con errores o resultados pocos frecuentes) para confirmar que la aplicación se comporta según lo previsto ante los errores. Por último, intente centrarse en probar cosas en las que se pueda producir un error, en lugar de centrarse en métricas como la cobertura de código. Por lo general, es mejor tener más cobertura de código que menos. Pero escribir algunas pruebas más de un método muy complejo y esencial para la empresa suele ser un mejor uso del tiempo que escribir pruebas para propiedades automáticas solo para mejorar la métrica de cobertura del código de prueba.

## <a name="organizing-test-projects"></a>Organizar los proyectos de prueba

Los proyectos de prueba se pueden organizar de la manera que mejor funcione. Es una buena idea separar las pruebas por tipo (prueba unitaria, prueba de integración) y por lo que van a probar (por proyecto, por espacio de nombres). Que esta separación conste de carpetas dentro de un único proyecto de prueba o de varios es una decisión de diseño. Lo más sencillo es un proyecto, pero para proyectos grandes con muchas pruebas, o bien para ejecutar más fácilmente otros conjuntos de pruebas, es posible que le interese tener varios proyectos de prueba distintos. Muchos equipos organizan los proyectos de prueba en función del proyecto que se está probando, que para las aplicaciones con más de unos pocos proyectos puede provocar un gran número de proyectos de prueba, en especial si se siguen dividiendo según el tipo de pruebas de cada proyecto. Un enfoque de compromiso consiste en disponer de un proyecto por tipo de prueba, por aplicación, con carpetas dentro de los proyectos de prueba para indicar el proyecto (y la clase) que se van a probar.

Un enfoque común consiste en organizar los proyectos de la aplicación en una carpeta "src" y los proyectos de prueba en una carpeta "tests" paralela. Si esta organización le parece útil, puede crear carpetas de solución coincidentes en Visual Studio.

![](./media/image9-2.png)

Figura 9-2 Organización de las pruebas en la solución

Puede usar el marco de pruebas que prefiera. El marco de trabajo xUnit funciona bien y es en el que se escriben todas las pruebas de ASP.NET Core y EF Core. Puede agregar un proyecto de prueba de xUnit en Visual Studio con la plantilla que se muestra en la figura 9-3 o desde la CLI mediante dotnet new xunit.

![](./media/image9-3.png)

Figura 9-3 Agregar un proyecto de prueba de xUnit en Visual Studio

### <a name="test-naming"></a>Nombres de pruebas

Debe asignar nombres a las pruebas de forma coherente, con un nombre que indique lo que hace cada prueba. Un enfoque con el que he tenido buenos resultados consiste en asignar nombres a las clases de prueba en función de la clase y el método que estén probando. Esto da como resultado muchas clases de prueba pequeñas, pero deja muy claro la responsabilidad de cada una. Con el nombre de la clase de prueba configurado para identificar la clase y el método que se van a probar, se puede usar el nombre del método de prueba para especificar el comportamiento que se está probando. Esto debe incluir el comportamiento esperado y las entradas o suposiciones que deban producir este comportamiento. Algunos nombres de prueba de ejemplo:

-   CatalogControllerGetImage.CallsImageServiceWithId

-   CatalogControllerGetImage.LogsWarningGivenImageMissingException

-   CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess

-   CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException

Una variante de este enfoque finaliza cada nombre de clase de prueba con "Should" (Debería) y modifica ligeramente el tiempo:

-   CatalogControllerGetImage**Should**.**Call**ImageServiceWithId

-   CatalogControllerGetImage**Should**.**Log**WarningGivenImageMissingException

Para algunos equipos el segundo método de nomenclatura es más claro, aunque un poco más detallado. En cualquier caso, intente usar una convención de nomenclatura que proporcione información del comportamiento de la prueba, para que cuando se produzca un error en una o varias pruebas, sea obvio a partir de los nombres en qué casos se ha producido el error. Evite asignar nombres a las pruebas de forma vaga, como PruebasControlador.Prueba1, dado que no ofrecen ningún valor cuando se ven en los resultados de las pruebas.

Si sigue una convención de nomenclatura como la anterior que genera muchas clases de prueba pequeñas, es aconsejable organizar más las pruebas mediante carpetas y espacios de nombres. En la figura 9-4 se muestra un enfoque para organizar las pruebas por carpeta en varios proyectos de prueba.

![](./media/image9-4.png)

**Figura 9-4.** Organización de las clases de prueba por carpeta en función de la clase que se está probando.

Evidentemente, si una clase de aplicación determinada tiene muchos métodos para probar (y, por tanto, muchas clases de prueba), tiene sentido colocarlos en una carpeta correspondiente a la clase de aplicación. Esta organización es similar a cómo se podrían organizar los archivos en carpetas en otra parte. Si tiene más de tres o cuatro archivos relacionados en una carpeta que contiene otros muchos archivos, suele resultar útil moverlos a su propia subcarpeta.

## <a name="unit-testing-aspnet-core-apps"></a>Pruebas unitarias de aplicaciones ASP.NET Core

En una aplicación ASP.NET Core bien diseñada, la mayor parte de la complejidad y la lógica de negocios se encapsulará en entidades de negocio y una variedad de servicios. La propia aplicación ASP.NET Core MVC con sus controladores, filtros, modelos de vista y vistas, no debería requerir muchas pruebas unitarias. Gran parte de la funcionalidad de una acción determinada se encuentra fuera del propio método de acción. Comprobar si el enrutamiento funciona correctamente o el control de errores global, no se puede realizar de forma eficaz con una prueba unitaria. Del mismo modo, los filtros, incluidos los de autenticación y validación del modelo y los de autorización, no se pueden someter a pruebas unitarias. Sin estas fuentes de comportamiento, la mayoría de los métodos de acción deberían ser pequeños, y delegar la mayor parte de su trabajo a servicios que se puedan probar de forma independiente al controlador que los usa.

En ocasiones tendrá que refactorizar el código para poder realizar pruebas unitarias en él. Con frecuencia, esto implica la identificación de abstracciones y el uso de la inserción de dependencias para tener acceso a la abstracción en el código que se quiere probar, en lugar de codificar directamente en la infraestructura. Por ejemplo, considere este método de acción simple para mostrar imágenes:

```cs
[HttpGet("[controller]/pic/{id}")]
public IActionResult GetImage(int id)
{
    var contentRoot = _env.ContentRootPath + "//Pics";
    var path = Path.Combine(contentRoot, id + ".png");
    Byte[] b = System.IO.File.ReadAllBytes(path);
    return File(b, "image/png");
}
```

La realización de pruebas unitarias en este método se complica debido a su dependencia directa de System.IO.File, que usa para leer del sistema de archivos. Puede probar este comportamiento para asegurarse de que funciona de la forma esperada, pero si lo hace con archivos reales será una prueba de integración. Cabe mencionar que no se puede probar la ruta de este método: verá cómo hacerlo con una prueba funcional en breve.

Si no se pueden realizar directamente pruebas unitarias del comportamiento del sistema de archivos y no se puede probar la ruta, ¿qué se puede probar? Después de la refactorización para que las pruebas unitarias sean posibles, puede detectar varios casos de prueba y comportamiento que falta, como el control de errores. ¿Qué hace el método cuando no se encuentra un archivo? ¿Qué debería hacer? En este ejemplo, el método refactorizado tiene el aspecto siguiente:

```cs
[HttpGet("[controller]/pic/{id}")\]
public IActionResult GetImage(int id)
{
    byte[] imageBytes;
    try
    {
        imageBytes = _imageService.GetImageBytesById(id);
    }
    catch (CatalogImageMissingException ex)
    {
        _logger.LogWarning($"No image found for id: {id}");
        return NotFound();
    }
    return File(imageBytes, "image/png");
}
```

\_logger e \_imageService se insertan como dependencias. Ahora se puede probar que el mismo identificador que se pasa al método de acción se pasa a \_imageService, y que los bytes resultantes se devuelven como parte de FileResult. También se puede probar que el registro de errores se está realizando de la forma esperada y que se devuelve un resultado de NotFound si la imagen no se encuentra, suponiendo que se trate de un comportamiento importante de la aplicación (es decir, no solo código temporal que el desarrollador agregó para diagnosticar un problema). La lógica real del archivo se ha trasladado a un servicio de implementación independiente y se ha ampliado para devolver una excepción específica de la aplicación en el caso de un archivo que falta. Puede probar esta implementación de forma independiente, con una prueba de integración.

## <a name="integration-testing-aspnet-core-apps"></a>Pruebas de integración en aplicaciones ASP.NET Core

```cs
    }
        catch (FileNotFoundException ex)
        {
            throw new CatalogImageMissingException(ex);
        }
    }
}
```

En este servicio se usa IHostingEnvironment, como hacía el código de CatalogController antes de refactorizarlo en un servicio independiente. Como este era el único código del controlador que usaba IHostingEnvironment, esa dependencia se quitó del constructor de CatalogController.

Para comprobar que este servicio funciona correctamente, tendrá que crear un archivo de imagen de prueba conocida y comprobar que el servicio devuelve si se proporciona una entrada específica. También debe evitar el uso de objetos ficticios en el comportamiento que se quiere probar (en este caso, leer del sistema de archivos). Pero los objetos ficticios pueden seguir siendo útiles para configurar pruebas de integración. En este caso, se puede simular IHostingEnvironment para que su ContentRootPath apunte a la carpeta que se va a usar para la imagen de prueba. La clase de prueba de integración funcional completa se muestra aquí:

```cs
public class LocalFileImageServiceGetImageBytesById
{
    private byte[] _testBytes = new byte[] { 0x01, 0x02, 0x03 };
    private readonly Mock<IHostingEnvironment> _mockEnvironment = new Mock<IHostingEnvironment>();
    private int _testImageId = 123;
    private string _testFileName = "123.png";
    public LocalFileImageServiceGetImageBytesById()
    {
        // create folder if necessary
        Directory.CreateDirectory(Path.Combine(GetFileDirectory(), "Pics"));
        string filePath = GetFilePath(_testFileName);
        System.IO.File.WriteAllBytes(filePath, _testBytes);
        _mockEnvironment.SetupGet<string>(m => m.ContentRootPath).Returns(GetFileDirectory());
    }
    private string GetFilePath(string fileName)
    {
        return Path.Combine(GetFileDirectory(), "Pics", fileName);
        }
            private string GetFileDirectory()
        {
            var location = System.Reflection.Assembly.GetEntryAssembly().Location;
            return Path.GetDirectoryName(location);
        }

        [Fact]
        public void ReturnsFileContentResultGivenValidId()
        {
            var fileService = new LocalFileImageService(_mockEnvironment.Object);
            var result = fileService.GetImageBytesById(_testImageId);
            Assert.Equal(_testBytes, result);
        }
    }
```

> [!NOTE]
> La propia prueba es muy sencilla: la mayor parte del código es necesaria para configurar el sistema y crear la infraestructura de pruebas (en este caso, un archivo real que se va a leer del disco). Esto es normal para las pruebas de integración, que a menudo requieren un trabajo de configuración más complejo que las pruebas unitarias.

## <a name="functional-testing-aspnet-core-apps"></a>Pruebas funcionales en aplicaciones ASP.NET Core

Para las aplicaciones ASP.NET Core, la clase TestServer facilita considerablemente la creación de pruebas funcionales. Se configura un TestServer mediante un WebHostBuilder, como se hace normalmente para la aplicación. Este WebHostBuilder se debe configurar como el host real de la aplicación, pero se puede modificar cualquiera de sus aspectos para simplificar las pruebas. En la mayoría de los casos, se podrá volver a usar el mismo TestServer para muchos casos de prueba, por lo que se puede encapsular en un método reutilizable (por ejemplo, en una clase base):

```cs
public abstract class BaseWebTest
{
    protected readonly HttpClient _client;
    protected string _contentRoot;

    public BaseWebTest()
    {
        _client = GetClient();
    }
    
    protected HttpClient GetClient()
    {
        var startupAssembly = typeof(Startup).GetTypeInfo().Assembly;
        _contentRoot = GetProjectPath("src", startupAssembly);
        var builder = new WebHostBuilder()
        .UseContentRoot(_contentRoot)
        .UseStartup&lt;Startup&gt;();
        var server = new TestServer(builder);
        var client = server.CreateClient();
        return client;
    }
}
```

El método GetProjectPath simplemente devuelve la ruta de acceso física al proyecto web (solución de ejemplo de descarga). En este caso, WebHostBuilder simplemente especifica dónde está la raíz del contenido de la aplicación web y hace referencia a la misma clase de inicio que usa la aplicación web real. Para trabajar con TestServer, se usa el tipo System.Net.HttpClient estándar para realizar solicitudes. TestServer expone un método CreateClient útil que proporciona un cliente preconfigurado listo para realizar solicitudes a la aplicación que se ejecuta en TestServer. Este cliente (establecido en el miembro protegido \_client en la prueba base anterior) se usa al escribir las pruebas funcionales para la aplicación ASP.NET Core:

```cs
public class CatalogControllerGetImage : BaseWebTest
{
    [Fact]
    public async Task ReturnsFileContentResultGivenValidId()
    {
        var testFilePath = Path.Combine(_contentRoot, "pics//1.png");
        var expectedFileBytes = File.ReadAllBytes(testFilePath);
        var response = await _client.GetAsync("/catalog/pic/1");
        response.EnsureSuccessStatusCode();
        var streamResponse = await response.Content.ReadAsStreamAsync();
        byte[] byteResult;
        using (var ms = new MemoryStream())
        {
            streamResponse.CopyTo(ms);
            byteResult = ms.ToArray();
        }
        Assert.Equal(expectedFileBytes, byteResult);
    }
}
```

Esta prueba funcional ejecuta la pila de la aplicación ASP.NET Core MVC completa, incluidos todo el software intermedio, filtros, enlazadores, etc., que pueden estar definidos. Comprueba que una ruta determinada ("/catalog/pic/1") devuelve la matriz de bytes esperada para un archivo en una ubicación conocida. Lo hace sin configurar un servidor web real y de ese modo evita gran parte de la fragilidad que supone el uso de un servidor web real para realizar pruebas (por ejemplo, problemas con la configuración de firewall). Las pruebas funcionales que se ejecutan en TestServer normalmente son más lentas que las pruebas unitarias y de integración, pero son mucho más rápidas que las que se ejecutarían a través de la red a un servidor web de prueba.

>[!div class="step-by-step"]
[Anterior] (work-with-data-in-asp-net-core-apps.md) [Siguiente] (development-process-for-azure.md)
