# Documentación y Guías de Estilos en Java

## Manual Completo de Dominio: De Principiante a Experto

---

**Versión 2.0** | **13 Módulos + Anexos** | **Basado en documentación oficial Oracle & Google**

---

## Índice General

| Módulo | Tema | Nivel |
|--------|------|-------|
| 1 | Introducción y Fundamentos | Principiante |
| 2 | Javadoc Básico | Principiante |
| 3 | Estructura y Marcado | Intermedio |
| 4 | Etiquetas Avanzadas | Intermedio |
| 5 | Guías de Estilo Oficiales Oracle | Avanzado |
| 6 | Doclets y Extensiones | Avanzado |
| 7 | Documentación de Excepciones | Experto |
| 8 | Comentarios a Nivel de Paquete | Experto |
| 9 | Markdown en Java Moderno | Experto |
| 10 | Herramientas y Buenas Prácticas | Experto |
| 11 | Casos de Estudio Completos | Experto |
| 12 | Glosario y Referencias | Referencia |
| 13 | Guía de Estilo de Java de Google | Referencia Oficial |
| A | Anexo A: Plantillas | Complementario |
| B | Anexo B: Convertidor Formatos | Complementario |
| C | Anexo C: Configuración | Complementario |

---

# MÓDULO 1: Introducción y Fundamentos

## 1.1 ¿Qué es la Documentación en Java?

La documentación en Java no es simplemente un añadido opcional al código; es una **parte integral del proceso de desarrollo de software profesional**. En entornos empresariales y proyectos de código abierto, la documentación de calidad marca la diferencia entre un proyecto mantenible y uno que se vuelve inmanejable.

### Importancia Crítica de la Documentación

| Aspecto | Impacto | Prioridad |
|---------|---------|-----------|
| **Mantenimiento** | Reduce tiempo de comprensión del código | ⭐⭐⭐⭐⭐ |
| **Colaboración** | Facilita trabajo en equipo | ⭐⭐⭐⭐⭐ |
| **Onboarding** | Acelera integración de nuevos desarrolladores | ⭐⭐⭐⭐ |
| **Depuración** | Ayuda a entender lógica compleja | ⭐⭐⭐ |
| **APIs Públicas** | Esencial para reutilización | ⭐⭐⭐⭐⭐ |

> 📌 **Nota Profesional**: Según estudios de la industria, los desarrolladores dedican entre un 40% y 60% de su tiempo leyendo código en lugar de escribirlo.

## 1.2 Evolución de Javadoc

| Año | Versión Java | Característica Clave |
|-----|--------------|---------------------|
| 1995 | Java 1.0 | Javadoc básico |
| 2000 | Java 1.3 | Etiquetas estándar |
| 2004 | Java 5.0 | Anotaciones y generics |
| 2014 | Java 8 | Lambdas y streams |
| 2023 | Java 21 | Pattern matching |
| 2023 | Java 23 | Markdown support (JEP 467) |

## 1.3 Javadoc: El Estándar de Documentación

**Javadoc** es el generador oficial de documentación de API para Java. Fue creado por **Sun Microsystems** (adquirida por Oracle en 2010).

### Características Clave:

1. **Generación Automática**: Convierte comentarios especializados en documentación HTML
2. **Estándar de la Industria**: Utilizado por millones de desarrolladores
3. **Integración IDE**: Soportado por todos los entornos de desarrollo modernos
4. **Extensibilidad**: Personalizable mediante doclets y taglets

## 1.4 Ventajas sobre Documentación Manual

| Javadoc | Documentación Manual |
|---------|---------------------|
| ✅ Siempre sincronizada con el código | ❌ Puede quedar desactualizada |
| ✅ Formato estándar y consistente | ❌ Formatos variables |
| ✅ Búsqueda automática | ❌ Búsqueda manual |
| ✅ Integración con herramientas | ❌ Poca integración |

## 1.5 Requisitos Previos

### Nivel Básico:
- Sintaxis básica de Java
- Conceptos de clases y objetos
- Estructuras de control

### Nivel Intermedio:
- Herencia y polimorfismo
- Interfaces y clases abstractas
- Manejo de excepciones

### Nivel Avanzado:
- Genéricos
- Anotaciones
- Programación funcional

---

# MÓDULO 2: Javadoc Básico

## 2.1 Anatomía de un Comentario Javadoc

```java
/**
 * Este es un comentario Javadoc.
 * Note el doble asterisco al inicio.
 */

/*
 * Este es un comentario normal.
 * Solo tiene un asterisco.
 */
```

### Estructura Básica:

```java
/**
 * [Descripción principal]
 * [Descripción detallada opcional]
 *
 * @etiqueta valor
 * @etiqueta valor
 */
public class MiClase {
    // Código...
}
```

## 2.2 Ubicación de Comentarios Javadoc

Los comentarios Javadoc pueden colocarse antes de:

1. **Clases** ✅
2. **Interfaces** ✅
3. **Métodos** ✅
4. **Constructores** ✅
5. **Campos/Variables** ✅
6. **Paquetes** (en archivo package-info.java) ✅
7. **Enumeraciones** ✅

## 2.3 Ejemplo Completo

```java
/**
 * Representa una cuenta bancaria con operaciones básicas.
 * Esta clase proporciona funcionalidad para gestionar
 * depósitos, retiros y consultas de saldo.
 *
 * @author Juan Pérez
 * @version 1.0
 * @since 2024
 */
public class CuentaBancaria {

    /**
     * Saldo actual de la cuenta.
     */
    private double saldo;

    /**
     * Número único de identificación de la cuenta.
     */
    private String numeroCuenta;

    /**
     * Constructor que inicializa una nueva cuenta bancaria.
     *
     * @param numeroCuenta El número único de la cuenta
     * @param saldoInicial El saldo inicial de la cuenta
     */
    public CuentaBancaria(String numeroCuenta, double saldoInicial) {
        this.numeroCuenta = numeroCuenta;
        this.saldo = saldoInicial;
    }

    /**
     * Deposita una cantidad en la cuenta.
     *
     * @param cantidad La cantidad a depositar
     * @throws IllegalArgumentException Si la cantidad es negativa
     */
    public void depositar(double cantidad) {
        if (cantidad < 0) {
            throw new IllegalArgumentException(
                "La cantidad no puede ser negativa");
        }
        saldo += cantidad;
    }
}
```

## 2.4 Generación de Documentación HTML

### Comando Básico:

```bash
javadoc -d docs/ MiClase.java
```

### Opciones Importantes:

```bash
# Generar documentación con paquetes específicos
javadoc -d docs/ -sourcepath src/ com.miempresa.paquete1

# Incluir miembros privados
javadoc -private -d docs/ MiClase.java

# Configurar encoding para acentos
javadoc -encoding UTF-8 -charset UTF-8 -d docs/ MiClase.java
```

## 2.5 Estructura de Salida HTML

1. **Página principal**: Índice de todos los paquetes
2. **Resumen de paquetes**: Clases e interfaces por paquete
3. **Páginas de clases**: Detalle de cada clase
4. **Árbol de herencia**: Jerarquía de clases
5. **Índice alfabético**: Todas las clases y métodos

---

# MÓDULO 3: Estructura y Marcado

## 3.1 Marcado HTML en Javadoc

| Etiqueta | Propósito | Ejemplo |
|----------|-----------|---------|
| `<p>` | Párrafo | Dividir texto en párrafos |
| `<b>` | Negrita | **Texto importante** |
| `<i>` | Cursiva | *Énfasis* |
| `<code>` | Código | `nombreMetodo()` |
| `<pre>` | Texto preformateado | Bloques de código |
| `<ul>`, `<li>` | Listas | • Elemento 1 |

## 3.2 Ejemplo con Marcado HTML

```java
/**
 * Calcula el <b>promedio</b> de una lista de números.
 * <p>
 * Este método <i>ignora</i> los valores nulos en el cálculo.
 * <p>
 * Ejemplo de uso:
 * <pre>{@code
 * List<Integer> numeros = Arrays.asList(1, 2, 3, null, 5);
 * double promedio = calcularPromedio(numeros);
 * }</pre>
 *
 * <ul>
 *   <li>Maneja listas vacías devolviendo 0</li>
 *   <li>Ignora valores nulos</li>
 * </ul>
 *
 * @param numeros Lista de números a promediar
 * @return El promedio de los números no nulos
 */
public double calcularPromedio(List<Integer> numeros) {
    return 0.0;
}
```

## 3.3 Reglas de Formato

### Primera Frase (Resumen)

La primera frase es crucial porque:
- **Se extrae automáticamente** para las tablas de resumen
- **Debe ser concisa pero completa**
- **Termina en el primer punto** seguido de espacio

```java
/**
 * Devuelve el elemento mayor de la lista. Esta primera frase
 * aparece en el resumen. El resto aparece en la página detallada.
 */
public int obtenerMaximo(List<Integer> lista) {
    return 0;
}
```

### Casos Especiales:

```java
// ❌ Incorrecto:
/**
 * Simula la computadora MIX del Prof. Knuth.
 */

// ✅ Correcto:
/**
 * Simula la computadora&nbsp;MIX del&nbsp;Prof.&nbsp;Knuth.
 */
```

## 3.4 Convenciones de Estilo

### Uso de Tercera Persona:

```java
// ✅ Preferido (tercera persona declarativa):
/**
 * Obtiene la etiqueta del botón.
 */
public String getLabel() { return null; }

// ❌ Evitar (segunda persona imperativa):
/**
 * Obten la etiqueta del botón.
 */
```

### Frases Verbales:

```java
// ✅ Preferido:
/**
 * Calcula el interés compuesto.
 */
public double calcularInteres() { return 0.0; }

// ❌ Evitar:
/**
 * Este método calcula el interés compuesto.
 */
```

---

# MÓDULO 4: Etiquetas Avanzadas

## 4.1 Etiquetas de Bloque

### @param

```java
/**
 * @param nombre Nombre del usuario
 * @param edad La edad del usuario en años
 */
public void registrarUsuario(String nombre, int edad) { }
```

### @return

```java
/**
 * @return El número total de elementos
 * @return {@code true} si la operación fue exitosa
 */
public boolean agregar(Object elemento) { return true; }
```

### @throws

```java
/**
 * @throws IllegalArgumentException Si el argumento es nulo
 * @throws IOException Si ocurre un error de E/S
 */
public void procesarArchivo(String nombreArchivo) throws IOException { }
```

## 4.2 Etiquetas de Metadatos

### @author

```java
/**
 * @author Juan Pérez
 * @author María García
 */
public class MiClase { }
```

### @version

```java
/**
 * @version 1.2
 */
public class MiClase { }
```

### @since

```java
/**
 * @since 1.0
 */
public class NuevaFuncionalidad { }
```

### @deprecated

```java
/**
 * @deprecated A partir de 2.0, reemplazado por {@link #nuevoMetodo()}
 */
@Deprecated
public void metodoAntiguo() { }
```

## 4.3 Etiquetas en Línea

### {@link}

```java
/**
 * Consulta {@link java.util.ArrayList} para más información.
 * Ver también {@link #metodoRelacionado()}.
 */
public class Documentacion { }
```

### {@code}

```java
/**
 * El valor {@code null} indica ausencia de valor.
 * Usa {@code iterator()} para recorrer la colección.
 */
public class Constantes { }
```

### {@value}

```java
public class Configuracion {
    /**
     * Valor por defecto: {@value}
     */
    public static final int TIMEOUT = 30;
}
```

### {@inheritDoc}

```java
public interface Animal {
    /**
     * Hace que el animal emita su sonido.
     */
    void hacerSonido();
}

public class Perro implements Animal {
    /**
     * {@inheritDoc}
     * Los perros ladran: "Guau guau".
     */
    @Override
    public void hacerSonido() {
        System.out.println("Guau guau");
    }
}
```

## 4.4 Tabla Completa de Etiquetas

| Etiqueta | Tipo | Se aplica a | Descripción | Desde |
|----------|------|-------------|-------------|-------|
| `@author` | Bloque | Clase, Interfaz | Identifica al autor | 1.0 |
| `{@docRoot}` | Línea | Todas | Ruta relativa al directorio raíz | 1.3 |
| `@version` | Bloque | Clase, Interfaz | Información de versión | 1.0 |
| `@since` | Bloque | Todas | Versión desde la que existe | 1.1 |
| `@see` | Bloque | Todas | Enlaces a otros elementos | 1.0 |
| `@param` | Bloque | Método | Descripción de parámetro | 1.0 |
| `@return` | Bloque | Método | Descripción del valor devuelto | 1.0 |
| `@throws` | Bloque | Método | Excepciones lanzadas | 1.2 |
| `@deprecated` | Bloque | Todas | Marca como obsoleto | 1.0 |
| `{@inheritDoc}` | Línea | Método | Hereda documentación | 1.4 |
| `{@link}` | Línea | Todas | Enlace a símbolo | 1.2 |
| `{@linkplain}` | Línea | Todas | Enlace en texto normal | 1.4 |
| `{@value}` | Línea | Campo estático | Valor de campo estático | 1.4 |
| `{@code}` | Línea | Todas | Texto en fuente código | 1.5 |
| `{@literal}` | Línea | Todas | Texto literal | 1.5 |
| `@serial` | Bloque | Campo | Campo serializable | 1.2 |

---

# MÓDULO 5: Guías de Estilo Oficiales Oracle

## 5.1 Principios de Oracle

Oracle mantiene convenciones específicas que priorizan:

1. **Especificaciones de API** sobre guías de programación
2. **Condiciones de contorno** y casos extremos
3. **Independencia de implementación**

## 5.2 Diferencia entre Especificación y Guía

| Aspecto | Especificación de API | Guía de Programación |
|---------|----------------------|---------------------|
| **Propósito** | Contrato formal | Ayuda al desarrollador |
| **Contenido** | Afirmaciones verificables | Ejemplos y descripciones |
| **Audiencia** | Implementadores y testers | Desarrolladores finales |
| **Ejemplos** | No incluidos | Incluidos abundantemente |

## 5.3 Documentación de Condiciones de Contorno

```java
/**
 * Obtiene un elemento de la lista por índice.
 * <p>
 * <b>Comportamiento en casos extremos:</b>
 * <ul>
 *   <li><b>Índice 0:</b> Devuelve el primer elemento</li>
 *   <li><b>Índice negativo:</b> Lanza IndexOutOfBoundsException</li>
 *   <li><b>Índice >= tamaño:</b> Lanza IndexOutOfBoundsException</li>
 * </ul>
 *
 * @param indice Índice del elemento (0-based)
 * @return El elemento en la posición especificada
 * @throws IndexOutOfBoundsException Si el índice está fuera de rango
 */
public E get(int indice) { return null; }
```

## 5.4 Reutilización Automática de Comentarios

Javadoc hereda documentación en tres casos:

1. **Método sobrescribe** método de superclase
2. **Método de interfaz** sobrescribe método de superinterfaz
3. **Método de clase** implementa método de interfaz

## 5.5 Convenciones de Orden de Etiquetas

1. `@param` (en orden de declaración)
2. `@return`
3. `@throws` (alfabéticamente)
4. `@see`
5. `@since`
6. `@deprecated`

---

# MÓDULO 6: Doclets y Extensiones

## 6.1 ¿Qué es un Doclet?

Un **Doclet** es un programa Java que personaliza la salida de Javadoc.

### Usos:
- Generar PDF, LaTeX, XML
- Realizar análisis estático
- Verificar conformidad de estilo
- Generar diagramas UML

## 6.2 Doclet Estándar

```bash
javadoc MiClase.java
```

## 6.3 Doclets Especializados

### MIF Doclet (PDF):

```bash
javadoc -doclet com.sun.tools.doclets.mif.MIFDoclet -d pdf-output/ MiClase.java
```

### DocCheck:

```bash
javadoc -doclet com.sun.tools.doclets.doccheck.DocCheck -d report/ MiClase.java
```

## 6.4 Crear Doclet Personalizado

```java
import com.sun.javadoc.*;

public class MiDoclet {
    public static boolean start(RootDoc root) {
        ClassDoc[] clases = root.classes();

        for (ClassDoc clase : clases) {
            System.out.println("Clase: " + clase.name());

            MethodDoc[] metodos = clase.methods();
            for (MethodDoc metodo : metodos) {
                System.out.println("  Método: " + metodo.name());
                System.out.println("  Comentario: " + metodo.commentText());
            }
        }

        return true;
    }
}
```

---

# MÓDULO 7: Documentación de Excepciones

## 7.1 Tipos de Excepciones

### Excepciones Verificadas:

```java
/**
 * @throws FileNotFoundException Si el archivo no existe
 * @throws IOException Si ocurre un error de lectura
 */
public String leerArchivo(String rutaArchivo) throws IOException { }
```

### Excepciones No Verificadas:

```java
/**
 * @throws ArithmeticException Si el divisor es cero
 */
public double dividir(double dividendo, double divisor) { return 0; }
```

## 7.2 Directrices para Documentar

| Tipo | ¿Documentar? | En @throws | En cláusula throws |
|------|--------------|------------|-------------------|
| Excepciones verificadas | ✅ Siempre | ✅ Siempre | ✅ Siempre |
| RuntimeException común | ✅ Si es esperada | ✅ Si | ❌ No |
| NullPointerException | ❌ Generalmente no | ⚠️ Opcional | ❌ No |
| Errors (JVM) | ❌ Nunca | ❌ No | ❌ No |

## 7.3 Ejemplo Completo

```java
/**
 * @param cuenta La cuenta origen (no puede ser null)
 * @param cantidad La cantidad a transferir
 * @return El identificador único de la transacción
 * @throws IllegalArgumentException Si cuenta es null
 * @throws IllegalStateException Si la cuenta está congelada
 */
public String procesarTransaccion(Account cuenta, double cantidad) { }
```

---

# MÓDULO 8: Comentarios a Nivel de Paquete

## 8.1 package-info.java

```java
/**
 * Proporciona las clases fundamentales para el diseño
 * de interfaces gráficas de usuario (GUI) en Java.
 *
 * @author Equipo de Desarrollo UI
 * @version 2.0
 * @since 1.0
 */
package com.empresa.ui;
```

## 8.2 Estructura de Contenido

```java
/**
 * [Primera frase: Resumen conciso]
 * <p>
 * [Descripción detallada]
 * </p>
 * <p>
 * <b>Especificación del Paquete</b>
 * [Detalles técnicos]
 * </p>
 *
 * @since [versión]
 */
package com.empresa.paquete;
```

## 8.3 package.html vs package-info.java

| Aspecto | package.html | package-info.java |
|---------|-------------|-------------------|
| **Introducido en** | Java 1.2 | Java 5 |
| **Contenido** | Solo Javadoc | Javadoc + anotaciones |
| **Recomendado** | ❌ Obsoleto | ✅ Preferido |

---

# MÓDULO 9: Markdown en Java Moderno

## 9.1 Introducción

A partir de **Java 23 (JEP 467)**, Javadoc soporta Markdown.

## 9.2 Sintaxis Básica

```java
/// Calcula el promedio de una lista de números.
///
/// Este método **ignora** los valores nulos.
///
/// ### Ejemplo de uso:
/// ```
/// List<Integer> numeros = Arrays.asList(1, 2, 3, null, 5);
/// double promedio = calcularPromedio(numeros);
/// ```
///
/// - Maneja listas vacías devolviendo 0
/// - Ignora valores nulos
///
/// @param numeros Lista de números a promediar
/// @return El promedio de los números no nulos
public double calcularPromedio(List<Integer> numeros) { return 0; }
```

## 9.3 Elementos Soportados

```java
/// # Encabezado 1
/// ## Encabezado 2
///
/// **Texto en negrita**
/// *Texto en cursiva*
/// `código en línea`
///
/// - Elemento de lista
///
/// ```java
/// // Bloque de código
/// ```
```

## 9.4 Ventajas

| Aspecto | HTML Tradicional | Markdown |
|---------|-----------------|----------|
| **Legibilidad** | ⭐⭐ | ⭐⭐⭐⭐⭐ |
| **Curva de aprendizaje** | Difícil | Fácil |
| **Sintaxis** | Verbosa | Concisa |
| **Compatibilidad** | Total | Java 23+ |

---

# MÓDULO 10: Herramientas y Buenas Prácticas

## 10.1 Verificación

```bash
javadoc -doclet com.sun.tools.doclets.doccheck.DocCheck -d report/ src/*.java
```

## 10.2 Maven

```xml
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-javadoc-plugin</artifactId>
    <version>3.6.0</version>
    <configuration>
        <encoding>UTF-8</encoding>
        <charset>UTF-8</charset>
    </configuration>
</plugin>
```

## 10.3 Gradle

```groovy
javadoc {
    options {
        encoding = 'UTF-8'
        windowTitle = 'Proyecto API'
    }
}
```

## 10.4 Checklist de Calidad

### ✅ Estructura
- [ ] Comienza con `/**` y termina con `*/`
- [ ] Primera frase es concisa y descriptiva
- [ ] Descripción en tercera persona

### ✅ Contenido
- [ ] @param para cada parámetro
- [ ] @return para métodos que devuelven valor
- [ ] @throws para todas las excepciones

### ✅ Formato
- [ ] HTML válido si se usa
- [ ] Enlaces con {@link}
- [ ] Longitud de línea <= 80 caracteres

## 10.5 Errores Comunes

```java
// ❌ Comentario vacío
/**
 * Método.
 */
public void metodo() { }

// ✅ Correcto
/**
 * Devuelve el valor numérico de esta instancia.
 *
 * @return El valor numérico (nunca negativo)
 */
public int getValor() { return 0; }
```

---

# MÓDULO 11: Casos de Estudio

## 11.1 API de Gestión de Biblioteca

```java
/**
 * Servicio principal para la gestión de préstamos.
 * <p>
 * <b>Reglas de negocio:</b>
 * <ul>
 *   <li>Máximo 5 préstamos activos</li>
 *   <li>Período de préstamo: 14 días</li>
 * </ul>
 * </p>
 *
 * @author María García
 * @version 3.1
 */
public class PrestamoService {

    /**
     * Realiza un préstamo de libro para un usuario.
     *
     * @param usuarioId El identificador único del usuario
     * @param libroISBN El ISBN del libro
     * @return Optional conteniendo el préstamo creado
     * @throws UsuarioNoEncontradoException Si el usuario no existe
     */
    public Optional<Prestamo> realizarPrestamo(
        Long usuarioId, String libroISBN) { return Optional.empty(); }
}
```

## 11.2 API de Pagos

```java
/**
 * Define el contrato para procesadores de pagos.
 *
 * @author Arquitectura de Pagos
 * @version 2.0
 */
public interface ProcesadorPago {

    /**
     * Procesa un pago de forma síncrona.
     *
     * @param idTransaccion Identificador único
     * @param monto El monto a cobrar
     * @return El resultado del procesamiento
     * @throws PagoRechazadoException Si el emisor rechaza
     */
    ResultadoPago procesarPago(
        Long idTransaccion, BigDecimal monto) { }
}
```

---

# MÓDULO 12: Glosario y Referencias

## 12.1 Glosario

| Término | Definición |
|---------|------------|
| **API** | Application Programming Interface (Interfaz de Programación de Aplicaciones) |
| **Doclet** | Document Let (Programa que procesa Javadoc) |
| **Javadoc** | Java Documentation (Herramienta de documentación) |
| **HTML** | HyperText Markup Language (Lenguaje de Marcado de Hipertexto) |
| **JDK** | Java Development Kit (Kit de Desarrollo Java) |
| **SDK** | Software Development Kit (Kit de Desarrollo de Software) |
| **IDE** | Integrated Development Environment (Entorno de Desarrollo Integrado) |
| **JCK** | Java Compatibility Kit (Kit de Compatibilidad Java) |
| **JSR** | Java Specification Request (Solicitud de Especificación Java) |
| **UML** | Unified Modeling Language (Lenguaje de Modelado Unificado) |
| **XML** | eXtensible Markup Language (Lenguaje de Marcado Extensible) |
| **JEP** | JDK Enhancement Proposal (Propuesta de Mejora del JDK) |
| **UTF-8** | Unicode Transformation Format 8-bit (Formato de Transformación Unicode de 8 bits) |
| **ASCII** | American Standard Code for Information Interchange |
| **K & R** | Kernighan and Ritchie (Estilo de formato de código) |

## 12.2 Referencias Oficiales

1. **Oracle Javadoc Tool**: https://www.oracle.com/java/technologies/javase/javadoc.html
2. **How to Write Doc Comments**: https://www.oracle.com/ca-en/technical-resources/articles/java/javadoc-tool.html
3. **Google Java Style Guide**: https://google.github.io/styleguide/javaguide.html
4. **JEP 467**: https://openjdk.org/jeps/467

---

# MÓDULO 13: Guía de Estilo de Java de Google

## 1. Introducción

Este documento sirve como la definición **completa** de los estándares de codificación de Google para el código fuente en el Lenguaje de Programación Java™. Un archivo fuente Java se describe como que está *en Estilo Google* si y solo si cumple con las reglas aquí establecidas.

### 1.1 Notas de terminología

1. El término *clase* incluye: clase normal, clase registro, clase enumeración, interfaz o tipo anotación (`@interface`).
2. El término *miembro* incluye: clase anidada, campo, método o constructor.
3. El término *comentario* siempre se refiere a comentarios de *implementación*. Usamos "Javadoc" para comentarios de documentación.

### 1.2 Notas sobre la guía

El código de ejemplo es **no normativo**. Las opciones de formato opcionales no deben aplicarse como reglas.

## 2. Aspectos básicos del archivo fuente

### 2.1 Nombre del archivo

El nombre del archivo consiste en el nombre de la clase de nivel superior, más la extensión `.java`.

### 2.2 Codificación de archivos: UTF-8 (Unicode Transformation Format, Formato de Transformación Unicode)

Los archivos fuente están codificados en **UTF-8**.

### 2.3 Caracteres especiales

#### 2.3.1 Caracteres de espacio en blanco

El **carácter de espacio horizontal ASCII** (**0x20**) es el único espacio en blanco permitido. Los tabuladores **no** se utilizan para sangría.

#### 2.3.2 Secuencias de escape especiales

Para caracteres con secuencia de escape (`\b`, `\t`, `\n`, `\f`, `\r`, `\"`, `\'`, `\\`), se usa esa secuencia.

#### 2.3.3 Caracteres no ASCII

| Ejemplo | Discusión |
|---------|-----------|
| `String unitAbbrev = "μs";` | Mejor: perfectamente claro |
| `String unitAbbrev = "\u03bcs"; // "μs"` | Permitido, pero innecesario |
| `String unitAbbrev = "\u03bcs";` | Deficiente: poco claro |

## 3. Estructura del archivo fuente

Un archivo fuente consta de estas secciones **en orden**:

1. Información de licencia o derechos de autor
2. Declaración de paquete
3. Importaciones
4. Exactamente una clase de nivel superior

### 3.1 Declaración de paquete

La declaración de paquete **no se ajusta a la línea**.

### 3.2 Importaciones

#### No se permiten importaciones comodín

```java
// ❌ Incorrecto
import java.util.*;

// ✅ Correcto
import java.util.List;
import java.util.ArrayList;
```

#### Ordenación

1. Todas las importaciones estáticas en un solo grupo
2. Todas las importaciones no estáticas en un solo grupo

### 3.3 Declaración de clase

Cada clase de nivel superior reside en un archivo propio.

#### Sobrecargas: nunca dividir

Los métodos con el mismo nombre aparecen en un grupo contiguo.

## 4. Formato

### 4.1 Llaves

#### Uso de llaves

Las llaves se usan con `if`, `else`, `for`, `do` y `while`, incluso cuando el cuerpo está vacío.

#### Estilo K & R (Kernighan and Ritchie, Kernighan y Ritchie)

```java
return new MyClass() {
    @Override public void method() {
        if (condition()) {
            try {
                something();
            } catch (ProblemException e) {
                recover();
            }
        } else if (otherCondition()) {
            somethingElse();
        } else {
            lastThing();
        }
    }
};
```

#### Bloques vacíos

```java
// Esto es aceptable
void doNothing() {}

// Esto no es aceptable en multi-bloque
try {
    doSomething();
} catch (Exception e) {}
```

### 4.2 Sangría: +2 espacios

Cada vez que se abre un bloque, la sangría aumenta en 2 espacios.

### 4.3 Una declaración por línea

Cada declaración es seguida por un salto de línea.

### 4.4 Límite de columna: 100

**Excepciones:**
1. URLs largas en Javadoc
2. Declaraciones `package` e importaciones
3. Contenido de bloques de texto
4. Líneas de comando copiables

### 4.5 Ajuste de línea

#### Dónde romper

1. En operador de *no asignación*: el corte viene *antes* del símbolo
2. En operador de *asignación*: el corte viene *después* del símbolo
3. Nombre de método permanece unido al paréntesis de apertura

```java
MyLambda<String, Long, Object> lambda =
    (String label, Long value, Object obj) -> {
    ...
};
```

#### Líneas de continuación: +4 espacios

Cada línea de continuación se sangra al menos +4 desde la línea original.

### 4.6 Espacios en blanco

#### Espacios en blanco verticales

Una línea en blanco entre miembros consecutivos de una clase.

#### Espacio en blanco horizontal

```java
if (condition) {  // espacio después de keyword
    method();      // sangría de 4 espacios
}
```

#### Alineación horizontal: nunca requerida

```java
// Esto está bien
private int x;
private Color color;

// Esto también, pero no necesario
private int   x;
private Color color;
```

### 4.7 Paréntesis de agrupación: recomendados

### 4.8 Construcciones específicas

#### Enumeraciones

```java
private enum Answer {
    YES {
        @Override public String toString() {
            return "yes";
        }
    },
    NO,
    MAYBE
}
```

#### Variables

Cada declaración declara solo una variable: `int a, b;` no se utiliza.

#### Matrices

`String[] args`, no `String args[]`.

#### Switch

```java
switch (number) {
    case 0, 1 -> handleZeroOrOne();
    case 2 ->
        handleTwoWithAnExtremelyLongMethodCall();
    default -> {
        logger.atInfo().log("Number %s", number);
        handleSurprisingNumber(number);
    }
}
```

#### Anotaciones

```java
// Clase
@Deprecated
@CheckReturnValue
public final class Frozzler { ... }

// Método
@Override public int hashCode() { ... }

// Campo
@Partial @Mock DataLoader loader;
```

#### Comentarios

```java
/*
 * Esto está
 * bien.
 */
```

#### Modificadores

```java
public protected private abstract default
static final sealed non-sealed
transient volatile synchronized native strictfp
```

#### Literales numéricos

`3000000000L`, no `3000000000l`.

## 5. Nomenclatura

### 5.1 Reglas comunes

Los identificadores usan solo letras y dígitos ASCII. No se utilizan prefijos como `name_`, `mName`, `s_name`.

### 5.2 Reglas por tipo

| Tipo | Estilo | Ejemplo |
|------|--------|---------|
| Paquete | Minúsculas | `com.example.deepspace` |
| Clase | UpperCamelCase | `ImmutableList` |
| Método | lowerCamelCase | `sendMessage` |
| Constante | UPPER_SNAKE_CASE | `NUMBER` |
| Campo no constante | lowerCamelCase | `computedValues` |
| Parámetro | lowerCamelCase | `nombreParametro` |
| Variable local | lowerCamelCase | `indiceActual` |
| Variable de tipo | Letra mayúscula o UpperCamelCase + T | `E`, `RequestT` |

### 5.3 Notación camello: definida

Para convertir una frase a notación camello:

1. Convierte a ASCII y elimina apóstrofes
2. Divide en palabras
3. Convierte todo a minúsculas
4. Mayúscula primera letra de cada palabra

| Forma en prosa | Correcto | Incorrecto |
|----------------|----------|------------|
| "solicitud HTTP XML" | `XmlHttpRequest` | `XMLHTTPRequest` |
| "nuevo ID de cliente" | `newCustomerId` | `newCustomerID` |
| "soporta IPv6 en iOS" | `supportsIpv6OnIos` | `supportsIPv6OnIOS` |
| "importador de YouTube" | `YouTubeImporter` | `YoutubeImporter`* |

## 6. Prácticas de programación

### 6.1 @Override: siempre utilizado

```java
@Override
public String getNameIfPresent() { ... }
```

**Excepción:** @Override puede omitirse cuando el método padre está @Deprecated.

### 6.2 Excepciones capturadas: no ignoradas

```java
try {
    int i = Integer.parseInt(response);
    return handleNumericResponse(i);
} catch (NumberFormatException _) {
    // no es numérico; está bien
}
return handleTextResponse(response);
```

### 6.3 Miembros estáticos: calificados mediante clase

```java
Foo.aStaticMethod(); // bueno
aFoo.aStaticMethod(); // malo
```

### 6.4 Finalizadores: no utilizados

No sobrescribas `Object.finalize`.

## 7. Javadoc

### 7.1 Formato

#### Markdown Javadoc

```java
/// El texto de Javadoc se escribe aquí,
/// ajustado normalmente...
public int method(String p1) { ... }
```

#### Javadoc Tradicional

```java
/**
 * Múltiples líneas de texto Javadoc
 * se escriben aquí.
 */
public int method(String p1) { ... }
```

### 7.2 El fragmento de resumen

Cada bloque Javadoc comienza con un **fragmento de resumen**. Es una frase sustantiva o verbal, no una oración completa.

```java
/// Devuelve el ID del cliente.
```

### 7.3 Dónde se utiliza

Como **mínimo**, Javadoc está presente para cada clase, miembro o componente de registro visible.

**Excepciones:**
- Miembros autoexplicativos (getFoo())
- Sobrescrituras
- Javadoc no requerido

---

# ANEXO A: Plantillas de Documentación

## Plantilla de Clase

```java
/**
 * [Breve descripción de la clase].
 * <p>
 * [Descripción detallada del propósito].
 * </p>
 *
 * @author [Nombre del autor]
 * @version [Versión]
 * @since [Versión desde la que existe]
 */
public class NombreClase {
    // ...
}
```

## Plantilla de Método

```java
/**
 * [Breve descripción del método].
 * <p>
 * [Descripción detallada del comportamiento].
 * </p>
 *
 * @param nombreParametro [Descripción]
 * @return [Descripción del valor devuelto]
 * @throws TipoExcepcion [Cuándo se lanza]
 */
public TipoRetorno nombreMetodo(TipoParametro nombreParametro) {
    // ...
}
```

---

# ANEXO B: Convertidor HTML a Markdown

| HTML | Markdown | Uso |
|------|----------|-----|
| `<b>texto</b>` | `**texto**` | Negrita |
| `<i>texto</i>` | `*texto*` | Cursiva |
| `<code>texto</code>` | `` `texto` `` | Código |
| `<pre>bloque</pre>` | ```bloque``` | Bloque código |
| `<ul><li>item</li></ul>` | `- item` | Lista |
| `<a href="url">texto</a>` | `[texto](url)` | Enlace |

---

# ANEXO C: Configuración Rápida

## Maven Minimalista

```xml
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-javadoc-plugin</artifactId>
    <version>3.6.0</version>
    <configuration>
        <encoding>UTF-8</encoding>
    </configuration>
</plugin>
```

## Script de Verificación

```bash
#!/bin/bash
echo "=== Verificación de Javadoc ==="
javadoc -Xdoclint:syntax src/*.java
echo "=== Verificación completada ==="
```

---

# GLOSARIO COMPLETO

| Término | Definición |
|---------|------------|
| **API** | Application Programming Interface (Interfaz de Programación de Aplicaciones) |
| **ASCII** | American Standard Code for Information Interchange (Código Estadounidense Estándar para el Intercambio de Información) |
| **Doclet** | Document Let (Programa que procesa Javadoc) |
| **HTML** | HyperText Markup Language (Lenguaje de Marcado de Hipertexto) |
| **IDE** | Integrated Development Environment (Entorno de Desarrollo Integrado) |
| **JCK** | Java Compatibility Kit (Kit de Compatibilidad Java) |
| **JDK** | Java Development Kit (Kit de Desarrollo Java) |
| **JEP** | JDK Enhancement Proposal (Propuesta de Mejora del JDK) |
| **JSR** | Java Specification Request (Solicitud de Especificación Java) |
| **JUnit** | Java Unit Testing Framework (Marco de Pruebas Unitarias de Java) |
| **K & R** | Kernighan and Ritchie (Estilo de formato) |
| **LowerCamelCase** | Notación camello inferior (ej. nombreDeMetodo) |
| **SDK** | Software Development Kit (Kit de Desarrollo de Software) |
| **UML** | Unified Modeling Language (Lenguaje de Modelado Unificado) |
| **UpperCamelCase** | Notación camello superior (ej. NombreDeClase) |
| **UTF-8** | Unicode Transformation Format 8-bit (Formato de Transformación Unicode de 8 bits) |
| **XML** | eXtensible Markup Language (Lenguaje de Marcado Extensible) |
| **CRV** | CheckReturnValue (Verificar Valor de Retorno) |
| **IPv6** | Internet Protocol version 6 (Protocolo de Internet versión 6) |
| **iOS** | iPhone Operating System (Sistema Operativo de iPhone) |
| **2SV** | Two-Step Verification (Verificación en Dos Pasos) |
| **HTTP** | HyperText Transfer Protocol (Protocolo de Transferencia de Hipertexto) |
| **URL** | Uniform Resource Locator (Localizador de Recursos Uniforme) |
| **JSNI** | JavaScript Native Interface (Interfaz Nativa de JavaScript) |
| **TODO** | "To Do" (Por hacer) |
| **UPPER_SNAKE_CASE** | Notación serpiente superior (ej. NOMBRE_CONSTANTE) |

---

**Fin del Manual**

---

*Guías de Estilos en Java - Versión 2.0*
*Incluye: Documentación oficial Oracle + Guía de Estilo Google*
*13 Módulos + 3 Anexos + Glosario Completo*
```

---
