# Actividad-de-evidencia-1_U2-Abstract-Factory
codigo 
https://drive.google.com/drive/folders/11dy_SLVFYWEIuQy5L4DDdgxzuEVXKYR9?usp=drive_link
2. Introducción al tema: Abstract Factory
El patrón de diseño Abstract Factory pertenece a los patrones creacionales y su principal objetivo es facilitar la creación de familias de objetos relacionados sin necesidad de especificar sus clases concretas directamente en el código principal. En lugar de instanciar objetos usando la palabra new en todas partes, se utiliza una fábrica que se encarga de crear los objetos adecuados dependiendo del tipo de configuración que se necesite.
Este patrón es útil cuando un sistema puede trabajar con diferentes tipos de productos que pertenecen a una misma familia, pero que cambian según el contexto. Por ejemplo, en el caso de esta práctica, se manejan distintas modalidades educativas: presencial, virtual e híbrida. Cada modalidad tiene su propia guía y su propio examen, pero todos siguen una misma estructura general.
La ventaja principal de Abstract Factory es que permite que el código sea más organizado y flexible. Si en el futuro se necesita agregar una nueva modalidad, solo se crea una nueva fábrica con sus respectivas clases, sin modificar el funcionamiento general del programa. Esto ayuda a mantener el principio de bajo acoplamiento y facilita el mantenimiento del sistema.


3. código implementado
using System;

namespace Abstract_Factory
{
    class Program
    {
        static void Main(string[] args)
        {
            MaterialFactory fabrica;

            // Modalidad presencial
            fabrica = new MaterialPresencialFactory();

            Guia guia = fabrica.CrearGuia();
            Examen examen = fabrica.CrearExamen();

            guia.Mostrar();
            examen.Aplicar();

            Console.WriteLine();

            // Modalidad virtual
            fabrica = new MaterialVirtualFactory();

            guia = fabrica.CrearGuia();
            examen = fabrica.CrearExamen();

            guia.Mostrar();
            examen.Aplicar();

            Console.WriteLine();

            // Modalidad hibrida
            fabrica = new MaterialHibridoFactory();

            guia = fabrica.CrearGuia();
            examen = fabrica.CrearExamen();

            guia.Mostrar();
            examen.Aplicar();

            Console.ReadKey();
        }
    }
}

namespace Abstract_Factory
{
    public class MaterialPresencialFactory : MaterialFactory
    {
        public override Guia CrearGuia()
        {
            return new GuiaImpresa();
        }

        public override Examen CrearExamen()
        {
            return new ExamenEnPapel();
        }
    }

    public class MaterialVirtualFactory : MaterialFactory
    {
        public override Guia CrearGuia()
        {
            return new GuiaPDF();
        }

        public override Examen CrearExamen()
        {
            return new ExamenOnline();
        }
    }

    public class MaterialHibridoFactory : MaterialFactory
    {
        public override Guia CrearGuia()
        {
            return new GuiaHibrida();
        }

        public override Examen CrearExamen()
        {
            return new ExamenMixto();
        }
    }
}
using System;

namespace Abstract_Factory
{
    public class GuiaHibrida : Guia
    {
        public override void Mostrar()
        {
            Console.WriteLine("Mostrando la guia en modalidad hibrida (semipresencial)");
        }
    }

    public class ExamenMixto : Examen
    {
        public override void Aplicar()
        {
            Console.WriteLine("Se aplica examen mixto");
        }
    }
}
using System;

namespace Abstract_Factory
{
    public class GuiaPDF : Guia
    {
        public override void Mostrar()
        {
            Console.WriteLine("Mostrando la guia PDF");
        }
    }

    public class ExamenOnline : Examen
    {
        public override void Aplicar()
        {
            Console.WriteLine("Se aplica examen en linea");
        }
    }
}
using System;

namespace Abstract_Factory
{
    public class GuiaImpresa : Guia
    {
        public override void Mostrar()
        {
            Console.WriteLine("Mostrando la guia impresa");
        }
    }

    public class ExamenEnPapel : Examen
    {
        public override void Aplicar()
        {
            Console.WriteLine("Se aplica examen en papel");
        }
    }
}
namespace Abstract_Factory
{
    public abstract class MaterialFactory
    {
        public abstract Guia CrearGuia();
        public abstract Examen CrearExamen();
    }

    public abstract class Guia
    {
        public abstract void Mostrar();
    }

    public abstract class Examen
    {
        public abstract void Aplicar();
    }
}


4. Conclusión del patrón y de la implementación realizada
En conclusión, el patrón Abstract Factory es una herramienta muy útil cuando se necesita trabajar con diferentes grupos de objetos que comparten una misma estructura pero tienen implementaciones distintas. Permite separar la lógica de creación de objetos del resto del programa, haciendo que el código sea más limpio y más fácil de ampliar.
En la implementación realizada, se aplicó este patrón para manejar tres modalidades: presencial, virtual e híbrida. Cada una cuenta con su propia guía y su propio examen, pero todas siguen la misma estructura base definida por las clases abstractas. Gracias a esto, el programa puede cambiar de modalidad simplemente cambiando la fábrica que se instancia, sin afectar el resto del código.
Además, al agregar la modalidad híbrida se comprobó que el patrón facilita la extensión del sistema, ya que solo fue necesario crear nuevas clases y una nueva fábrica, sin modificar las clases existentes. Esto demuestra que el patrón cumple con su propósito de hacer el sistema más escalable y organizado.
En general, esta práctica permitió entender mejor cómo funcionan los patrones creacionales y cómo pueden aplicarse en situaciones reales para mejorar la estructura del código.

[Actividad de evidencia 1_U2 Abstract Factory.zip](https://github.com/user-attachments/files/25873529/Actividad.de.evidencia.1_U2.Abstract.Factory.zip)
