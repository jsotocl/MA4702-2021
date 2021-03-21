# Página complementaria curso MA4702. 
# Versión 2021.

Esta página se actualizará con la información necesaria para los laboratorios del curso.

## Instalación de software

# 1. Instalar Julia

En este curso usaremos el lenguaje de programación [Julia](https://julialang.org/).

En este curso recomendamos usar Julia 1.5.4 o superior. Puede descargar Julia en <https://julialang.org/downloads/>. En la misma página están las instrucciones para añadir Julia a la variable de entorno PATH para así poder llamar julia mediante la terminal a través del comando `julia`.

Puede trabajar directamente en la linea de comandos o a través de un ambiente de desarrollo (IDE). Para trabajar de manera individual un buen IDE es [JUNO](https://junolab.org/), editor de código construido sobre ATOM. 

Sin embargo, para trabajar en los laboratorios y mostrar los resultados usaremos siempre el ambiente [Jupyter notebook](https://jupyter.org/) que se usa sobre un navegador (chrome, por ejemplo).

# 2. Instalar Jupyter Notebook

Julia cuenta con <a href=https://github.com/JuliaLang/IJulia.jl>IJulia</a>, un paquete que permite utilizar el entorno interactivo de <a href=https://jupyter.org/>Jupyter notebook</a>. 

Primero debe instalar el paqueta IJulia ejecutando los siguientes comandos (solo la primera vez que lo usa) 
Nota: Pkg es el gestor de paquetes de Julia, lo usaremos bastante para instalar nuevas funcionalidades.

```julia
julia>  import Pkg
julia>  Pkg.add("IJulia")
```

Cada vez que quiera abrir Jupyter notebook en el navegador, ejecute sobre la consola de Julia los siguientes comandos:

```julia
julia>  using IJulia
julia>  notebook()
```

# 3. Instalar Gurobi

[Gurobi](https://www.gurobi.com) es el solver de programación lineal mixta (y de programación convexa, no convexa, no lineal, etc.) que usaremos en este curso.
Si bien es un solver comercial, podemos acceder a él gracias a una licencia académica. Recomendamos usar Gurobi 9.1.1 o superior.

Descargue Gurobi en el link de abajo. Las instrucciones para instalarlo en su sistema operativo están en el mismo link en el archivo README.
Para facilitar los siguientes pasos, es conveniente que instale Gurobi en un directorio con nombre sencillo (directo en la raíz, gurobi911 por ejemplo).

https://www.gurobi.com/downloads/gurobi-software/

Solicite la licencia aquí (debe registrarse como estudiante de la Universidad)

https://www.gurobi.com/downloads/end-user-license-agreement-academic/

Para activar la licencia desde un computador con gurobi instalado debe ejecutar un comando (``grbgetkey numero-licencia``) desde la linea de comandos y  conectado a internet (no requiere VPN). Las instrucciones de activación están en esta url:

https://www.gurobi.com/downloads/free-academic-license/

# 4. Instalar API de Gurobi en Julia

Una vez que tenga Gurobi instalado en su sistema operativo, necesitamos que Julia se pueda comunicar con Gurobi. Para instalar la API de Gurobi de Julia debe fijar la variable de entorno ``ENV["GUROBI_HOME"]`` con el directorio en el que está instalado Gurobi y luego instalar los paquetes apropiados (para más detalles, puede ir a https://github.com/JuliaOpt/Gurobi.jl). Para esto en un terminal de Julia escriba (solo una vez).


```julia
# En Windows, puede ser...
ENV["GUROBI_HOME"] = "C:\\Program Files\\gurobi911\\win64"
# ... or tal vez ...
ENV["GUROBI_HOME"] = "C:\\gurobi911\\win64"
import Pkg
Pkg.add("Gurobi")
Pkg.build("Gurobi")

# En Mac, puede ser...
ENV["GUROBI_HOME"] = "/Library/gurobi910/mac64"
import Pkg
Pkg.add("Gurobi")
Pkg.build("Gurobi")

```

# 5. Instalar JuMP (en Julia)

[JuMP](https://jump.dev) es un lenguage de modelamiento que soporta Julia. Usar JuMP no solo facilita formular y resolver programas lineales (puros, enteros o mixtos) sino tambien permite modelar programación semidefinida positiva, programación no lineal y clases relacionadas. Recomendamos usar JuMP 0.21 o superior.

Instale la  última versión estable de JuMP escribiendo en julia:

```julia
Pkg.add("JuMP")
```

(en caso que no haya importado Pkg en esta sesión debe hacerlo antes de usar el comando anterior).

### Nota sobre instalación de paquetes en Julia.

Los paquetes se pueden instalar desde Jupyter o desde la terminal de Julia. Si la instalación falla en Jupyter se sugiere instalar desde la terminal de julia.

En vez de importar el gestor de paquetes Pkg, pueden usarlo directamente escribiendo `]` en el terminal, para salir del modo apretar `backspace`, por ejemplo:
```julia
#instalar
pkg> add GLPK #primera opción
pkg> build GLPK #segunda opción si no funciona el primero
#apretar backspace
julia> using GLPK #importar paquete
```

Alternativamente:
```julia
julia>  using Pkg
julia>  Pkg.add("GLPK")  #primera opción
julia>  Pkg.build("GLPK") #segunda opción si no funciona el primero
```

# 5. Documentación y guías

- [Introducción a Julia](https://juliaacademy.com/p/intro-to-julia)
- [Documentación de Julia](https://docs.julialang.org/)
- [Documentación de Gurobi](https://www.gurobi.com/documentation/)
- [Documentación de JuMP](https://docs.julialang.org/)
